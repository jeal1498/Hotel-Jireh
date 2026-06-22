# Schema & Structured Data — Hotel Jireh Bacalar
**Score: 72/100**

## Implementación actual

### Bloque 1: `Hotel` (Schema.org)
Ubicación: `<head>` → `<script type="application/ld+json">`

| Campo | Estado |
|-------|--------|
| name | ✓ "Hotel Jireh Bacalar" |
| description | ✓ Descripción completa |
| url | ✓ https://www.hoteljirehbacalar.com/ |
| telephone | ✓ +529831019716 |
| email | ✓ hoteljireh.bacalar@gmail.com |
| address (PostalAddress) | ✓ Completo con CP 77930 |
| geo (GeoCoordinates) | ✓ lat: 18.6840, lng: -88.3975 |
| aggregateRating | ✓ 7.2/10, 142 ratingCount |
| amenityFeature (8 items) | ✓ Completo |
| priceRange | ✓ "$600 - $950 MXN" |
| starRating (2★) | ⚠️ Ver nota |
| checkinTime / checkoutTime | ✓ 13:30 / 12:00 |
| makesOffer (3 tipos) | ✓ Sencilla/King/Familiar con precios |
| nearbyAttraction (5 items) | ✓ |
| **image** | ✗ AUSENTE |
| **sameAs** | ✗ AUSENTE |
| **hasMap** | ✗ AUSENTE |
| **currenciesAccepted** | ✗ AUSENTE |
| **paymentAccepted** | ✗ AUSENTE |
| **openingHoursSpecification** | ✗ AUSENTE |

### Bloque 2: `FAQPage`
6 preguntas estructuradas correctamente. Excelente para featured snippets y citaciones de IA.

## Hallazgos

### [High] Propiedad `image` ausente en esquema Hotel
- **Evidencia**: No existe campo `"image"` en el JSON-LD de Hotel
- **Impacto**: Google no puede mostrar imagen del hotel en Knowledge Panel ni en rich results de hotel. Es un campo recomendado por Google para hoteles.
- **Solución**:
```json
"image": [
  "https://www.hoteljirehbacalar.com/images/facade-day.jpg",
  "https://www.hoteljirehbacalar.com/images/pool.jpg",
  "https://www.hoteljirehbacalar.com/images/room-king.jpg"
]
```

### [High] Propiedad `sameAs` ausente
- **Evidencia**: No hay `"sameAs"` vinculando perfiles sociales
- **Impacto**: Google no puede conectar la entidad del hotel con sus perfiles verificados (Facebook, Google Business, Booking.com). Reduce la autoridad de la entidad Knowledge Graph.
- **Solución**:
```json
"sameAs": [
  "https://www.facebook.com/hoteljireh.bacalar/",
  "https://maps.google.com/?cid=<PLACE_ID>"
]
```

### [Medium] `og:type` usa valor no estándar
- **Evidencia**: `<meta property="og:type" content="lodging.hotel">`
- **Impacto**: El protocolo Open Graph solo acepta tipos base (`website`, `article`, `video`, `music`, `profile`). `lodging.hotel` no es un tipo OG válido — Facebook y LinkedIn podrían ignorar este tag o tratarlo como error.
- **Solución**: Cambiar a `<meta property="og:type" content="website">`

### [Medium] Propiedad `hasMap` ausente
- **Evidencia**: No hay `"hasMap"` con enlace a Google Maps
- **Impacto**: Los motores generativos (ChatGPT, Perplexity) no pueden proporcionar enlace directo al mapa al citar el hotel
- **Solución**:
```json
"hasMap": "https://maps.google.com/?q=Hotel+Jireh+Bacalar"
```

### [Medium] `starRating: 2` — verificar exactitud
- **Evidencia**: `"starRating": {"@type": "Rating", "ratingValue": "2"}`
- **Riesgo**: Si el hotel no tiene categorización oficial de 2 estrellas por Sectur u organismo equivalente, usar este campo puede ser engañoso. Google puede mostrar "2★" en resultados.
- **Solución**: Si no hay categorización oficial, eliminar `starRating`. Si es oficial, agregar `"author": {"@type":"Organization","name":"Sectur México"}`

### [Medium] `currenciesAccepted` y `paymentAccepted` ausentes
- **Evidencia**: Sin estos campos, los motores de IA no pueden responder "¿Qué formas de pago acepta?"
- **Solución**:
```json
"currenciesAccepted": "MXN",
"paymentAccepted": "Efectivo, transferencia bancaria"
```

### [Low] `openingHoursSpecification` ausente
- **Evidencia**: Solo hay checkin/checkout. La recepción es 24 horas pero no está formalizada en schema.
- **Solución**: Agregar spec de apertura para recepción 24h

### [Low] Twitter Card sin `twitter:image`
- **Evidencia**: Bloque Twitter Card completo pero sin `<meta name="twitter:image">`
- **Impacto**: Al compartir en X/Twitter, el card mostrará solo texto sin imagen
- **Solución**: `<meta name="twitter:image" content="https://www.hoteljirehbacalar.com/images/facade-day.jpg">`
