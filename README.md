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
