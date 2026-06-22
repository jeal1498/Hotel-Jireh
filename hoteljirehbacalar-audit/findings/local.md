# Local SEO — Hotel Jireh Bacalar
**Score: 62/100**

## Lo que funciona ✓
- **NAP consistente**: Nombre, dirección y teléfono idénticos en schema, HTML y footer
- **GeoCoordinates** en schema (18.6840, -88.3975)
- **Código postal** correcto en schema (77930)
- **Mención "Pueblo Mágico"** — keyword de alto valor para turismo en Bacalar
- **Atracciones cercanas** bien documentadas con distancias
- **WhatsApp flotante** — Canal de conversión principal optimizado
- **Acceso en auto y a pie** desde terminal ADO mencionado

## Hallazgos

### [Critical] Sin Google Business Profile (GBP) verificado o vinculado
- **Evidencia**: No hay enlace a Google Maps, no hay Place ID en schema, no hay mención de GBP en el sitio
- **Impacto**: GBP es el factor #1 para aparecer en el Local Pack de Google (el mapa que aparece cuando alguien busca "hotel en Bacalar"). Sin GBP optimizado, el hotel es invisible para búsquedas locales en Maps.
- **Solución**:
  1. Reclamar/verificar GBP en https://business.google.com
  2. Completar: horarios, fotos, servicios, precios, descripción
  3. Agregar `sameAs` con Google Maps URL en el schema
  4. Agregar botón "Ver en Google Maps" en la sección de ubicación

### [High] Sin mapa embed en la sección de ubicación
- **Evidencia**: La sección `#ubicacion` solo tiene lista de distancias. No hay iframe de Google Maps.
- **Impacto**: Los usuarios no pueden visualizar la ubicación exacta del hotel. Aumenta la fricción para llegar.
- **Solución**: Agregar `<iframe>` de Google Maps con el Place del Hotel Jireh

### [High] Sin programa de gestión de reseñas
- **Evidencia**: Se menciona "7.2/10 en 142 reseñas" pero sin fuente ni enlace. Sin widget de reseñas.
- **Impacto**: Los viajeros no pueden leer ni dejar reseñas directamente desde el sitio. Las reseñas son el factor #2 de ranking local.
- **Solución**:
  - Identificar la plataforma con 142 reseñas (posiblemente Booking.com)
  - Agregar enlace "Leer reseñas en [plataforma]" con badge de calificación
  - Crear proceso para solicitar reseñas a huéspedes tras el check-out

### [High] Sin TripAdvisor ni Booking.com links
- **Evidencia**: Footer solo enlaza a Facebook. Sin OTAs visibles.
- **Impacto**: Los viajeros internacionales que buscan en TripAdvisor/Booking no encuentran el hotel desde el sitio web. Sin listados OTA, el hotel depende 100% de búsqueda directa.
- **Solución**: Agregar sección "Encuéntranos en" con links a Booking.com, TripAdvisor y Google

### [Medium] Sección de ubicación sin Google Maps link
- **Evidencia**: "En Bacalar, cerca de todo lo importante" describe la zona pero sin URL de Maps
- **Solución**: `<a href="https://maps.google.com/?q=Hotel+Jireh+Bacalar" target="_blank">Ver en Google Maps →</a>`

### [Medium] Schema sin `openingHoursSpecification` formal
- **Evidencia**: Recepción 24h mencionada en texto pero no en schema
- **Solución**:
```json
"openingHoursSpecification": {
  "@type": "OpeningHoursSpecification",
  "dayOfWeek": ["Monday","Tuesday","Wednesday","Thursday","Friday","Saturday","Sunday"],
  "opens": "00:00",
  "closes": "23:59"
}
```

### [Low] Sin información de transporte público
- **Evidencia**: Se menciona "Terminal ADO a pie" pero sin más detalle
- **Impacto**: Viajeros que llegan en autobús no saben exactamente cómo llegar al hotel
- **Solución**: Agregar instrucciones breves: "A 5 minutos a pie de la Terminal ADO Bacalar"

### [Low] Facebook como único perfil social
- **Evidencia**: Solo se enlaza a Facebook. Sin Instagram, TikTok ni YouTube.
- **Impacto**: Hoteles con presencia en Instagram tienen mejor visibilidad para turistas jóvenes que buscan en esa plataforma.
- **Solución**: Crear y enlazar perfil de Instagram con fotos de las instalaciones
