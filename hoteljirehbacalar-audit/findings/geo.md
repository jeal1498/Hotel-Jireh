# GEO (Generative Engine Optimization) — Hotel Jireh Bacalar
**Score: 78/100**

GEO mide qué tan bien posicionado está el contenido para ser citado por motores de IA como
ChatGPT, Perplexity, Google AI Overviews, Gemini y Bing Copilot.

## Lo que funciona ✓

### Estructura de datos citables
- **FAQPage schema** con 6 preguntas específicas y respuestas completas — el formato más citable por LLMs
- **Hotel schema** con datos verificables: coordenadas GPS exactas, precios MXN, horarios checkin/checkout
- **Datos factuales explícitos**: "$600 MXN/noche", "1.1 km al Fuerte de San Felipe", "lat: 18.6840, lng: -88.3975"
- **NAP consistente** en schema, HTML y footer (nombre, dirección, teléfono idénticos)
- **Atracciones cercanas** mapeadas con distancias exactas — útil para consultas "¿qué hay cerca de...?"

### Contenido limpio y parseable
- Sin JavaScript que bloquee el contenido para crawlers de IA
- HTML semántico (header/main/section/footer) facilita la extracción de contenido
- Texto plano accesible sin dependencia de JS rendering

### Señales de autoridad local
- Keyword "Pueblo Mágico de Bacalar" presente
- "Laguna de los 7 Colores" mencionada (variante de nombre popular)
- Coordenadas GPS verificables en schema

## Hallazgos

### [High] llms.txt ausente
- **Evidencia**: No existe `/llms.txt`
- **¿Qué es llms.txt?**: Archivo de texto plano que resume el sitio para crawlers de LLMs (análogo a robots.txt pero para modelos de IA). Perplexity y otros motores lo leen.
- **Impacto**: Sin este archivo, los LLMs deben inferir el contexto del HTML completo, con riesgo de errores o información incompleta.
- **Solución**: Crear `/llms.txt` con:
```
# Hotel Jireh Bacalar

Hotel familiar económico en Bacalar, Quintana Roo, México.

## Información esencial
- Nombre: Hotel Jireh Bacalar
- Dirección: Avenida 19, entre Calle 22 y 24, Bacalar, QR, CP 77930, México
- Teléfono: +52 983 101 9716
- Email: hoteljireh.bacalar@gmail.com
- Facebook: https://www.facebook.com/hoteljireh.bacalar/

## Habitaciones y precios (MXN por noche)
- Sencilla (2 personas, cama matrimonial): $600 MXN
- King Size (cama king): $850 MXN
- Familiar (2 king + 1 matrimonial): $950 MXN

## Servicios incluidos
Alberca al aire libre, palapa, wifi gratuito, A/C, TV por cable,
estacionamiento privado gratuito, recepción 24h, agua fría y caliente.

## Check-in / Check-out
Check-in: 13:30 | Check-out: 12:00 | Edad mínima: 18 años

## Ubicación
- Fuerte de San Felipe Bacalar: 1.1 km
- Laguna de Bacalar: ~5 min en auto
- Cenote de la Bruja: ~6 min caminando
- Terminal ADO Bacalar: a pie
- Aeropuerto Chetumal: 25 km
- Coordenadas: 18.6840, -88.3975

## Calificación
7.2/10 basado en 142 opiniones de viajeros
```

### [High] Sin enlace a Google Business Profile (GBP)
- **Evidencia**: No hay `sameAs` con Google Maps Place ID en el schema
- **Impacto GEO**: Google AI Overviews usa datos de GBP para responder consultas locales como "hotel económico en Bacalar". Sin GBP vinculado, el hotel puede ser ignorado.
- **Solución**: Reclamar/actualizar GBP y agregar `sameAs` con el Place URL en el schema Hotel.

### [Medium] Señales de marca insuficientes para desambiguación
- **Evidencia**: "Jireh" es un término hebreo bíblico. Sin contexto, un LLM podría confundirlo con otros negocios con el mismo nombre en otras ciudades.
- **Impacto**: En consultas sin "Bacalar", la IA puede citar el hotel incorrecto
- **Solución**: Usar sistemáticamente "Hotel Jireh Bacalar" (nombre completo con ciudad) en todos los H1, H2, schema y llms.txt. Evitar mencionar solo "Hotel Jireh".

### [Medium] Sin menciones en directorios de viajes
- **Evidencia**: No hay enlace ni mención a Booking.com, TripAdvisor, Airbnb, Expedia
- **Impacto GEO**: Los LLMs aprenden de fuentes como TripAdvisor y Booking.com. Si el hotel no tiene presencia consolidada allí, las respuestas de IA serán menos frecuentes y menos precisas.
- **Solución**: Asegurar ficha completa en Booking.com y TripAdvisor, y agregar el enlace en el footer del sitio.

### [Low] Política de cancelación no documentada
- **Impacto GEO**: Consultas tipo "¿se puede cancelar reserva en Hotel Jireh?" quedarán sin respuesta en AI Overviews
- **Solución**: Agregar FAQ con política de cancelación

### [Low] Sin información sobre el número total de habitaciones
- **Impacto GEO**: LLMs no pueden responder "¿cuántas habitaciones tiene el Hotel Jireh?"
- **Solución**: Agregar `"numberOfRooms"` al schema Hotel y mencionarlo en el contenido

## Score de Citabilidad por Plataforma

| Motor de IA | Score | Razón |
|-------------|-------|-------|
| Google AI Overviews | 72/100 | Hotel schema + FAQ, pero sin GBP vinculado |
| ChatGPT/GPT-4o | 70/100 | Datos factuales buenos, sin llms.txt |
| Perplexity | 65/100 | Sin llms.txt ni fuentes verificadas externas |
| Bing Copilot | 68/100 | Sin Bing Webmaster ni datos estructurados Bing |
| Gemini | 74/100 | Schema Hotel bien estructurado |
