# AGENTS.md — ConcienTIC

## Prioridad
Construye el sitio respetando en este orden:
1. Manual de Marca ConcienTIC v2.0.
2. Sistema de Diseño Web ConcienTIC v1.0.
3. `kiro/specs/concientic-web-redesign.md` (v4 — diff completo v5→v11, incluye subpáginas).
4. Este archivo y los steering files de `.kiro/steering/`.
5. `docs/concientic_v11_reference.html` como referencia visual, no como
   fuente arquitectónica.

## Identidad
- Primario principal: #00C49A.
- Secundario principal: #6C63FF.
- Azul tecnológico: #0077FF.
- Cian futuro: #00B4D8.
- Oscuro digital: #0D1B2A.
- Naranja innovación: #FF7A00.
- Amarillo: #FFC857.
- Rosa: #FF6EB6.
- Fondo claro: #F5F7F9.
- Tipografía de marca/títulos: Poppins.
- Tipografía UI/lectura: Inter.

## Logo (actualizado)
Wordmark "ConcienTIC Nexus", sin el ícono de árbol, en dos variantes:
`concientic-nexus-wordmark-transparente-fondo-claro.png` (fondos claros) y
`concientic-nexus-wordmark-transparente-fondo-oscuro.png` (fondos oscuros).
Debe verse a un tamaño legible (se debe distinguir "NEXUS" y el tagline). El
isotipo `logo-concientic.png` (árbol/cerebro) queda solo para favicon.

## Guardianes
Los Guardianes de la Inteligencia Digital son el equipo virtual de
ConcienTIC. No tratarlos como mascotas decorativas.
- Emi — Empatía Digital.
- Locky — Seguridad Digital.
- Lex — Pensamiento Crítico.
- Byte — Alfabetización Digital.
- Detective DQ — Discernimiento Digital.
- Nexo — Conexión Digital.
- Nova — Innovación Digital.

La sección Equipo es un único bloque de fondo oscuro (no dos secciones con
distinto tono), sin la línea "Agente virtual · Equipo ConcienTIC" en las
tarjetas, con una tarjeta de cita de texto grande como 8vo elemento del grid.
Ver `kiro/specs/concientic-web-redesign.md` para el detalle completo.

## Interacción y accesibilidad
Botones, enlaces y tarjetas deben tener los estados de hover/focus definidos
en `kiro/steering/design-system.md` (relleno deslizante en botones, subrayado
animado en enlaces, elevación en tarjetas), siempre desactivados bajo
`prefers-reduced-motion`. El sitio debe incluir skip link inicial y
`:focus-visible` global. El formulario de contacto nunca debe simular un
envío exitoso (usar mensaje de estado con `aria-live`, no `alert()`).

## UX consciente
- Sin infinite scroll.
- Sin autoplay.
- Sin dark patterns.
- Sin FOMO.
- Sin streaks o recompensas de permanencia.
- Sin urgencia artificial.
- Animación sobria y respetuosa de `prefers-reduced-motion`.
- Navegación evidente y salidas claras.
- El CTA informa y facilita la decisión; no manipula.

## Implementación
- TypeScript estricto.
- Componentes reutilizables.
- Contenido separado de presentación cuando sea razonable.
- Imágenes locales optimizadas con `next/image`, incluidas las dos
  ilustraciones DQUILIBRIO de `public/diagrams/` (usarlas tal cual, no
  reconstruirlas en SVG/CSS).
- No incrustar imágenes en base64 en producción.
- No sustituir assets de marca por aproximaciones generadas.
- No inventar casos, métricas, clientes, testimonios o nombres humanos.
- Validar responsive, accesibilidad, SEO y performance antes de entregar.
