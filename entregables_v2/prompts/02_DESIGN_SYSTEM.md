# Prompt 02 — Implementar Design System

Implementa el Sistema de Diseño Web ConcienTIC v1.0 como una capa reusable.

Usa:
- Primario: #00C49A. Secundario: #6C63FF. Azul: #0077FF. Cian: #00B4D8.
- Oscuro: #0D1B2A. Naranja: #FF7A00. Amarillo: #FFC857. Rosa: #FF6EB6.
- Fondo suave: #F5F7F9. Texto: #1E293B. Muted: #64748B.
- Poppins para títulos/marca. Inter para UI/lectura.

Construye tokens para color, tipografía, spacing, radius, shadow, container
widths y breakpoints.

Construye componentes reutilizables para: Button, Badge/Eyebrow,
SectionHeader, Card, Navigation, Footer, EvidenceCard, GuardianCard,
**QuoteCard** (nuevo — tarjeta de cita para la sección Equipo, con tipografía
más grande que el texto descriptivo de las tarjetas de Guardián) y **Logo**
(nuevo — componente que resuelve entre la variante clara y oscura del
wordmark "ConcienTIC Nexus" según el fondo de la sección; ver
`.kiro/steering/design-system.md` para los nombres de archivo exactos).

El sistema debe favorecer calma y legibilidad. No agregar patrones de
retención.

Implementa los patrones de interacción definidos en
`.kiro/steering/design-system.md` (sección Movimiento): relleno deslizante en
botones al hover/focus, subrayado animado en enlaces de texto, elevación
suave en tarjetas al hover, y elevación/intensificación de borde en tarjetas
de Guardián. Todos deben desactivarse bajo `prefers-reduced-motion`.

Agrega también los elementos de accesibilidad descritos en esa misma sección:
skip link al inicio del `<body>`, `:focus-visible` global, y mensaje de
estado accesible (no `alert()`) para el formulario de contacto.

Valida contraste, focus states, teclado y reduced motion.
