# Plan de Acción SEO — Hotel Jireh Bacalar
**Generado:** 22 de junio de 2026
**Score actual:** 62/100 → **Score proyectado Fase 1:** 74/100

---

## CRÍTICO — Esta semana (Días 1-3)

### 1. Crear robots.txt
**Archivo:** `/robots.txt`
```
User-agent: *
Allow: /
Sitemap: https://www.hoteljirehbacalar.com/sitemap.xml
```

---

### 2. Crear sitemap.xml
**Archivo:** `/sitemap.xml`
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

---

### 3. Agregar width y height a TODAS las imágenes en index.html

Buscar cada `<img>` y agregar dimensiones reales:

```html
<!-- Hero -->
<img src="images/facade-day.jpg"
     alt="Fachada y entrada del Hotel Jireh en Bacalar, Quintana Roo"
     width="800" height="1000"
     loading="eager">

<!-- Logo (en header y footer) -->
<img src="images/logo.jpg" alt="Logo Hotel Jireh Bacalar"
     width="44" height="44">

<!-- Galería -->
<img src="images/facade-night.jpg" alt="Patio y pasillo del Hotel Jireh de noche"
     width="800" height="600" loading="lazy">
<img src="images/room-simple.jpg" alt="Habitación Sencilla del Hotel Jireh con cama matrimonial"
     width="800" height="600" loading="lazy">
<img src="images/room-king.jpg" alt="Habitación King Size del Hotel Jireh"
     width="800" height="600" loading="lazy">
<img src="images/pool.jpg" alt="Alberca al aire libre del Hotel Jireh en Bacalar"
     width="800" height="600" loading="lazy">
<img src="images/palapa.jpg" alt="Área de palapa y mesas junto a la alberca del Hotel Jireh"
     width="800" height="600" loading="lazy">

<!-- Habitaciones -->
<img class="room-photo" src="images/room-simple.jpg" alt="Habitación Sencilla del Hotel Jireh"
     width="600" height="450" loading="lazy">
<img class="room-photo" src="images/room-king.jpg" alt="Habitación King Size del Hotel Jireh"
     width="600" height="450" loading="lazy">
<img class="room-photo" src="images/palapa.jpg" alt="Área de palapa del Hotel Jireh"
     width="600" height="450" loading="lazy">
```

---

### 4. Agregar preload para imagen hero
En `<head>`, **antes** de cualquier otro `<link>`:
```html
<link rel="preload" href="images/facade-day.jpg" as="image" fetchpriority="high">
```

---

### 5. Cargar fuentes correctamente
Reemplazar en `<head>` (después del preload):
```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Fraunces:ital,opsz,wght@0,9..144,600;1,9..144,600&family=Inter:wght@400;500;600&display=swap" rel="stylesheet">
```

Actualizar en CSS:
```css
body {
  font-family: 'Inter', 'Segoe UI', system-ui, sans-serif;
}
h1, h2, h3, .display {
  font-family: 'Fraunces', Georgia, 'Times New Roman', serif;
}
```

---

### 6. Agregar favicon
```html
<link rel="icon" href="/favicon.ico" sizes="any">
<link rel="icon" href="/favicon.svg" type="image/svg+xml">
<link rel="apple-touch-icon" href="/apple-touch-icon.png">
```
*(Generar desde logo en https://favicon.io o similar)*

---

### 7. Reclamar Google Business Profile
- URL: https://business.google.com
- Buscar "Hotel Jireh Bacalar"
- Verificar con postal o video
- Completar: horarios, fotos (mínimo 10), descripción, precios

---

## ALTO IMPACTO — Semana 2

### 8. Corregir og:type y agregar twitter:image
```html
<!-- Cambiar esto: -->
<meta property="og:type" content="lodging.hotel">
<!-- Por esto: -->
<meta property="og:type" content="website">

<!-- Agregar esta línea: -->
<meta name="twitter:image" content="https://www.hoteljirehbacalar.com/images/facade-day.jpg">
```

---

### 9. Agregar campos faltantes al schema Hotel
En el JSON-LD de `@type: "Hotel"`, agregar dentro del objeto principal:
```json
"image": [
  "https://www.hoteljirehbacalar.com/images/facade-day.jpg",
  "https://www.hoteljirehbacalar.com/images/pool.jpg",
  "https://www.hoteljirehbacalar.com/images/room-king.jpg",
  "https://www.hoteljirehbacalar.com/images/room-simple.jpg"
],
"sameAs": [
  "https://www.facebook.com/hoteljireh.bacalar/"
],
"hasMap": "https://maps.google.com/?q=Hotel+Jireh+Bacalar",
"currenciesAccepted": "MXN",
"paymentAccepted": "Efectivo, transferencia bancaria"
```

---

### 10. Crear llms.txt
**Archivo:** `/llms.txt`
```
# Hotel Jireh Bacalar

Hotel familiar económico en Bacalar, Quintana Roo, México.

## Información de contacto
- Teléfono / WhatsApp: +52 983 101 9716
- Email: hoteljireh.bacalar@gmail.com
- Facebook: https://www.facebook.com/hoteljireh.bacalar/
- Dirección: Avenida 19, entre Calle 22 y 24, Bacalar, Quintana Roo, CP 77930, México
- Coordenadas: 18.6840, -88.3975

## Habitaciones y precios (MXN por noche)
- Habitación Sencilla: $600 MXN — 1 cama matrimonial, máximo 2 personas
- Habitación King Size: $850 MXN — 1 cama king size, habitación más amplia
- Habitación Familiar: $950 MXN — 2 camas king size + 1 cama matrimonial

## Servicios incluidos
- Alberca al aire libre con área de palapa y mesas
- Aire acondicionado y ventilador en todas las habitaciones
- Agua fría y caliente
- TV por cable
- Wifi gratuito en habitaciones y áreas comunes
- Estacionamiento privado gratuito
- Recepción 24 horas
- Servicio de limpieza diaria

## Check-in y Check-out
- Check-in: a partir de las 13:30 horas
- Check-out: antes de las 12:00 horas
- Edad mínima para check-in: 18 años
- No se permiten mascotas

## Ubicación y distancias
- Fuerte de San Felipe Bacalar: 1.1 km
- Laguna de Bacalar (Parque Ecológico): ~5 minutos en auto
- Cenote de la Bruja: ~6 minutos caminando
- Canal de los Piratas: 1.7 km
- Cenote Azul: ~10 minutos en auto
- Terminal ADO Bacalar: a pie
- Aeropuerto Internacional de Chetumal: 25 km

## Calificación
7.2/10 basado en 142 opiniones de viajeros

## Reservaciones
Reservar por WhatsApp al +52 983 101 9716 o por correo a hoteljireh.bacalar@gmail.com
```

---

### 11. Optimizar title y meta description

```html
<!-- Title actual (82 chars — demasiado largo): -->
<title>Hotel Jireh Bacalar | Hotel Familiar Económico cerca de la Laguna de los 7 Colores</title>

<!-- Title optimizado (~62 chars): -->
<title>Hotel Jireh Bacalar | Hospedaje Económico cerca de la Laguna</title>

<!-- Meta description actual (240 chars — demasiado larga): -->
<!-- Meta description optimizada (~152 chars): -->
<meta name="description" content="Hotel Jireh: hospedaje familiar en Bacalar, QR. Habitaciones desde $600/noche con A/C, alberca, wifi y estacionamiento gratuito. Reserva por WhatsApp.">
```

---

### 12. Agregar Google Analytics 4
```html
<!-- Después del </title>, antes del </head>: -->
<!-- Google tag (gtag.js) — reemplazar G-XXXXXXXXXX con tu ID real -->
<script async src="https://www.googletagmanager.com/gtag/js?id=G-XXXXXXXXXX"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());
  gtag('config', 'G-XXXXXXXXXX');
</script>
```

---

### 13. Agregar Google Maps embed en sección ubicación
En `<section id="ubicacion">`, agregar después de `<div class="section-head">`:
```html
<div style="margin-bottom:32px;border-radius:14px;overflow:hidden;border:1px solid var(--borde);">
  <iframe
    src="https://maps.google.com/maps?q=Hotel+Jireh+Bacalar&output=embed&z=15"
    width="100%"
    height="320"
    style="border:0;display:block;"
    allowfullscreen=""
    loading="lazy"
    referrerpolicy="no-referrer-when-downgrade"
    title="Ubicación del Hotel Jireh en Google Maps">
  </iframe>
</div>
<p style="margin-bottom:16px;">
  <a href="https://maps.google.com/?q=Hotel+Jireh+Bacalar"
     target="_blank" rel="noopener"
     class="btn btn-outline" style="display:inline-flex;">
    Ver en Google Maps →
  </a>
</p>
```

---

## CONTENIDO — Mes 2

### 14. Agregar sección "Acerca del Hotel"
Antes del footer, agregar una nueva sección con 3-4 oraciones sobre la historia y familia propietaria.

### 15. Agregar badge de reseñas verificadas
Identificar la plataforma con 142 reseñas y agregar:
```html
<a href="[URL-DE-BOOKING-O-GOOGLE]" target="_blank" rel="noopener" class="btn btn-outline">
  ⭐ 7.2/10 en Booking.com — Ver 142 reseñas
</a>
```

### 16. Fotografiar Habitación Familiar
Reemplazar `images/palapa.jpg` en la tarjeta de Habitación Familiar por una foto real de esa habitación.

### 17. Convertir imágenes a WebP
```bash
# Instalar cwebp si es necesario: apt install webp
for img in images/*.jpg; do
  cwebp -q 85 "$img" -o "${img%.jpg}.webp"
done
```
Luego envolver cada `<img>` en `<picture>`:
```html
<picture>
  <source srcset="images/facade-day.webp" type="image/webp">
  <img src="images/facade-day.jpg" alt="..." width="800" height="1000" loading="eager">
</picture>
```

---

## Verificación Post-Implementación

- [ ] PageSpeed Insights: https://pagespeed.web.dev/?url=https://www.hoteljirehbacalar.com/
- [ ] Google Rich Results Test: https://search.google.com/test/rich-results
- [ ] Schema.org Validator: https://validator.schema.org/
- [ ] Google Search Console: enviar sitemap.xml
- [ ] Facebook Sharing Debugger: verificar OG tags
- [ ] Twitter Card Validator: verificar twitter:image
