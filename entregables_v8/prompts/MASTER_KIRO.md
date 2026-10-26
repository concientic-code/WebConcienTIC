# MASTER PROMPT — ConcienTIC Web / Next.js / Vercel (v7, rediseño completo de la página principal)

Quiero que actualices el repositorio que actualmente despliega
`https://www.concientic.com/` (dominio de producción confirmado — ver spec
§14.6) para que coincida con el estado final descrito en
`kiro/specs/concientic-web-redesign.md` y con la referencia visual
`docs/concientic_v13_reference.html` (página principal — reemplaza a
`docs/concientic_v12_reference.html`). Las subpáginas de DQUILIBRIO y de
Servicios siguen igual, solo cambia desde dónde se enlazan en la home.

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
3. `kiro/specs/concientic-web-redesign.md` (v7 — §1-§13 documentan el diff
   v5→v12; §14 documenta el rediseño completo v12→v13, que es el estado
   vigente de la página principal)
4. `.kiro/steering/*`
5. `docs/concientic_v13_reference.html` como referencia visual vigente de la
   página principal (no como fuente arquitectónica — no copiar su HTML/CSS
   literalmente, reconstruir como componentes Next.js). `docs/concientic_v12_reference.html`
   se conserva solo como referencia histórica.
6. `reference-code/content/guardians.ts` y `reference-code/styles/design-tokens.css`

Si el repositorio ya tiene una implementación previa (de una iteración
anterior de este mismo proyecto), **no reconstruyas desde cero**:
- Si está en el estado v5 original o en cualquier punto intermedio hasta
  v12, usa primero `prompts/07_ACTUALIZACION_CAMBIOS.md`,
  `prompts/08_SUBPAGINAS_DQUILIBRIO.md` y `prompts/09_SERVICIOS_SUBPAGINAS.md`
  según corresponda, y luego `prompts/10_REDISENIO_HOME_V13.md`.
- Si ya está en v12, aplica directamente `prompts/10_REDISENIO_HOME_V13.md`.

Reconstruye desde cero solo si el repositorio está vacío o en estado de
placeholders sin relación con ConcienTIC — en ese caso implementa
directamente el estado v13 (no v12, que queda superado) siguiendo
`prompts/03_IMPLEMENTACION.md` como base de componentes/Design System y
`kiro/specs/concientic-web-redesign.md` §14 para el contenido real de la
página principal.

## ORDEN DE EJECUCIÓN (repo nuevo o placeholder)
1. Audita el repositorio y determina stack real (`prompts/00_AUDITORIA.md`).
2. Implementa base Next.js, tokens y componentes (`prompts/01_BASE_NEXTJS.md`,
   `prompts/02_DESIGN_SYSTEM.md`).
3. Implementa las secciones de la página principal en el orden vigente de
   §14.1 del spec (Hero, Ecosistema, Guardianes, Recursos, Metodología,
   Experiencia, DQUILIBRIO, Contacto) — usa `prompts/03_IMPLEMENTACION.md`
   solo como referencia de patrones de componente/Design System, no para el
   orden de secciones de v12 que ya no aplica.
4. Implementa la franja única de Guardianes (`prompts/10_REDISENIO_HOME_V13.md`,
   punto F) — ya no es la grilla de 7 tarjetas con bio de
   `prompts/04_EQUIPO_GUARDIANES.md` (ese prompt queda como referencia
   histórica, útil solo si Jeimy confirma mantener esa versión en otra página).
5. Implementa las subpáginas DQUILIBRIO como assets estáticos enlazados
   (`prompts/08_SUBPAGINAS_DQUILIBRIO.md`).
6. Implementa la subpágina "Contenidos", enlazada ahora desde la sección
   Recursos (`prompts/09_SERVICIOS_SUBPAGINAS.md` + `prompts/10_REDISENIO_HOME_V13.md`
   punto G).
7. QA visual, funcional, accesibilidad y performance
   (`prompts/05_QA_VERCEL.md`, `prompts/06_REVISION_VISUAL.md`), incluyendo
   las preguntas abiertas listadas al final de `prompts/10_REDISENIO_HOME_V13.md`.

## ORDEN DE SECCIONES DEFINITIVO (vigente — página principal, v13)
Header → Hero → Ecosistema → Guardianes → Aprende/Recursos → Metodología →
Experiencia → DQUILIBRIO → Contacto → Footer.

El orden anterior (v12: Header → Hero → Banda de principio → DQUILIBRIO →
Servicios → El desafío → Desinfoxicación → Metodología → Centro de
Evidencia → Equipo → Casos → Referentes → Manifiesto → Contacto → Footer)
queda **superado** — ver spec §14.1 para el detalle de qué secciones se
eliminan y cuáles quedan pendientes de confirmación con Jeimy antes de
borrar su contenido definitivamente.

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

## EQUIPO / GUARDIANES (vigente en la página principal: franja única, no la grilla de 7 tarjetas)
Desde v13, la página principal muestra una sola franja "Guardianes" (imagen
de grupo + 7 competencias + cierre) — ver spec §14.5 y
`prompts/10_REDISENIO_HOME_V13.md` punto F. La grilla de 7 tarjetas con
foto/rol/bio individual que describen `concientic-web-redesign.md` (§5) y
`prompts/04_EQUIPO_GUARDIANES.md` queda como referencia histórica, útil solo
si Jeimy confirma que esa versión debe conservarse en otra página (p. ej.
una futura `/equipo`).

## SUBPÁGINAS DQUILIBRIO
Ver reglas completas en `concientic-web-redesign.md` (§10) y
`prompts/08_SUBPAGINAS_DQUILIBRIO.md`. En resumen: las 4 tarjetas de la
sección DQUILIBRIO son enlaces (`target="_blank"`) a 4 experiencias ya
diseñadas (`assets/dquilibrio-subpaginas/*.html`) que se copian tal cual a
`public/dquilibrio/`, sin reescribirlas ni "mejorarlas". Desde v13 estos
enlaces se construyen con el dominio absoluto
`https://www.concientic.com/dquilibrio/*.html` (antes, rutas relativas).

## SERVICIOS/RECURSOS — SUBPÁGINA "CONTENIDOS" (ya no hay bloque de 5 tarjetas con estados en la home)
Ver reglas completas en `concientic-web-redesign.md` (§11, §14.6) y
`prompts/09_SERVICIOS_SUBPAGINAS.md` + `prompts/10_REDISENIO_HOME_V13.md`
punto G. El bloque original de 5 tarjetas de Servicios (con los estados
"enlace", "ancla", "en construcción" y "sin cambios") **ya no existe en la
página principal** desde v13 — queda como referencia histórica. Lo único
que sigue vigente de ese bloque es el enlace a la subpágina "Contenidos"
(`assets/servicios-subpaginas/contenidos.html` → `public/servicios/`), que
ahora vive dentro de la nueva sección "Aprende/Recursos" y se enlaza con el
dominio absoluto `https://www.concientic.com/servicios/contenidos`. La
subpágina "Laboratorios" (pendiente de entrega) ya no tiene una tarjeta
dedicada en la home; su futuro enlace deberá decidirse cuando Jeimy entregue
esa subpágina.

## REDISEÑO COMPLETO DE LA PÁGINA PRINCIPAL (v13 — NUEVO, vigente)
Ver reglas completas en `concientic-web-redesign.md` (§14) y
`prompts/10_REDISENIO_HOME_V13.md`. Resumen: nueva arquitectura de 8
secciones (Hero, Ecosistema, Guardianes, Recursos, Metodología, Experiencia,
DQUILIBRIO, Contacto), varias secciones de v12 eliminadas pendientes de
confirmación de destino, dominio de producción confirmado
`concientic.com`, y un conjunto de desviaciones de marca en el archivo de
referencia (paleta y tipografía) que deben implementarse con los valores
OFICIALES del Manual de Marca hasta que Jeimy confirme lo contrario.

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

## SUBPÁGINA "LABORATORIOS IA" Y NUEVA REGLA DE MENÚ PARA SUBPÁGINAS (NUEVO)
Ver reglas completas en `concientic-web-redesign.md` (§16) y
`prompts/11_LABORATORIOS_SUBPAGINA.md`. Resumen: nueva subpágina estática
con 4 laboratorios (SIGINEX, EmprendeCreativo, DQ-Nexus, TutorIA), publicada
tal cual desde `assets/ecosistema-subpaginas/laboratoriosia.html` a
`public/ecosistema/laboratoriosia.html`. La tarjeta "Laboratorios IA" de la
sección Ecosistema de la home debe enlazar a esta subpágina en pestaña
nueva en vez de a `#contacto`. **Regla transversal nueva**: todas las
subpáginas deben usar el mismo menú de la página central, no uno propio —
ya aplicada en esta subpágina; las 5 subpáginas anteriores (DQUILIBRIO ×4 y
"Contenidos") no se tocan todavía, pendiente de confirmación de Jeimy.

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
