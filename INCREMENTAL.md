---
titulo: Frio.cl — Incremental del proyecto
tipo: incremental
proyecto: frio-cl
actualizado: 2025-11-15
tags: [frio-cl, po, agile, mentorias, web, incremental]
---

# Frio.cl — Incremental (estado del proyecto)

## Qué es
Sitio one-page tipo deck (8 pantallas, navegación por transiciones, cero scroll de página)
para vender formación práctica: **Product Owner** (fuerte principal) y **metodologías ágiles**
en general. Público: estudiantes (precios con descuento estudiantil). Pagos: solo
transferencia bancaria. Captación de leads vía WhatsApp. Sin garantía de empleo, sin
testimonios falsos.

## Historial de iteraciones
- **V1–V6**: landing de entrevistas fintech (contexto previo, recuperado de hoja de trabajo).
- **V7**: reconstrucción como experiencia app/deck con transiciones (Loop de diseño).
- **V8**: deck de 6 pantallas + motor de navegación (rueda/flechas/swipe/dots), FAQ overlay.
- **V9**: pivote de posicionamiento: de "prepárate para la entrevista" a "aprende a ser PO".
  Casos ágiles nuevos, programas, FAQ reescrito, guía de historias de usuario como lead magnet.
- **V10 (actual)**: 8 pantallas (suma Metodología detallada + Complementa), precios
  estudiantes ($40k/$100k/$180k), Agile Essentials $70k, botón "Feedback con IA",
  foto mentor embebida (edición propia), bug de Lenis (colisión de globales) resuelto con IIFE.

- **V11**: mejora integral. Hero sin desbordes (tamaño por alto de pantalla), fuentes con fallback condensado,
  navegación por nombre + #hash compartible (ej. frio.cl/#entrevistas), menú móvil, puntos de navegación sin solapes,
  scroll interno de pantallas largas (rueda/swipe/teclado ya no saltan de pantalla a mitad de lectura),
  espacio en textarea ya no navega, secciones responsivas (Metodología, Ecosistema), accesibilidad (foco, reduced-motion),
  OG/favicon, nueva pantalla «Entrevistas» (p5) y `source` en el formulario para medir de dónde viene cada lead.
  Pantalla Entrevistas con rúbrica propia (30/25/25/20 + regla de veto), caso de muestra de pagos (cifras sintéticas revisadas) y FAQ de grabación (borrado a los 30 días: PENDIENTE confirmación de Pedro).
  Bugs corregidos: «Ver packs» llevaba a Práctica; typos («papado», «practizar»).

## Decisiones vigentes
- No pasarela de pago: transferencia bancaria sola.
- No garantía de empleo; "no somos bolsa de trabajo" en FAQ y disclaimer.
- Marca Frio.cl (pendiente evaluar si renombrar al negocio de formación).
- Foto mentor: mejor edición honesta de selfie embebida; **retoma profesional pendiente**
  (receta: luz de ventana, fondo liso, celular a altura de ojos, mirada al lente).
- WhatsApp real PENDIENTE (placeholder 56912345678 en CONFIG).

## Infraestructura
- Repo: https://github.com/pedroalread/frio-cl (rama `develop` = trabajo, `main` = producción congelada).
- Preview de develop: https://htmlpreview.github.io/?https://github.com/pedroalread/frio-cl/blob/develop/index.html
- Vercel: pendiente hasta autorización de producción.

## Backlog (priorizado)
1. [[Quiz de nivel]] → recomendador de programa (idea: rutas de aprendizaje Atlassian).
2. [[Biblioteca de plantillas]] descargables (DoR/DoD, retros) — formato "biblioteca Reforge".
3. Bullets de resultado por programa (copy estilo Mountain Goat).
4. CONFIG.whatsapp con número real.
5. Endpoint IA para feedback automático.
6. Capa de agente IA (ver README: contrato de endpoints).
7. Clase pública mensual gratuita (marca + leads).

## Referentes robados
- Atlassian Agile Coach (rutas, tutoriales con tiempo, plantillas, agile+IA human-in-the-loop).
- Mountain Goat Software (copy orientado a resultados concretos).
- Reforge (biblioteca de ejemplos reales + guías prácticas).
- Scrum.org (entrenamiento interactivo sin slides).
- Maven / Product Faculty / Lenny's (cohortes, prueba social con cohorte, flywheel de contenido).
