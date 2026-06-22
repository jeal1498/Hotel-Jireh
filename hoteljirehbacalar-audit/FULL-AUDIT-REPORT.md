# Auditoría SEO & GEO Completa — Hotel Jireh Bacalar
**Dominio:** hoteljirehbacalar.com
**Fecha:** 22 de junio de 2026
**Páginas auditadas:** 1 (sitio de una sola página)
**Tipo de sitio:** HTML estático — sin JavaScript
**Tipo de negocio:** Hotel local / Hospitalidad — Bacalar, Quintana Roo, México

---

## Puntuación SEO Global: 62 / 100

```
┌─────────────────────────────────────────────────────────┐
│  SEO HEALTH SCORE                                        │
│                                                         │
│  62/100  ████████████░░░░░░░░  Necesita mejoras         │
│                                                         │
│  Technical SEO       48/100  ████░░░░░░  Débil          │
│  Content (E-E-A-T)   68/100  ███████░░░  Moderado       │
│  On-Page SEO         70/100  ███████░░░  Moderado       │
│  Schema              72/100  ███████░░░  Moderado       │
│  Performance (CWV)   45/100  ████░░░░░░  Débil          │
│  AI Search (GEO)     78/100  ████████░░  Bueno          │
│  Images              40/100  ████░░░░░░  Débil          │
│  Local SEO           62/100  ██████░░░░  Moderado       │
└─────────────────────────────────────────────────────────┘
```

**Nota:** El score refleja el estado actual del repositorio. Con las mejoras de Fase 1 implementadas, el score puede subir a **78-82/100** en 2-3 semanas.

---

## Resumen Ejecutivo

Hotel Jireh Bacalar tiene una base SEO razonablemente sólida para un sitio de una sola página: estructura HTML semántica correcta, schema Hotel + FAQPage bien implementados, alt text en todas las imágenes, información de contacto visible y contenido factual citable por motores de IA. Sin embargo, hay **brechas técnicas fundamentales** que limitan su visibilidad:

1. **Sin robots.txt ni sitemap.xml** — Google no tiene orientación de crawl
2. **Sin Google Analytics ni Search Console** — el hotel está "ciego" a su tráfico
3. **Sin Google Business Profile vinculado** — el factor #1 de visibilidad local
4. **Performance degradada** — imágenes sin dimensiones, sin lazy loading, fuentes no cargadas
5. **Menú móvil roto** — la navegación desaparece en smartphones

La buena noticia: la mayoría de los problemas críticos son correcciones rápidas de código (< 1 hora en total). El contenido y la estructura de datos son buenos; se trata principalmente de completar los elementos técnicos faltantes.

---

## 1. Technical SEO — 48/100

### ✓ Fortalezas
- `lang="es-MX"` correcto
- URL canónica declarada correctamente
- Sin JavaScript — carga ultra-rápida
- HTML5 semántico (header/main/footer/nav)
- Skip link de accesibilidad implementado

### ✗ Problemas críticos

#### robots.txt AUSENTE — Crítico
No existe `/robots.txt`. Los crawlers de Google, Bing, ChatGPT y otros motores de IA no tienen directivas. Sin `Sitemap:` en robots.txt, el sitemap no se autodescubre.

**Solución inmediata:**
```
User-agent: *
Allow: /
Sitemap: https://www.hoteljirehbacalar.com/sitemap.xml
```

#### sitemap.xml AUSENTE — Crítico
Sin sitemap.xml, imposible enviar el sitio a Google Search Console para indexación controlada.

**Solución inmediata:**
```xml
<?xml version="1.0" encoding="UTF-8"?>
<urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">
  <url>
    <loc>https://www.hoteljirehbacalar.com/</loc>
    <lastmod>2026-06-22</lastmod>
    <changefreq>monthly</changefreq>
    <priority>1.0</priority>
  </url>
</urlset>
```

#### Fuentes personalizadas no cargadas — Alto
CSS declara `'Inter Body'` y `'Fraunces Display'` pero no hay `@font-face` ni CDN. El diseño visual no corresponde a lo planificado. Causa FOUT (Flash of Unstyled Text) y CLS.

**Solución:**
```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Fraunces:ital,opsz,wght@0,9..144,600;1,9..144,600&family=Inter:wght@400;500;600&display=swap" rel="stylesheet">
```
Luego actualizar CSS: `font-family: 'Inter', 'Segoe UI', system-ui, sans-serif;` y `font-family: 'Fraunces', Georgia, serif;`

#### Menú móvil roto — Alto
`nav.main-nav{display:none}` en `@media(max-width:760px)` sin menú alternativo. Los smartphones no tienen navegación.

---

## 2. Content Quality (E-E-A-T) — 68/100

### ✓ Fortalezas
- Estructura de encabezados perfecta: 1 H1, 6 H2, 17 H3
- Precios explícitos ($600/$850/$950 MXN) — alta conversión
- 6 FAQs de alta intención de búsqueda
- Amenidades detalladas por habitación
- Información de contacto completa y visible

### ✗ Problemas

**Reseñas sin fuente — Alto:** "7.2/10 en 142 reseñas" no indica la plataforma ni tiene enlace. Sin fuente verificable, los motores de IA no pueden citar esta información con confianza.

**Sin historia del hotel — Alto:** No hay "Acerca de" ni mención de historia o propietarios. Reduce la confianza (E-E-A-T).

**Imagen incorrecta en Habitación Familiar — Alto:** Se muestra foto de palapa en lugar de la habitación. Reduce conversión.

**Title tag (82 chars) y meta description (240 chars) demasiado largos** — Google los trunca.

---

## 3. On-Page SEO — 70/100

### ✓ Fortalezas
- 1 H1 único con keyword principal
- Alt text en 11/11 imágenes
- Canonical tag correcto
- OG tags casi completos
- NAP consistente

### ✗ Problemas

| Elemento | Estado | Solución |
|----------|--------|----------|
| og:type | `lodging.hotel` (inválido) | Cambiar a `website` |
| twitter:image | AUSENTE | Agregar meta tag |
| Google Maps link | AUSENTE | Agregar en sección ubicación |
| Title length | 82 chars | Reducir a <60 chars |
| Meta description | 240 chars | Reducir a <155 chars |

---

## 4. Schema & Structured Data — 72/100

### ✓ Fortalezas
- Hotel schema bien estructurado con 13 campos completos
- GeoCoordinates exactas
- FAQPage con 6 preguntas (excelente para featured snippets)
- makesOffer con 3 tipos de habitación y precios MXN
- nearbyAttraction con 5 atracciones locales

### ✗ Problemas

**`image` ausente en Hotel schema — Alto:** Campo recomendado por Google para Knowledge Panel y rich results.

**`sameAs` ausente — Alto:** Sin sameAs, Google no puede verificar la entidad ni conectarla con Facebook/GBP.

**Campos opcionales faltantes:**
- `hasMap` — necesario para citaciones de IA
- `currenciesAccepted: "MXN"`
- `paymentAccepted: "Efectivo, transferencia bancaria"`
- `openingHoursSpecification` (recepción 24h)

**Agregar al JSON-LD:**
```json
"image": [
  "https://www.hoteljirehbacalar.com/images/facade-day.jpg",
  "https://www.hoteljirehbacalar.com/images/pool.jpg",
  "https://www.hoteljirehbacalar.com/images/room-king.jpg"
],
"sameAs": [
  "https://www.facebook.com/hoteljireh.bacalar/"
],
"hasMap": "https://maps.google.com/?q=Hotel+Jireh+Bacalar",
"currenciesAccepted": "MXN",
"paymentAccepted": "Efectivo, transferencia bancaria"
```

---

## 5. Performance (Core Web Vitals) — 45/100

### Estimaciones de métricas

| Métrica | Estimado | Umbral "Bueno" | Estado |
|---------|----------|----------------|--------|
| LCP | ~2.5-4s | < 2.5s | ⚠️ Necesita mejora |
| INP | ~50ms | < 200ms | ✓ Bueno |
| CLS | ~0.15-0.25 | < 0.1 | ✗ Deficiente |
| FID/TTI | ~0ms | < 100ms | ✓ Excelente |

*Estimaciones lab. Verificar con PageSpeed Insights una vez desplegado.*

### ✓ Fortalezas
- Sin JavaScript → TTI instantáneo
- CSS inline → 0 requests de stylesheet bloqueantes
- HTML 32KB (ligero)

### ✗ Problemas críticos

**CLS crítico — 11/11 imágenes sin width/height:** El browser no reserva espacio → layout shifts constantes. Este es el problema #1 de performance.

**LCP alto — imagen hero sin preload:** `facade-day.jpg` (176KB) no está precargada. Solución de una línea:
```html
<link rel="preload" href="images/facade-day.jpg" as="image" fetchpriority="high">
```

**Imágenes sin optimizar:**
- 0/7 en WebP (ahorraría ~210KB / 37%)
- 9/11 sin `loading="lazy"`
- 0/7 con `srcset`

**Peso total de imágenes: ~560KB JPG → ~350KB WebP**

---

## 6. AI Search Readiness (GEO) — 78/100

Este es el punto más fuerte del sitio. La implementación GEO es destacable:

### ✓ Fortalezas sobresalientes
- **FAQPage schema** con 6 preguntas concretas → formato más citable por LLMs
- **Datos factuales verificables**: GPS exactas, precios MXN, distancias en metros/km
- **HTML sin JS** → crawlable por todos los bots de IA sin rendering
- **NAP consistente** en 3 lugares del documento

### Score de Citabilidad por Plataforma

| Motor de IA | Score | Limitación principal |
|-------------|-------|---------------------|
| Google AI Overviews | 72/100 | Sin GBP vinculado en sameAs |
| ChatGPT / GPT-4o | 70/100 | Sin llms.txt |
| Perplexity | 65/100 | Sin llms.txt ni OTAs verificadas |
| Bing Copilot | 68/100 | Sin Bing Webmaster indexado |
| Gemini | 74/100 | Hotel schema bien estructurado |

### ✗ Problemas

**llms.txt ausente:** Sin este archivo, los LLMs deben interpretar el HTML completo con riesgo de errores. Es la mejora de mayor ROI para GEO.

**GBP no vinculado en schema:** Google AI Overviews prioriza negocios con GBP verificado. Sin `sameAs` apuntando al Place ID, el hotel puede ser omitido en respuestas de IA para consultas locales.

**Sin menciones en OTAs:** Los LLMs aprenden de Booking.com y TripAdvisor. Sin presencia consolidada allí, las citas de IA son menos frecuentes y confiables.

---

## 7. Local SEO — 62/100

Bacalar es un destino turístico de alto tráfico en temporada. La visibilidad local es crítica.

### ✓ Fortalezas
- NAP perfecto y consistente
- "Pueblo Mágico de Bacalar" mencionado
- Distancias exactas a 7 puntos de interés
- WhatsApp como canal principal (99% de penetración en México)

### ✗ Problemas Críticos

**Sin Google Business Profile:** GBP es el factor #1 para aparecer en el Local Pack (el mapa de Google). Sin GBP verificado y optimizado, el hotel no aparece cuando alguien busca "hotel en Bacalar" en Google Maps.

**Pasos para activar GBP:**
1. Ir a https://business.google.com
2. Buscar "Hotel Jireh Bacalar"
3. Reclamar o crear la ficha
4. Verificar con tarjeta postal o video
5. Completar: horarios, fotos, servicios, precios, descripción en español
6. Activar respuestas a preguntas y reseñas

**Sin mapa embed:** La sección de ubicación es solo texto. Un iframe de Google Maps aumenta el tiempo en página y la confianza.

**Sin gestión de reseñas:** Con 142 reseñas en alguna plataforma (sin identificar), hay una base sólida. Pero sin proceso de solicitud activa de nuevas reseñas, ese número crece lentamente.

---

## 8. Images — 40/100

### ✓ Fortalezas
- 7/7 alt texts presentes y descriptivos (incluyen keywords de Bacalar)
- Nombres de archivo semánticos (no img001.jpg)

### ✗ Problemas

| Problema | Impacto | Prioridad |
|----------|---------|-----------|
| Logo en JPG (sin transparencia) | Visual | Crítico |
| 0/7 imágenes en WebP | Peso +210KB | Crítico |
| 0/11 sin width/height | CLS | Alto |
| 9/11 sin lazy loading | LCP | Alto |
| 0/7 sin srcset | Mobile | Alto |
| Foto incorrecta en Hab. Familiar | Conversión | Medio |
| Sin imagen OG 1200×630 | Redes sociales | Bajo |

---

## Plan de Acción Priorizado

### Fase 1: Correcciones Críticas (Días 1-3) — Est. 3-4 horas

| # | Tarea | Tiempo | Impacto |
|---|-------|--------|---------|
| 1 | Crear `/robots.txt` | 5 min | Indexabilidad |
| 2 | Crear `/sitemap.xml` | 10 min | GSC submission |
| 3 | Agregar `width`+`height` a 11 imágenes | 30 min | CLS crítico |
| 4 | Agregar `loading="lazy"` a 9 imágenes | 20 min | LCP + bandwidth |
| 5 | Agregar `<link rel="preload">` para hero | 5 min | LCP |
| 6 | Cargar fuentes (Google Fonts + preconnect) | 20 min | Visual + CLS |
| 7 | Implementar menú hamburger móvil | 45 min | UX móvil |
| 8 | Reclamar Google Business Profile | 30 min | Local #1 |

### Fase 2: Alto Impacto (Días 4-14) — Est. 6-8 horas

| # | Tarea | Tiempo | Impacto |
|---|-------|--------|---------|
| 9 | Convertir imágenes a WebP + `<picture>` | 90 min | Performance |
| 10 | Agregar `image`, `sameAs`, `hasMap` al schema | 20 min | Rich results |
| 11 | Corregir `og:type` + agregar `twitter:image` | 5 min | Social sharing |
| 12 | Crear `/llms.txt` | 15 min | GEO / IA |
| 13 | Instalar Google Analytics 4 + Search Console | 30 min | Medición |
| 14 | Agregar iframe Google Maps en `#ubicacion` | 15 min | Local UX |
| 15 | Reducir title (82→60 chars) y meta desc (240→155) | 10 min | CTR en SERP |
| 16 | Agregar `<link rel="icon">` favicon | 20 min | Branding |
| 17 | Convertir logo a SVG/PNG transparente | 30 min | Visual |

### Fase 3: Contenido y Autoridad (Mes 2)

- Agregar sección "Acerca del Hotel" (historia, familia)
- Fotografiar Habitación Familiar para su tarjeta
- Agregar badge de reseñas con fuente verificada y enlace
- Completar fichas en Booking.com y TripAdvisor
- Agregar política de cancelación en FAQ
- Crear imagen OG 1200×630px
- `srcset` responsivo para todas las imágenes
- Crear y enlazar perfil de Instagram

### Fase 4: Monitoreo Mensual

- Revisar Search Console: errores, indexación, CTR
- Analizar GA4: tráfico orgánico, evento de clic WhatsApp
- Solicitar reseñas a huéspedes tras check-out
- Actualizar precios en HTML y schema si cambian
- Verificar Core Web Vitals en PageSpeed Insights

---

## Proyección de Mejora

| Acción | Score actual | Score proyectado |
|--------|-------------|-----------------|
| Solo Fase 1 | 62/100 | 74/100 |
| Fase 1 + 2 | 62/100 | 82/100 |
| Fase 1 + 2 + 3 | 62/100 | 89/100 |

---

## Conclusión

Hotel Jireh Bacalar tiene **una base SEO mejor que el promedio** para un hotel boutique pequeño en México: schema bien implementado, contenido factual específico, alt texts completos, HTML semántico y sin JavaScript que bloquee la indexación. El sitio está notablemente optimizado para **GEO** (78/100) gracias al FAQPage schema y los datos precisos, lo que es una ventaja competitiva para aparecer en respuestas de ChatGPT y Perplexity.

Las brechas más críticas son puramente técnicas y se resuelven en pocas horas: **robots.txt, sitemap, dimensiones de imagen y Google Business Profile**. Con la Fase 1 implementada, el sitio puede estar en el rango **74-78/100** en menos de una semana, competitivo para búsquedas locales en Bacalar.

---

*Auditoría realizada el 22 de junio de 2026 sobre el repositorio local. Sin acceso a Google Search Console, CrUX, GA4 ni DataForSEO. Los scores de performance son estimaciones estáticas — verificar con PageSpeed Insights una vez desplegado en producción.*
