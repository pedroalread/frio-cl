# Frio.cl — Formación práctica de Product Owner & metodologías ágiles

Sitio one-page tipo deck (8 pantallas, navegación por transiciones) para la oferta de
mentorías y programas de formación: Product Owner (fuerte principal) y metodologías
ágiles en general (Agile Essentials).

## Estructura
- `index.html` — aplicación completa, autocontenida (CSS y JS embebidos, sin build).
  Fotos embebidas en base64. Únicos recursos externos opcionales: Google Fonts y Lenis
  (con fallbacks si no cargan).

## Configuración (bloque CONFIG al inicio del <script>)
- `whatsapp`   → número real (código país sin +). PENDIENTE: hoy es placeholder.
- `aiEndpoint` → URL del evaluador IA para el botón "Feedback con IA". Vacío = modo WhatsApp.
- `bookingLink` / `email` → reservados (agenda y respaldo de leads).
- `packs`      → nombres y precios (editar aquí).

## Flujo de trabajo (acordado)
- Rama `develop` → desarrollo continuo. Cada push genera URL Preview automática en Vercel.
- Rama `main` → producción. SOLO se actualiza con autorización explícita de Pedro.
- Historial real desde este commit; no crear proyectos paralelos.

## Decisiones de producto vigentes
- Público: estudiantes (precios con descuento estudiantil).
- Pagos: solo transferencia bancaria (sin pasarela por ahora).
- Sin garantía de empleo, sin testimonios falsos. Leads vía WhatsApp.
- Lead magnet: guía de historias de usuario (descarga TXT).
- Foto mentor: edición propia embebida; retoma profesional pendiente.

## Backlog próximo
1. Quiz de nivel (recomendador de programa).
2. Biblioteca de plantillas descargables (DoR/DoD, retros).
3. CONFIG.whatsapp con número real.
4. Endpoint IA para feedback automático.

## Capa de Agente IA (automatización de todo contacto con personas)
Filosofía: agente (LLM + herramientas + base de conocimiento), NO bot de reglas.
KB = este repo (sitio + políticas de precios/pagos). Canal principal: WhatsApp Business
(Cloud API, gratis). Respaldo: correo.

### Contrato de endpoints (el sitio ya habla este idioma)
| Endpoint | Payload | Respuesta | Uso |
|---|---|---|---|
| POST /evaluate | {answer, rubric:"po-40-30-30"} | {feedback} | Botón "Feedback con IA" → CONFIG.aiEndpoint |
| POST /lead | {name, email, source, ts} | 204 | Notificación automática de leads (YA CABLEADO) → CONFIG.leadEndpoint |
| POST /quiz | {answers[]} | {level, recommendedPack, message} | Quiz de nivel (backlog) |
| POST /plan | {sessionNotes} | {plan} | Plan de mejora post-sesión |
| POST /followup | {leadId, type} | 204 | Recordatorios 24h y reactivación de leads fríos |

### Mapa de automatización (interacción → agente)
- Descarga de guía → el sitio ya notifica al agente (leadEndpoint) + abre WhatsApp.
- Click en pack → agente responde 24/7: precios, datos de transferencia, agenda, objeciones.
- Feedback de casos → evaluador automático con la rúbrica (aiEndpoint).
- FAQ → agente con KB del sitio (WhatsApp/correo).
- Agenda → agente ofrece horarios vía Cal.com API (CONFIG.bookingLink).
- Post-sesión → agente redacta el plan desde notas de la sesión.

### Implementación sugerida
n8n (self-host) o servidor propio + API de LLM + WhatsApp Cloud API de Meta.
Orden de construcción: 1) /evaluate, 2) agente WhatsApp con KB, 3) /quiz, 4) /followup.

### Personalidad del agente (reglas de voz: que se sienta humano)
- Español de Chile (es-419), SIEMPRE primera persona. Prohibido decir "como IA", "como modelo de lenguaje" o similar.
- Usa el nombre de la persona apenas la conoces y recuérdalo entre mensajes.
- Estructura: saludo breve + reconocimiento de lo que dijo + respuesta + máximo UNA pregunta.
- Admite dudas con naturalidad ("puede que no tenga el dato exacto de tu caso, pero…") en vez de inventar.
- Largo tipo mensaje de WhatsApp: 2–4 frases cortas, párrafos chicos; listas solo si piden un plan.
- Latencia humana: nunca responder al instante; 1.5–4 s según complejidad, con indicador de "escribiendo…".
- Firma con criterio ("— tu mentor") y despedidas cálidas pero breves.
- El sitio ya implementa esto: latencia mínima + escritura progresiva (typeOut) + tono de primera persona.
