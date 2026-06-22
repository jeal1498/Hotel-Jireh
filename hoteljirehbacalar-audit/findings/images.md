# Images SEO — Hotel Jireh Bacalar
**Score: 40/100**

## Inventario de imágenes

| Archivo | Tamaño | Alt Text | Lazy | Width/Height | Formato |
|---------|--------|----------|------|--------------|---------|
| facade-day.jpg | 176KB | ✓ | ✗ | ✗ | JPG |
| facade-night.jpg | 140KB | ✓ | ✗ | ✗ | JPG |
| logo.jpg | 24KB | ✓ | eager | ✗ | JPG |
| palapa.jpg | 48KB | ✓ | ✗ | ✗ | JPG |
| pool.jpg | 28KB | ✓ | ✗ | ✗ | JPG |
| room-king.jpg | 28KB | ✓ | ✗ | ✗ | JPG |
| room-simple.jpg | 116KB | ✓ | ✗ | ✗ | JPG |
| **Total** | **~560KB** | 7/7 ✓ | 0/7 ✗ | 0/7 ✗ | 7/7 JPG |

## Lo que funciona ✓
- **Todos los alt texts presentes** — Excelente para accesibilidad y Google Image Search
- **Alt texts descriptivos y con keywords** — "Fachada y entrada del Hotel Jireh en Bacalar, Quintana Roo", "Alberca al aire libre del Hotel Jireh en Bacalar"
- **Nombres de archivo descriptivos** — facade-day, room-king, pool (no img001.jpg)

## Hallazgos

### [Critical] Logo en formato JPG (no SVG/PNG)
- **Evidencia**: `images/logo.jpg` (24KB)
- **Impacto**: JPG no soporta transparencia. El logo tiene fondo fijo, se ve mal sobre cualquier fondo de color diferente. Además, los logos deben ser vectoriales (SVG) para verse nítidos en pantallas Retina.
- **Solución**: Convertir logo a SVG o PNG con fondo transparente. Peso objetivo: <5KB en SVG.

### [Critical] 0/7 imágenes en formato WebP/AVIF
- **Evidencia**: Todas las imágenes son `.jpg`
- **Impacto en performance**:
  - facade-day.jpg (176KB) → WebP esperado: ~110KB (-37%)
  - facade-night.jpg (140KB) → WebP esperado: ~88KB (-37%)
  - room-simple.jpg (116KB) → WebP esperado: ~73KB (-37%)
  - **Ahorro total estimado: ~210KB (37%)**
- **Solución**:
  ```bash
  # Convertir con cwebp (en servidor/CI):
  cwebp -q 85 images/facade-day.jpg -o images/facade-day.webp
  ```
  Luego usar `<picture>` con fallback JPG.

### [High] 0/7 imágenes con `width` y `height` explícitos
- **Evidencia**: `<img src="images/facade-day.jpg" alt="Fachada...">` sin dimensiones
- **Impacto CLS**: Sin reserva de espacio, el contenido salta al cargar → CLS alto → penalización Core Web Vitals
- **Dimensiones a agregar**:
  - facade-day.jpg: width="800" height="1000" (ratio 4:5 según CSS)
  - facade-night.jpg: width="800" height="600"
  - room-*.jpg: width="600" height="450" (ratio 4:3 según CSS)
  - pool.jpg: width="600" height="450"
  - palapa.jpg: width="600" height="450"
  - logo.jpg: width="44" height="44" (ya aplicado en style)

### [High] 6/7 imágenes sin `loading="lazy"`
- **Evidencia**: Solo la imagen hero debería cargar inmediatamente. Las demás están below the fold.
- **Impacto**: El browser inicia descarga de ~560KB en el primer load, bloqueando LCP
- **Solución**: Agregar `loading="lazy"` a todas excepto `facade-day.jpg` (LCP):
  ```html
  <img src="images/pool.jpg" loading="lazy" width="600" height="450" alt="...">
  ```

### [High] Sin `srcset` para imágenes responsivas
- **Evidencia**: Una sola versión JPG para todos los dispositivos
- **Impacto**: Un iPhone descarga la misma imagen que un monitor 4K. En Bacalar, con cobertura móvil variable, esto impacta la experiencia.
- **Solución**: Generar versiones 400w, 800w, 1200w:
  ```html
  <img
    srcset="images/facade-day-400.webp 400w, images/facade-day-800.webp 800w, images/facade-day.webp 1200w"
    sizes="(max-width:880px) 100vw, 50vw"
    src="images/facade-day.jpg"
    alt="..." width="1200" height="1500" loading="eager">
  ```

### [Medium] Foto de palapa usada para Habitación Familiar
- **Evidencia**: `<img src="images/palapa.jpg" alt="Área de palapa..." >` en tarjeta de Habitación Familiar
- **Impacto**: El usuario ve foto de palapa cuando espera ver la habitación. Reduce conversión y credibilidad.
- **Solución**: Fotografiar la Habitación Familiar y usar esa imagen en su tarjeta

### [Low] Sin imagen OG optimizada (1200×630px)
- **Evidencia**: OG usa `facade-day.jpg` cuyo ratio es aproximadamente 4:5 (vertical), no 1.91:1 (horizontal) que requiere Open Graph
- **Impacto**: Al compartir en Facebook/WhatsApp/LinkedIn, la imagen se recorta de forma subóptima
- **Solución**: Crear versión 1200×630px de facade-day.jpg específicamente para redes sociales
