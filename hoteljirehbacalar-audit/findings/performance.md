# Performance & Core Web Vitals — Hotel Jireh Bacalar
**Score: 45/100**

## Estimaciones (lab data — sin acceso a CrUX/campo real)

| Métrica | Estimación | Umbral Google |
|---------|-----------|---------------|
| LCP (Largest Contentful Paint) | ~2.5-4s* | Bueno: <2.5s |
| INP (Interaction to Next Paint) | ~50ms | Bueno: <200ms |
| CLS (Cumulative Layout Shift) | ~0.15-0.25* | Bueno: <0.1 |
| FID / TTI | Excelente (sin JS) | — |

*Estimaciones basadas en análisis estático. LCP y CLS se ven afectados por los problemas de imagen.

## Lo que funciona ✓
- **Cero JavaScript** — TTI inmediato, sin bloqueo de parser
- **CSS inline** — Elimina request adicional de stylesheet externo
- **HTML ligero** — 32KB total para el HTML
- **Sin frameworks** — Sin Vue/React/Angular overhead

## Hallazgos Críticos

### [Critical] 11/11 imágenes sin atributos `width` y `height`
- **Evidencia**: Todas las imágenes `<img>` carecen de `width` y `height` explícitos
- **Impacto CLS**: Sin dimensiones, el navegador no puede reservar espacio antes de cargar. Causa saltos de layout (CLS alto). Google penaliza CLS > 0.1 en Core Web Vitals.
- **Solución**: Agregar `width` y `height` a cada `<img>`. Ejemplo:
  ```html
  <img src="images/facade-day.jpg" width="800" height="1000" alt="...">
  ```

### [High] Imagen hero (LCP) sin preload
- **Evidencia**: `facade-day.jpg` (176KB) es la imagen más grande above the fold y candidata principal a LCP. No hay `<link rel="preload">`.
- **Impacto**: LCP se retrasa hasta que el browser parsea el HTML y descubre la imagen
- **Solución**:
  ```html
  <link rel="preload" href="images/facade-day.jpg" as="image" fetchpriority="high">
  ```

### [High] 9/11 imágenes sin `loading="lazy"`
- **Evidencia**: Solo la imagen hero debería cargar eager. Las 9 imágenes restantes (galería, habitaciones) no tienen `loading="lazy"`
- **Impacto**: El browser descarga todas las imágenes en el primer load, incrementando el peso total (~560KB en JPG)
- **Solución**: Agregar `loading="lazy"` a todas las imágenes below the fold

### [High] Imágenes solo en formato JPG — sin WebP/AVIF
- **Evidencia**:
  - facade-day.jpg → 176KB
  - facade-night.jpg → 140KB
  - room-simple.jpg → 116KB
  - Total: ~560KB en 7 imágenes
- **Impacto**: WebP reduce el tamaño 25-34% vs JPG; AVIF hasta 50%. En conexiones móviles lentas (común en Bacalar), esto marca la diferencia.
- **Solución**: Convertir a WebP y usar `<picture>` con fallback JPG:
  ```html
  <picture>
    <source srcset="images/facade-day.webp" type="image/webp">
    <img src="images/facade-day.jpg" alt="..." width="800" height="1000">
  </picture>
  ```

### [High] Fuentes personalizadas sin cargar (FOUT severo)
- **Evidencia**: CSS declara `'Inter Body'` y `'Fraunces Display'` pero no hay `@font-face` ni CDN de fuentes. El browser renderiza en Segoe UI/Georgia.
- **Impacto**: Layout Shift al cargar fuentes (CLS), experiencia visual incorrecta
- **Solución**: Agregar Google Fonts con `display=swap`:
  ```html
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Fraunces:ital,wght@0,600;1,600&family=Inter:wght@400;500;600&display=swap" rel="stylesheet">
  ```

### [Medium] Sin `srcset` para imágenes responsivas
- **Evidencia**: Ninguna imagen usa `srcset` o `sizes`
- **Impacto**: Un móvil con pantalla 390px descarga la misma imagen que un monitor 4K
- **Solución**: Generar versiones de 400w, 800w, 1200w y usar `srcset`

### [Low] HTML sin compresión declarada (servidor)
- **Evidencia**: Sin acceso al servidor, no podemos verificar gzip/brotli
- **Recomendación**: Asegurar que el hosting tenga compresión habilitada para HTML/CSS
