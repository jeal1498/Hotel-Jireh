# Technical SEO — Hotel Jireh Bacalar
**Score: 48/100**

## Lo que funciona ✓
- `lang="es-MX"` declarado correctamente en `<html>`
- Meta viewport presente
- URL canónica declarada: `https://www.hoteljirehbacalar.com/`
- Skip link de accesibilidad implementado
- Estructura semántica HTML5 (header, main, footer, nav, section)
- HTTPS implícito en URL canónica
- Sin JavaScript externo (carga ultra-rápida)

## Hallazgos Críticos

### [Critical] robots.txt ausente
- **Evidencia**: Archivo `/robots.txt` no existe en el repositorio
- **Impacto**: Los crawlers de Google, Bing y motores de IA no tienen directivas. Sin `Sitemap:` declarado en robots.txt, el sitemap no se auto-descubre.
- **Solución**: Crear `/robots.txt` con `User-agent: *`, `Allow: /`, `Sitemap: https://www.hoteljirehbacalar.com/sitemap.xml`

### [Critical] sitemap.xml ausente
- **Evidencia**: Archivo `/sitemap.xml` no existe
- **Impacto**: Imposible enviar el sitio a Google Search Console ni a Bing Webmaster Tools. Sin sitemap, la indexación depende 100% del crawl orgánico.
- **Solución**: Crear `/sitemap.xml` con la URL canónica, lastmod y changefreq

### [High] Fuentes declaradas pero nunca cargadas
- **Evidencia**: CSS usa `font-family:'Inter Body'` y `font-family:'Fraunces Display'` pero no hay ningún `@font-face`, `<link>` a Google Fonts ni CDN de tipografías en el HTML
- **Impacto**: El navegador hace fallback a `Segoe UI` / `Georgia`. El diseño visual no corresponde a lo planificado. FOUT/FOIT potencial
- **Solución**: Agregar Google Fonts o Bunny Fonts para Inter y Fraunces Display, con `font-display:swap`

### [High] Menú móvil roto (<760px)
- **Evidencia**: `@media(max-width:760px){ nav.main-nav{display:none;} }` sin hamburger toggle ni alternativa
- **Impacto**: En smartphones, la navegación principal desaparece completamente sin reemplazo. Crítico para UX y Core Web Vitals de Interacción.
- **Solución**: Implementar menú hamburger con CSS/JS o botón `<details>/<summary>`

### [High] Sin Google Analytics ni Search Console
- **Evidencia**: No hay GTM, GA4, ni meta tag de verificación GSC
- **Impacto**: Imposible medir tráfico orgánico, conversiones WhatsApp, comportamiento de usuarios. Sin GSC no se pueden detectar errores de indexación.
- **Solución**: Instalar GA4 via GTM + verificar GSC con meta tag

### [Medium] Favicon ausente
- **Evidencia**: No existe `<link rel="icon">` ni `/favicon.ico`
- **Impacto**: Pestaña del navegador y resultados de búsqueda (favicon en SERP) sin imagen. Señal de sitio poco mantenido.
- **Solución**: Agregar favicon en múltiples tamaños (16x16, 32x32, 180x180 para Apple Touch)

### [Medium] Sin preconnect ni preload hints
- **Evidencia**: No hay `<link rel="preconnect">` ni `<link rel="preload">`
- **Impacto**: La imagen hero (`facade-day.jpg`, 176KB) es el candidato LCP y no está precargada. Impacto negativo en LCP score.
- **Solución**: `<link rel="preload" href="images/facade-day.jpg" as="image">`

### [Low] llms.txt ausente
- **Evidencia**: No existe `/llms.txt`
- **Impacto**: Los motores de IA (ChatGPT, Perplexity, Gemini) no tienen un archivo de contexto optimizado para entender el sitio
- **Solución**: Crear `/llms.txt` con descripción del negocio, servicios, precios y contacto en formato plano
