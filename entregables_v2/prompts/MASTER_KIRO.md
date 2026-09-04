# MASTER PROMPT — ConcienTIC Web / Next.js / Vercel (v3, diff completo v5→v10)

Quiero que actualices el repositorio que actualmente despliega
`https://concientic.vercel.app/` para que coincida con el estado final descrito
en `kiro/specs/concientic-web-redesign.md` y con la referencia visual
`docs/concientic_v10_reference.html`.

## CONTEXTO
ConcienTIC es un ecosistema de Inteligencia Digital. La propuesta central es:
**"Aprender tecnología. Sin perder humanidad."**

DQUILIBRIO es la filosofía transversal: aumentar nuestra capacidad de elegir
cómo, cuándo, por qué y para qué usamos la tecnología. En piezas de marca, "DQ"
va en verde primario y el resto de la palabra en el color de contraste del
fondo (blanco sobre oscuro), conectando con la idea de Digital Quotient.

Los Guardianes de la Inteligencia Digital son el equipo virtual oficial de
ConcienTIC. Son agentes especializados, no mascotas decorativas.

## FUENTES DE VERDAD (en este orden)
1. `docs/Manual_de_Marca_ConcienTIC_v2_0.docx`
2. `docs/Sistema_de_Diseno_Web_ConcienTIC_v1_0.docx`
3. `kiro/specs/concientic-web-redesign.md` (v3 — diff completo desde el
   prototipo original v5 hasta el estado final v10: orden de secciones,
   logo, copy del Hero, ilustraciones, sección Equipo, tipografía del
   Manifiesto, interacción/hover y accesibilidad)
4. `.kiro/steering/*`
5. `docs/concientic_v10_reference.html` como referencia visual final (no como
   fuente arquitectónica — no copiar su HTML/CSS literalmente, reconstruir
   como componentes Next.js)
6. `reference-code/content/guardians.ts` y `reference-code/styles/design-tokens.css`

Si el repositorio ya tiene una implementación previa (de una iteración
anterior de este mismo proyecto), **no reconstruyas desde cero**: usa
`prompts/07_ACTUALIZACION_CAMBIOS.md`, que lista puntualmente qué cambió desde
la última versión. Reconstruye desde cero solo si el repositorio está vacío o
en estado de placeholders sin relación con ConcienTIC.

## ORDEN DE EJECUCIÓN (repo nuevo o placeholder)
1. Audita el repositorio y determina stack real (`prompts/00_AUDITORIA.md`).
2. Implementa base Next.js, tokens y componentes (`prompts/01_BASE_NEXTJS.md`,
   `prompts/02_DESIGN_SYSTEM.md`).
3. Implementa todas las secciones en el orden definitivo de
   `concientic-web-redesign.md` (`prompts/03_IMPLEMENTACION.md`).
4. Implementa Equipo/Guardianes con la estructura simplificada
   (`prompts/04_EQUIPO_GUARDIANES.md`).
5. QA visual, funcional, accesibilidad y performance
   (`prompts/05_QA_VERCEL.md`, `prompts/06_REVISION_VISUAL.md`).

## ORDEN DE SECCIONES DEFINITIVO
Header → Hero → Banda de principio → DQUILIBRIO → **Servicios** → El desafío →
Desinfoxicación → Metodología → Centro de Evidencia → Equipo → Casos →
Referentes → Manifiesto → Contacto → Footer.
(Servicios se movió: antes iba después de Desinfoxicación, ahora va
inmediatamente después de DQUILIBRIO.)

## PALETA OBLIGATORIA
Primario: #00C49A · Secundario: #6C63FF · Azul: #0077FF · Cian: #00B4D8 ·
Oscuro: #0D1B2A · Naranja: #FF7A00 · Amarillo: #FFC857 · Rosa: #FF6EB6 ·
Fondo suave: #F5F7F9 · Texto: #1E293B · Muted: #64748B.

## TIPOGRAFÍA
Poppins para títulos, marca y mensajes de alto impacto. Inter para UI y
lectura.

## LOGO
Wordmark "ConcienTIC Nexus" en dos variantes (`assets/concientic-nexus-wordmark-transparente-fondo-claro.png`
y `...-fondo-oscuro.png`) — elegir según el fondo de la sección donde se use.
Tamaño legible en el header (mínimo ~52-58px de alto en desktop, debe leerse
"NEXUS" y el tagline). El isotipo `logo-concientic.png` queda solo para
favicon.

## ILUSTRACIONES DQUILIBRIO
Usar tal cual, como imágenes estáticas vía `next/image` (no reconstruir en
SVG/CSS):
- `assets/diagrams/equilibrio-concientic-mejorado.png` → visual del Hero.
- `assets/diagrams/ciclo-dquilibrio-mejorado.png` → diagrama de Metodología.

## EQUIPO / GUARDIANES
Ver reglas completas en `concientic-web-redesign.md` y
`prompts/04_EQUIPO_GUARDIANES.md`. En resumen: una sola sección de fondo
oscuro, un solo encabezado, sin las cajas de estadística, tarjeta de cita
dentro de la grilla de 4 columnas (8vo elemento, texto grande), sin la línea
"Agente virtual · Equipo ConcienTIC" en las tarjetas.

## INTERACCIÓN Y ACCESIBILIDAD
Ver detalle completo en `concientic-web-redesign.md` (§7 y §8). En resumen:
botones con relleno deslizante al hover/focus, enlaces con subrayado
animado, tarjetas con elevación al hover (más notoria en las de Guardián),
todo desactivado bajo `prefers-reduced-motion`; skip link inicial,
`:focus-visible` global, y formulario de contacto con mensaje de estado
accesible (`aria-live`) en vez de `alert()`.

## DISEÑO CONSCIENTE
No agregar: infinite scroll, autoplay, FOMO, streaks, rankings, contadores de
permanencia, dark patterns, urgencia artificial, popups innecesarios. La
navegación debe ser clara y fácil de abandonar.

## CONTENIDO
No inventes clientes, métricas, testimonios ni resultados. Si falta
información real, usa un bloque interno marcado como TODO o contenido neutro
no engañoso. No presentar DQUILIBRIO como escala clínica validada. No utilizar
"dopamina" como explicación científica simplista.

## SEO Y ACCESIBILIDAD
Metadata, Open Graph, headings semánticos, alt text, keyboard navigation,
focus visible, contraste AA y reduced motion.

## VERCEL
La aplicación debe funcionar con el comando de build definido por el proyecto.
No almacenar secretos. Crear `.env.example` si se requiere configuración
externa.

## ENTREGA
Al finalizar:
1. Resume arquitectura final y qué cambió respecto a la versión anterior del
   repo (si aplicaba `prompts/07_ACTUALIZACION_CAMBIOS.md`).
2. Enumera archivos creados/modificados.
3. Reporta lint/typecheck/build.
4. Reporta cualquier limitación.
5. Indica exactamente qué falta para el deploy final en Vercel, si falta algo.
