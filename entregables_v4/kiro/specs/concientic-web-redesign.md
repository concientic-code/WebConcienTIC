# Spec — Rediseño web ConcienTIC (v4, incluye subpáginas DQUILIBRIO)

> Reemplaza las versiones anteriores de este spec. `docs/concientic_v11_reference.html`
> es el prototipo visual aprobado y vigente. Este documento describe **todo**
> lo que cambió respecto al prototipo original `concientic_v5_reference.html`
> (la referencia usada la primera vez que se construyó el sitio), no solo el
> último ajuste — así Kiro puede actualizar el sitio en producción sin
> importar en qué punto de esa evolución se haya quedado el repositorio
> desplegado.

## Objetivo
Actualizar `https://concientic.vercel.app/` para que coincida exactamente con
`docs/concientic_v11_reference.html`, implementado como Next.js mantenible,
tipado y desplegable en Vercel.

---

## 1. Orden de secciones (definitivo)
1. Header (logo + navegación)
2. Hero — id `inicio`
3. Banda de principio ("No queremos más tiempo de tu vida...")
4. DQUILIBRIO — id `dquilibrio`
5. **Servicios — id `servicios`** ⚠️ En el prototipo v5 original iba después de
   Desinfoxicación. Ahora va inmediatamente después de DQUILIBRIO.
6. El desafío — id `desafio`
7. Desinfoxicación — id `desinfoxicacion`
8. Metodología — id `metodologia`
9. Centro de Evidencia — id `evidencia`
10. Equipo / Guardianes — id `equipo` (estructura muy distinta a v5, ver §5)
11. Casos — id `casos`
12. Referentes — id `referentes`
13. Manifiesto (sin id de ancla)
14. Contacto — id `contacto`
15. Footer

La navegación (header y footer) debe listar los enlaces en este mismo orden.

---

## 2. Logo — reemplazo completo
En v5 el logo era el isotipo original (árbol/cerebro) embebido como imagen
en el header, acompañado del texto "concienTIC" generado con HTML/CSS (no era
una imagen de wordmark).

Cambio: reemplazar por el nuevo wordmark "ConcienTIC Nexus" (sin el ícono de
árbol), como imagen, en header **y** footer. Hay dos variantes en `assets/`:
- `concientic-nexus-wordmark-transparente-fondo-claro.png` → fondos claros
  (header, footer, cualquier sección con `--surface`/`--soft`/blanco).
- `concientic-nexus-wordmark-transparente-fondo-oscuro.png` → fondos oscuros
  (`--dark`, sección Equipo, banda, manifiesto), si en el futuro se agrega el
  logo a alguna de esas secciones.
- `logo-concientic.png` (el árbol/cerebro original) se conserva solo como
  isotipo para favicon.

Tamaño: el wordmark debe verse a un tamaño generoso — el texto "NEXUS" y el
tagline "Conciencia Digital para un mundo mejor." deben ser legibles. Tamaño
final acordado: **58px de alto en el header, 38px en el footer** (en un
primer ajuste se probó a 42px/30px y resultó ilegible; no bajar de 52-58px en
el header).

---

## 3. Hero — copy y visual
### Copy
- H1 (sin cambios): "Aprender tecnología. Sin perder humanidad."
- Párrafo lead — **cambió**. Texto anterior (v5):
  "ConcienTIC desarrolla competencias digitales e inteligencia artificial
  mientras ayuda a personas y organizaciones a construir una relación
  consciente, autónoma y equilibrada con la tecnología."
  Texto final (usar este, textual):
  "ConcienTIC desarrolla Inteligencia Digital mientras ayuda a personas y
  organizaciones a construir una relación consciente, autónoma y equilibrada
  con la tecnología."

### Visual
En v5 el visual del Hero era una composición hecha a mano en CSS: una caja
con borde redondeado y dos anillos concéntricos decorativos
(pseudo-elementos `::before`/`::after`), un círculo oscuro central
("DQUILIBRIO / tecnología con conciencia") y 5 píldoras flotantes
posicionadas absolutamente (ATENCIÓN, IA + TECH, CRITERIO, AUTONOMÍA,
HUMANIDAD).

Cambio: reemplazar toda esa composición por una sola imagen estática ya
diseñada: `assets/diagrams/equilibrio-concientic-mejorado.png`. Esta imagen
ya resuelve el mismo concepto (los 5 elementos alrededor de un centro
DQUILIBRIO) pero con sombras suaves, relleno tintado por color y el centro
con "DQ" en verde primario + "UILIBRIO" en blanco. No reconstruir en CSS/SVG.
Mostrar a un tamaño más grande que el original: ancho máximo ≈600px en
desktop (el contenedor CSS original limitaba a ~460-510px).

---

## 4. Metodología — diagrama
En v5 el diagrama era un `<svg>` dibujado a mano: círculo guía, 5 arcos de
colores con marcadores de flecha, 5 círculos numerados (01-05) con su
etiqueta, y un círculo central con "DQUILIBRIO" y "volver a elegir".

Cambio: reemplazar el `<svg>` completo por la imagen estática
`assets/diagrams/ciclo-dquilibrio-mejorado.png`, que resuelve el mismo
concepto (mismo orden y colores de etapas) con sombras suaves, relleno
tintado por nodo y el centro con "DQ" en verde y "UILIBRIO" en blanco. No
reconstruir en SVG.

---

## 5. Equipo / Guardianes — reestructuración completa
En v5 esta área eran **dos secciones separadas**:
- `.team-hero`: fondo `--dark`, con kicker "Nuestro equipo" + H2 "Guardianes
  de la Inteligencia Digital" + párrafo, y dos cajas de estadística ("7
  agentes. 7 capacidades especializadas que se complementan." / "1
  inteligencia colectiva. Todos forman parte de ConcienTIC...").
- `.guardians`: fondo casi negro (`#050A12`, más oscuro que `--dark`), con un
  **segundo** encabezado ("Equipo virtual" / "Conoce a los Guardianes" +
  párrafo "No son mascotas decorativas..."), la grilla de 7 tarjetas, y el
  cierre "Juntos construyen una inteligencia digital consciente, crítica,
  creativa, colaborativa y transformadora." completo en un solo color verde
  (`<strong>` con `color:var(--primary)`).

Cambios (todos aplican, no son alternativas):
1. **Unificar en una sola sección**, fondo `--dark` de principio a fin. No
   usar el tono casi negro (`#050A12`) en ninguna parte.
2. **Un solo encabezado** (el de `.team-hero`: "Nuestro equipo" / "Guardianes
   de la Inteligencia Digital" / párrafo). Eliminar el segundo encabezado
   "Equipo virtual / Conoce a los Guardianes" por completo.
3. **Eliminar las dos cajas de estadística** ("7 agentes" / "1 inteligencia
   colectiva").
4. **Eliminar la línea "Agente virtual · Equipo ConcienTIC"** que aparecía al
   pie de cada una de las 7 tarjetas de Guardián.
5. **Agregar una tarjeta de cita** como 8º elemento de la grilla de 4
   columnas (junto a las 7 tarjetas de Guardián — la grilla sigue siendo de 4
   columnas, ahora con 8 elementos en vez de 7), con el texto: "Cada guardián
   tiene un territorio de competencia y una función real dentro de las
   experiencias del Ecosistema ConcienTIC." Esta tarjeta no lleva imagen;
   solo texto centrado sobre un fondo apenas más claro que `--dark`, con
   borde sutil. El tamaño de fuente debe ser notoriamente mayor que el texto
   descriptivo de las tarjetas de Guardián (no debe leerse como texto
   secundario/pequeño) — tamaño final acordado ≈1.2rem, peso medio.
6. **Colorear el cierre de sección por palabra**: "Juntos construyen una
   inteligencia digital **consciente** (púrpura `#6C63FF`), **crítica** (cian
   `#00B4D8`), **creativa** (verde `#00C49A`), **colaborativa** (rosa
   `#FF6EB6`) y **transformadora** (naranja `#FF7A00`)." en vez de la frase
   completa en un solo color.

Las 7 tarjetas de Guardián en sí (imagen, nombre, rol, competencia,
descripción, color territorial) no cambiaron de contenido — ver
`content.md` para el texto exacto de cada una.

---

## 6. Manifiesto — ajuste tipográfico
En v5 el titular "Si una experiencia necesita robarte atención para
funcionar, debemos rediseñarla." usaba el mismo tamaño global de H2 que el
resto del sitio (`clamp(2.3rem, 4.8vw, 4.2rem)`), lo que hacía que la columna
izquierda (kicker + titular + párrafo) dominara visualmente la sección frente
a la grilla de 6 recuadros de principios de la derecha.

Cambio: reducir el tamaño de **este H2 específico** a
`clamp(1.5rem, 2.3vw, 2.05rem)` (line-height 1.32, letter-spacing -.02em),
de modo que ambas columnas ocupen un espacio visual comparable. No cambiar el
tamaño de H2 en ninguna otra sección del sitio.

---

## 7. Interacción y microanimaciones (nuevo respecto a v5)
v5 prácticamente no tenía estados de hover (solo un color de hover en los
enlaces de navegación) ni transiciones. Se agregaron los siguientes patrones,
inspirados en el lenguaje visual de humanetech.com, y deben implementarse:

- **Botones** (`.btn-primary`, `.btn-secondary`): al pasar el mouse o
  enfocar con teclado, un relleno oscuro (`--dark`) se desliza desde la
  izquierda cubriendo todo el botón (`transform: scaleX(0)→scaleX(1)`,
  `transform-origin: left`), y el texto cambia a blanco. Los botones en v5
  eran planos, sin ningún estado de interacción.
- **Enlaces de texto** (tarjetas de Referentes, tarjetas de Evidencia,
  enlaces del footer, enlaces de navegación): subrayado animado que crece de
  0% a 100% de ancho al pasar el mouse o enfocar (`background-size`
  transition sobre un `linear-gradient` de 1px de alto).
- **Tarjetas** (`.card`, `.service`, `.evidence-card`, `.reference`, `.case`,
  `.principle`): al pasar el mouse se elevan levemente
  (`translateY(-3px)` a `-4px`) y la sombra se intensifica. Ninguna tenía
  hover en v5.
- **Tarjetas de Guardián**: al pasar el mouse se elevan de forma más notoria
  (`translateY(-6px)`), el borde se intensifica hacia el color territorial
  completo, y el resplandor radial detrás del personaje se intensifica.
- Todo lo anterior es "hover discreto" / "transición de estado" (permitido
  por el Sistema de Diseño); no se agregó animación automática, parallax,
  auto-scroll ni loops — eso sigue prohibido.
- Todas las transiciones y animaciones deben desactivarse por completo bajo
  `prefers-reduced-motion: reduce`.

**Nota de limpieza técnica**: si el repositorio actual todavía tiene el
diagrama de Metodología en SVG o el visual del Hero en CSS (ver §3 y §4),
también van a existir reglas CSS asociadas (`.core`, `.node`, `.n1`-`.n5`,
`.cycle-node-g`, `.cycle circle.node`) que quedan obsoletas al reemplazar
esos elementos por imágenes estáticas. Elimínalas junto con el HTML que
reemplazas, no las dejes como código muerto.

---

## 8. Accesibilidad (nuevo respecto a v5)
v5 no tenía ninguno de estos elementos; se agregaron y deben conservarse:
- **Skip link**: enlace "Saltar al contenido" al inicio del `<body>`,
  visualmente oculto salvo cuando recibe foco de teclado, que salta a
  `#main`.
- **`:focus-visible`** con contorno visible (azul `--blue`, 2px, offset 3px)
  aplicado globalmente, no solo el estado `:hover` por defecto del navegador.
- **Formulario de contacto**: v5 usaba un `onsubmit` con `alert()` del
  navegador (bloqueante) para simular el envío. Cambiar a un mensaje de
  estado no bloqueante dentro de la página, con `role="status"` y
  `aria-live="polite"`, que informe: "Maqueta de demostración: conecta este
  formulario a un servicio real (por ejemplo, Resend) antes de producción."
  — nunca simular un envío exitoso real.
- Mantener landmarks semánticos (`<main id="main">`, `<nav aria-label="...">`,
  `alt` en todas las imágenes, incluidas las dos ilustraciones de diagramas).

---

## 9. Assets
Copiar todo `assets/` a `public/` así:
- `assets/*.png` (guardianes + `logo-concientic.png`) → `public/guardians/` y
  `public/brand/` según corresponda (ver `structure.md`).
- `assets/concientic-nexus-wordmark-*.png` → `public/brand/`.
- `assets/diagrams/*.png` → `public/diagrams/`.

Usar `next/image` para todos. Conservar transparencia. No usar base64 en
producción bajo ninguna circunstancia.

---

## 10. Subpáginas DQUILIBRIO (nuevo)
Las 4 tarjetas de la sección DQUILIBRIO (§1, id `dquilibrio`) dejan de ser
solo texto: cada una es ahora un enlace clicable que abre una experiencia
propia, ya diseñada y entregada como HTML autocontenido:

| Tarjeta | Archivo | Ruta pública |
|---|---|---|
| 01 · Atención — Recuperar presencia | `assets/dquilibrio-subpaginas/atencion.html` | `/dquilibrio/atencion.html` |
| 02 · Información — Reducir saturación | `assets/dquilibrio-subpaginas/informacion.html` | `/dquilibrio/informacion.html` |
| 03 · Criterio — Decidir con criterio | `assets/dquilibrio-subpaginas/discernimiento.html` | `/dquilibrio/discernimiento.html` |
| 04 · Autonomía — Elegir conscientemente | `assets/dquilibrio-subpaginas/autonomia.html` | `/dquilibrio/autonomia.html` |

### Regla de fidelidad — no tocar el contenido de las 4 subpáginas
Cada archivo es un diseño ya aprobado, autocontenido (HTML+CSS+JS embebidos,
imágenes en base64), con su propia experiencia interactiva (temporizador,
curador de información, verificador de afirmaciones, diseñador de decisión)
y su propia pareja de Guardianes. **Cóncielos como assets estáticos y
despliégalos byte a byte, sin reescribirlos como componentes React ni
"mejorarlos"**: cópialos tal cual a `public/dquilibrio/` con esos nombres de
archivo. Cualquier ajuste de contenido, color o estructura a estas 4 páginas
requiere confirmación explícita antes de aplicarse — no asumir cambios.

**Nota conocida, no corregir sin confirmación**: las 4 subpáginas usan el
isotipo original (árbol/cerebro) en su propio header, no el wordmark
"ConcienTIC Nexus" ya vigente en el resto del sitio (§2). Es una
inconsistencia real, señalada, pero no se corrige en esta iteración.

### Mecanismo de apertura y regreso
Las 4 tarjetas de `#dquilibrio` son `<a>` (no `<article>`) con
`target="_blank" rel="noopener noreferrer"`, apuntando a las rutas de la
tabla de arriba. Esto es lo que resuelve "abrir en otra ventana": la pestaña
original del sitio permanece abierta detrás, así que el regreso es
simplemente cambiar de pestaña o cerrar la nueva. **No se agrega ningún
elemento de "volver" dentro de las 4 subpáginas** — no se modifica su
contenido (ver regla de fidelidad arriba).

Cada tarjeta-enlace conserva el estilo visual `.card` existente (mismo
fondo, borde, padding, hover de elevación) y agrega, solo al pasar el mouse
o enfocar con teclado, un texto discreto "Abrir →" en la esquina inferior
derecha (color `--primary`) como afordance de que ahora es clicable —
consistente con el patrón "Visitar referente ↗" que ya existe en la sección
Referentes. Se agrega `aria-label` descriptivo en cada enlace para lectores
de pantalla, indicando que abre en una pestaña nueva.

---

## 11. Criterios de aceptación
- `npm run build` exitoso, sin errores de TypeScript ni lint.
- El orden de secciones y del menú coincide exactamente con §1.
- El logo es el wordmark completo "ConcienTIC Nexus" (no el isotipo solo), en
  la variante correcta según el fondo, legible a ≥52-58px de alto en el
  header.
- El visual del Hero y el diagrama de Metodología son las imágenes finales de
  `assets/diagrams/` (no CSS/SVG reconstruido).
- La sección Equipo es una sola sección de fondo oscuro uniforme, sin las dos
  cajas de estadística, sin el segundo encabezado, con la tarjeta de cita
  dentro de la grilla de 8 elementos, y sin la línea "Agente virtual · Equipo
  ConcienTIC".
- El titular del Manifiesto no domina visualmente la sección frente a la
  grilla de principios.
- Botones, enlaces y tarjetas tienen los estados de hover descritos en §7;
  todos respetan `prefers-reduced-motion`.
- Existe skip link, `:focus-visible` global, y el formulario de contacto usa
  un mensaje de estado accesible en vez de `alert()`.
- Responsive en 360, 768, 1024 y 1440 px.
- No placeholders visibles salvo casos reales aún no disponibles (sección
  Casos), claramente marcados.
- Vercel deployment sin configuración innecesaria.
- Las 4 tarjetas de DQUILIBRIO son enlaces funcionales que abren
  `/dquilibrio/{atencion,informacion,discernimiento,autonomia}.html` en una
  pestaña nueva (`target="_blank"`), y las 4 subpáginas están desplegadas sin
  alterar su contenido, estilo ni comportamiento originales.
