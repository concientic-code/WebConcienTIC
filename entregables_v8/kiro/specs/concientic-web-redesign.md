# Spec — Rediseño web ConcienTIC (v7, rediseño completo de la página principal)

> Reemplaza las versiones anteriores de este spec. **`docs/concientic_v13_reference.html`
> es ahora el prototipo visual vigente de la página principal** y sustituye a
> `docs/concientic_v12_reference.html` como objetivo a implementar. Las
> secciones §1-§13 de este documento describen la evolución v5→v12 (historia
> completa, no se borra, útil si el repo de Kiro quedó en un punto
> intermedio de esa evolución). **La §14 documenta el rediseño v12→v13, que
> es una reestructuración completa de la arquitectura de información de la
> página principal, no un ajuste incremental** — varias secciones de v12 se
> eliminan y la navegación cambia por completo. Para un repo que ya está en
> v12, aplicar §14 lleva al estado vigente; para un repo en cualquier punto
> anterior, aplicar primero las secciones previas y luego §14.

## Objetivo
Actualizar `https://www.concientic.com/` (dominio de producción confirmado;
ver nota en §14.6) para que coincida exactamente con
`docs/concientic_v13_reference.html`, implementado como Next.js mantenible,
tipado y desplegable en Vercel. Las subpáginas de DQUILIBRIO y de Servicios
(§10-§12) siguen vigentes sin cambios en su propio contenido.

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

## 11. Subpáginas de Servicios (nuevo)
La sección Servicios (§1, id `servicios`) tiene 5 tarjetas (`.service`).
Cambian de comportamiento así:

| # | Tarjeta | Comportamiento nuevo | Archivo / destino |
|---|---|---|---|
| 1 | Competencias Digitales | Enlace, abre en pestaña nueva | `assets/servicios-subpaginas/contenidos.html` → `/servicios/contenidos.html` |
| 2 | IA consciente | **Sin cambios por ahora** — sigue como tarjeta de texto plano, sin enlace. Tendrá una subpágina llamada "Laboratorios" cuando se entregue su HTML; hasta entonces no se toca ni se marca como "en construcción" (a diferencia de las tarjetas 3 y 4, esta sí es un desarrollo activo, no pausado). | — |
| 3 | Desinfoxicación | Deshabilitada: gris, sin hover, sin clic, etiqueta "En construcción" | — |
| 4 | Transformación cultural | Deshabilitada, igual que la 3 | — |
| 5 | DQUILIBRIO | Enlace ancla a `#dquilibrio` (misma página, no abre pestaña nueva) | — |

### Regla de fidelidad (igual que con las subpáginas DQUILIBRIO)
`assets/servicios-subpaginas/contenidos.html` es un diseño ya aprobado y
autocontenido (catálogo filtrable de recursos gratuitos por categoría,
buscador, sección "Academia ConcienTIC" marcada como "Próximamente", cierre
con el ciclo DQUILIBRIO). Cópialo tal cual a `public/servicios/` con ese
nombre de archivo. No lo reescribas como componente React ni le cambies
nada — cualquier ajuste requiere confirmación explícita.

**Nota**: el header de esta subpágina ya enlaza correctamente a
`https://www.concientic.com/` y a las anclas reales del sitio
(`#dquilibrio`, `#servicios`, `#metodologia`, `#equipo`) — a diferencia de
las subpáginas DQUILIBRIO, esta sí trae su propio mecanismo de regreso
funcional. Usa el dominio `concientic.com`, no `concientic.vercel.app`;
verificar cuál es el dominio de producción real antes de publicar (ver
también la nota equivalente en el spec original sobre este mismo punto).

### Tarjetas deshabilitadas (Desinfoxicación, Transformación cultural)
Se marcan visualmente como no disponibles, sin inventar ninguna subpágina
para ellas:
- Fondo gris (`#F1F3F5`), borde discontinuo, sin elevación ni sombra al
  pasar el mouse, cursor `not-allowed`.
- Etiqueta "En construcción" (fondo `--muted`, texto blanco, píldora) antes
  del título.
- `aria-disabled="true"` en el elemento; siguen siendo `<article>`, no
  `<a>` — no deben ser enfocables por teclado como si fueran interactivas.
- Conservan su texto original (título, descripción, tag) sin cambios.

### Tarjeta-enlace y tarjeta-ancla
- La tarjeta 1 (Competencias Digitales) usa el mismo patrón ya establecido
  con las tarjetas de DQUILIBRIO: `<a class="service" target="_blank"
  rel="noopener noreferrer">`, con el afordance "Abrir →" visible solo al
  hover/focus.
- La tarjeta 5 (DQUILIBRIO) usa `<a class="service anchor" href="#dquilibrio">`
  (sin `target="_blank"`, es la misma página) y muestra "Ver ↓" en vez de
  "Abrir →" al hover/focus, para no sugerir que abre algo nuevo.

---

## 12. Subpágina "Contenidos" — rediseño del hero y de las tarjetas (nuevo)
Sobre `assets/servicios-subpaginas/contenidos.html` (la subpágina de la
tarjeta "Competencias Digitales"), se aplicaron los siguientes cambios,
pedidos directamente sobre esa subpágina (no afectan el resto del sitio):

1. **Header simplificado**: se eliminó el menú de navegación
   (`DQUILIBRIO · Servicios · Metodología · Equipo`). Queda solo el logo
   (que ya enlazaba a `https://www.concientic.com/`) y el botón "Hablemos".
2. **Hero reemplazado por completo**: el hero original ("Aprender a habitar
   el mundo digital...", con un visual decorativo de órbita/nodos) se
   eliminó. En su lugar, el hero ahora es "¿Qué quieres aprender hoy?" —
   contenido que antes vivía en una sección aparte más abajo en la página
   ("Explora por necesidad") y que se fusionó dentro del hero:
   - Miga de pan: "Servicios · Competencias Digitales · Contenidos" (sin
     cambios).
   - H1: "¿Qué quieres aprender hoy?"
   - Lead: "Empieza por tu propósito, no por una plataforma."
   - Los mismos dos botones que ya existían: "Explorar contenidos" (ancla a
     `#catalogo`) y "Conocer Academia" (ancla a `#academia`).
   - Las 4 tarjetas de ruta (Entender Internet, Empezar con IA, Protegerme,
     Crear y colaborar) se muestran debajo, en una sola fila de 4 en
     tablet/desktop (en móvil bajan a 2 columnas, nunca a 1, para que sigan
     leyéndose como un conjunto).
   - La sección "Explora por necesidad" que existía más abajo se eliminó
     (quedó fusionada en el hero) para no duplicar el mismo contenido dos
     veces en la página.
   - La banda oscura "No necesitas aprenderlo todo..." que ya iba justo
     después del hero no se modificó — sigue en el mismo lugar.
3. **Sección "Guardianes" eliminada**: la sección "El aprendizaje también
   tiene compañía" (grilla con las iniciales de los 7 Guardianes) se quitó
   por completo de esta subpágina.
4. **Tarjetas del catálogo — personaje y color por Guardián real**: cada
   tarjeta de recurso ya traía en sus datos qué Guardián(es) le corresponden
   (ej. `'Byte · Detective DQ'`); se usa ahora el primero de la lista para
   mostrar su imagen oficial (`/guardians/{archivo}.png`) como avatar de la
   tarjeta, y el color de la etiqueta de categoría de cada tarjeta pasa a
   ser el color oficial de ese Guardián en el Manual de Marca (verde para
   Byte, azul para Locky, amarillo para Lex, púrpura para Detective DQ, cian
   para Nexo, naranja para Nova, rosa para Emi) en vez de un color genérico
   por categoría que no correspondía a ningún personaje. No se tocó ningún
   texto de las tarjetas — solo imagen y color.
5. **Identificación de la fuente/proveedor**: en vez de mostrar el nombre
   del proveedor como texto plano gris, cada tarjeta muestra su nombre como
   una pequeña insignia tipográfica en el color de marca real de ese
   proveedor (Google, Microsoft, IBM, Cisco, MinTIC, Meta, OpenLearn,
   Comisión Europea, DQ Institute, UNESCO, Santander).
   **Decisión de diseño, distinta a como se veía en la imagen de
   referencia**: se usó el nombre en texto con el color de marca del
   proveedor, no el logotipo/ícono real de cada empresa. Reproducir el
   isotipo exacto de marcas de terceros (el círculo de colores de Google, las
   4 casillas de Microsoft, el símbolo de Meta, etc.) dentro de un asset que
   se redistribuye implica un uso de marca registrada que conviene evitar
   sin autorización explícita de cada proveedor. El nombre en su color de
   marca cumple la misma función de identificación visual rápida sin ese
   riesgo. Si más adelante consiguen permiso o assets de marca oficiales de
   cada proveedor, esto se puede reemplazar por sus logotipos reales.
6. **Limpieza de CSS muerto**: se eliminaron las reglas de estilo que ya no
   se usan (`.visual`, `.core`, `.orbit`, `.node`, `.n1`-`.n4` del hero
   anterior, y el resto de reglas ligadas a la sección de Guardianes
   eliminada).

No se tocó la sección "Academia ConcienTIC" ni el cierre con el ciclo
DQUILIBRIO — quedan igual que en la versión anterior de esta subpágina.

---

## 14. Rediseño completo de la página principal (v12 → v13)

> Fuente: `docs/concientic_v13_reference.html` (archivo entregado por Jeimy,
> 1.5 MB, imágenes embebidas en base64 — igual que los demás archivos de
> referencia, **no copiar la técnica de base64 a producción**, solo el
> contenido/diseño). Este es un **rediseño de arquitectura de información**,
> no una lista de ajustes puntuales: cambia el menú, se eliminan secciones
> completas de v12 y aparecen secciones nuevas. Tratar como reemplazo total
> de la página principal (manteniendo el header/footer y el sistema de
> diseño base) en vez de aplicar diffs sección por sección.

### 14.1 Nuevo orden de secciones (reemplaza integralmente a §1)
1. Header (logotipo + navegación — ver §14.7, cambia de técnica)
2. Hero — id `inicio`
3. Ecosistema — id `ecosistema` (nueva)
4. Guardianes — id `guardianes` (reemplaza a la sección Equipo/Guardianes de §5 y §1.10)
5. Aprende / Recursos — id `recursos` (nueva; incorpora el enlace a la subpágina "Contenidos")
6. Metodología — id `metodologia` (se conserva, mismo ciclo circular de §4)
7. Experiencia — id `experiencia` (nueva, demo interactiva)
8. DQUILIBRIO — id `dquilibrio` (se conserva, mismas 4 tarjetas y subpáginas de §10)
9. Contacto / CTA final — id `contacto`
10. Footer

**Secciones de v12 que se eliminan por completo** (no tienen equivalente 1:1
en v13 — su contenido o bien se retira, o queda absorbido de forma distinta
en las secciones nuevas de arriba): "El desafío" (`desafio`), "Desinfoxicación"
(`desinfoxicacion`), "Servicios" de 5 tarjetas con estados (`servicios` —
el enlace a la subpágina Contenidos migra a la nueva sección `recursos`, y
el enlace ancla a DQUILIBRIO ya no es necesario porque DQUILIBRIO está en
el menú principal), "Centro de Evidencia" (`evidencia`), "Casos" (`casos`),
"Referentes" (`referentes`), y el Manifiesto de cierre sin ancla. La banda
de principio ("No queremos más tiempo de tu vida...") de §3/§6 tampoco
aparece como sección propia en v13.

**Antes de borrar código**, confirmar con Jeimy si el contenido de estas
secciones (sobre todo Centro de Evidencia, Casos y Referentes, que tienen
reglas estrictas de "no inventar métricas/clientes" ya resueltas) se
descarta definitivamente o se reubica en otra parte del sitio — el archivo
v13 no lo aclara.

### 14.2 Navegación (header y footer)
Menú principal, en este orden exacto: Ecosistema · Guardianes · Aprende ·
Metodología · DQUILIBRIO · botón-CTA "Encuentra tu ruta ↗" (ancla a
`#experiencia`). El footer repite los mismos 5 enlaces (sin el CTA) más el
logotipo y "© ConcienTIC".

### 14.3 Hero (id `inicio`)
- Etiqueta superior: "Aprende con intención. Aplica con criterio."
- Titular (h1): "La inteligencia digital empieza contigo."
- Cuerpo: "No necesitas consumir más contenido. Necesitas reconocer lo que
  importa, desarrollar las competencias adecuadas y llevarlas a tu vida con
  propósito y equilibrio."
- Dos CTA: "Descubre tu siguiente paso ↗" (ancla `#experiencia`) y "Conoce
  nuestra metodología" (ancla `#metodologia`).
- Frase de cierre visual: "Menos ruido. Más criterio. Aprendizaje que se
  convierte en acción."

### 14.4 Ecosistema (id `ecosistema`, nueva)
Encabezado: "El ecosistema ConcienTIC — Tres territorios. Un propósito
compartido." Intro: "Conectamos diagnóstico, acompañamiento inteligente y
soluciones especializadas. Cada componente cumple una función concreta
dentro de una visión común." Tres tarjetas:
1. **01 · Diagnóstico y orientación — DQnexus.** "Reconoce fortalezas y
   oportunidades en tus competencias digitales para orientar próximos
   pasos relevantes." CTA "Explorar el diagnóstico ↗" → ancla `#experiencia`.
2. **02 · Aprendizaje inteligente — TutorIA.** "Un acompañante para
   comprender conceptos, practicar, resolver dudas y avanzar con mayor
   autonomía." CTA "Conocer la experiencia ↗" → ancla `#experiencia`.
3. **03 · Experimentación y aplicación — Laboratorios IA.** "Espacios para
   diseñar, probar y aplicar soluciones con inteligencia artificial a retos
   concretos. SIGINEX es una de las aplicaciones especializadas del
   ecosistema." CTA → ancla `#contacto`.

Nota de honestidad al pie de la sección, **mantenerla literal, no
resumirla ni quitarla**: "La disponibilidad y el alcance de cada producto
deben describirse según su estado real de desarrollo. Esta propuesta no
presupone funcionalidades ya publicadas." — es la misma regla de "no
inventar resultados" que ya rige Casos/Evidencia, aplicada aquí a DQnexus,
TutorIA y Laboratorios IA/SIGINEX.

### 14.5 Guardianes (id `guardianes`, reemplaza la sección Equipo de §5)
Deja de ser una grilla de 7 tarjetas individuales con foto, rol y bio
(como en v12/§5). En v13 es una sola franja con:
- Encabezado: "Los Guardianes — Inteligencia con propósito." / "La IA tiene
  un papel. La persona conserva el protagonismo."
- Cuerpo: "Los Guardianes se integran donde pueden aportar orientación,
  protección, comprensión o creatividad. Cada intervención debe tener una
  razón clara y un límite definido."
- Una sola imagen compuesta con los 7 Guardianes juntos (alt-text oficial:
  "Los siete Guardianes de ConcienTIC: Emi, Locky, Lex, Byte, Detective DQ,
  Nexo y Nova, con sus colores y capacidades digitales.") — **usar el
  asset real de grupo si Jeimy lo provee; si no existe todavía, puede
  componerse con los 7 PNG individuales ya entregados** (`assets/*.png`),
  no hace falta pedir un archivo nuevo para avanzar.
- Lista de 7 competencias con su glifo/ícono (sin nombre de Guardián
  visible en esta franja): Empatía Digital, Seguridad Digital, Derechos
  Digitales, Alfabetización Digital, Pensamiento Crítico, Colaboración
  Digital, Innovación Digital.
- Cierre: "La mejor tecnología no decide por ti: te ayuda a decidir mejor."

**Confirmar con Jeimy** si esto reemplaza definitivamente la sección
Equipo de 7 tarjetas con bios (§5) o si esa versión debe conservarse en
otra página (por ejemplo una futura subpágina "/equipo"), ya que v13 no
incluye biografías ni roles individuales por Guardián en la página
principal.

### 14.6 Aprende / Recursos (id `recursos`, nueva — incorpora el enlace a Contenidos)
Encabezado: "Aprender con intención — Contenido que orienta. Experiencias
que transforman." Intro: "El contenido gratuito sigue siendo una puerta de
entrada. Lo conectamos con rutas, práctica y acompañamiento opcional para
que cada persona encuentre el nivel de apoyo que necesita." Tres tarjetas:
1. **01/EXPLORAR — Referentes y recursos abiertos.** "Contenido curado,
   fuentes confiables y herramientas para comprender un tema sin perderse
   entre miles de enlaces." CTA "Ver contenidos gratuitos ↗" → enlace
   **absoluto** `https://www.concientic.com/servicios/contenidos` (antes
   era una ruta relativa `/servicios/contenidos.html`; mantener el target
   `_blank`/`rel="noopener noreferrer"` establecido en §11 para esta
   subpágina — el contenido de `assets/servicios-subpaginas/contenidos.html`
   no cambia).
2. **02/APRENDER Y PROFUNDIZAR — Academia ConcienTIC.** "Formación y
   programas de aprendizaje disponibles a través de nuestra academia en
   Hotmart, conectados con rutas y objetivos prácticos." CTA "Explorar
   Academia ↗" → enlace externo `https://hotmart.com/` (placeholder real
   del archivo entregado; **confirmar con Jeimy la URL definitiva de la
   Academia en Hotmart** antes de publicar, ya que el dominio genérico
   `hotmart.com` no apunta a la página real del curso).
3. **03/PROFUNDIZAR — Programas y acompañamiento.** Talleres, cohortes o
   apoyo experto para desafíos que requieren interacción y
   retroalimentación.

**Nota sobre el dominio (resuelve la duda abierta desde v2-v6):** el propio
archivo v13 usa `https://www.concientic.com/...` en enlaces absolutos (acá
y en §14.8), no `concientic.vercel.app`. Se adopta `concientic.com` como
dominio de producción definitivo en todo el paquete a partir de esta
versión; `concientic.vercel.app` queda solo como alias/preview de Vercel
si Jeimy decide conservarlo.

### 14.7 Logotipo del header — cambio de técnica (revisar con Jeimy)
v13 **no usa una imagen de logo** (ni el isotipo ni el wordmark PNG/JPG
usados desde §2). El header muestra un lockup de texto en CSS:
"concienTIC" + línea pequeña "INTELIGENCIA DIGITAL CONSCIENTE" debajo, sin
`<img>`. Esto es un cambio respecto a la regla de §2 ("el logo es el
wordmark completo, no CSS/texto reconstruido"). **No implementar este
cambio todavía sin confirmación de Jeimy** — puede ser una simplificación
intencional del archivo de trabajo (p. ej. para que cargue más rápido en
el editor) y no una decisión final de marca. Mientras no haya
confirmación, usar el wordmark de imagen ya vigente (§2) sobre esta nueva
estructura de header/menú.

### 14.8 Experiencia demostrativa (id `experiencia`, nueva)
Encabezado: "Empieza por ti — Tu siguiente paso no tiene que ser
aprenderlo todo." Aviso explícito que debe mostrarse igual, **no
suavizarlo ni quitarlo** (coherente con la regla de no fingir resultados
reales): "Este pequeño ejemplo muestra cómo ConcienTIC podría orientar el
primer paso. No es el diagnóstico oficial DQnexus ni guarda respuestas. En
la experiencia real, las recomendaciones deberán apoyarse en criterios
transparentes, recursos confiables y una ruta relacionada con tu
objetivo." Etiqueta: "Experiencia demostrativa · 1 pregunta — ¿Qué te
gustaría mejorar primero?" con 4 opciones (usar la IA con más criterio y
seguridad / evaluar información y reconocer la desinformación / ahorrar
tiempo con herramientas digitales / recuperar equilibrio y atención en mi
vida digital) y botón "Ver una orientación inicial ↗". La lógica de
recomendación es un `switch`/objeto JS simple embebido en el archivo de
referencia (no hay backend) — implementar como componente de cliente sin
persistencia ni envío de datos, y mantener visible el aviso de que es
demostrativa.

### 14.9 Contacto / CTA final (id `contacto`)
Encabezado: "El siguiente paso empieza aquí — Haz que la tecnología tenga
sentido para ti." Cuerpo: "Cuéntanos qué quieres comprender, mejorar o
transformar. Podemos ayudarte a identificar un punto de partida." CTA
"Conversemos ↗".

### 14.10 Paleta — desviaciones encontradas en el archivo v13 (confirmar, no corregir sin autorización)
El archivo v13 usa casi la misma paleta de tokens de siempre pero con dos
valores hex que no coinciden exactamente con el Manual de Marca v2.0:
- `--navy` (fondo/texto oscuro) = `#0D182A` en v13, vs. `#0D1B2A` oficial.
- `--pink` (Rosa Humano) = `#FF68B4` en v13, vs. `#FF6EB6` oficial.
También usa `--paper` = `#f5f7f3` como fondo de `<body>`, muy cercano pero
no idéntico al `#F5F7F9` de "Superficie" del Design System v1.0. Y la
tipografía: **Poppins no se carga en ningún lado del archivo v13** — todo
el texto, incluidos los titulares, usa Inter. El Manual de Marca v2.0
especifica Poppins para marca/titulares. **Tratar estas cuatro diferencias
como pendientes de confirmación con Jeimy, no como correcciones
automáticas** — podrían ser una decisión intencional de este rediseño o
un desvío accidental del archivo de trabajo. Mientras no haya respuesta,
usar los valores oficiales del Manual de Marca (hex exactos y Poppins para
titulares) en la implementación, y dejarlo anotado como pregunta abierta
en la revisión visual (`06_REVISION_VISUAL.md`).

### 14.11 Accesibilidad — qué se conserva y qué falta en el archivo de referencia
Se mantienen en v13: `:focus-visible` global, `aria-live` para el mensaje
de estado, y `prefers-reduced-motion`. **No está presente el "skip link"**
("Saltar al contenido") que sí exige §8/§13 de este spec — mantenerlo en
la implementación de todas formas, ya que es un requisito de accesibilidad
del Design System v1.0, no una decisión de diseño visual de esta página.
Tampoco hay tarjetas deshabilitadas/"En construcción" en v13 (ese patrón
de §11 solo sigue vigente en la sección Servicios que ya no existe en la
página principal — las subpáginas de Servicios y sus estados no cambian).

---

## 16. Subpágina "Laboratorios IA" (nuevo)

> Fuente: `assets/ecosistema-subpaginas/laboratoriosia.html` (archivo
> entregado por Jeimy). Se publica en producción como
> `https://www.concientic.com/ecosistema/laboratoriosia` (ruta propuesta por
> consistencia con las demás subpáginas — **confirmar con Jeimy** si prefiere
> otra ruta, por ejemplo `/laboratoriosia` directamente en la raíz).

### 16.1 Regla nueva y transversal: el menú de TODAS las subpáginas pasa a ser el de la página central
Jeimy indicó explícitamente: *"en todas las subpáginas vamos a manejar el
mismo menú de la página central"*. Esto es una regla general, no específica
de esta subpágina, y cambia el criterio que se venía siguiendo hasta ahora
(cada subpágina con su propio menú, copiada byte a byte sin tocar nada).
Para esta subpágina ya se aplicó: se sustituyó su `<nav>` propio ("Inicio /
Laboratorios / Nuestro enfoque") y los enlaces del footer por el menú
vigente de la home v13 (Ecosistema · Guardianes · Aprende · Metodología ·
DQUILIBRIO · CTA "Encuentra tu ruta ↗"), todos como enlaces absolutos con
ancla a `https://www.concientic.com/#<id>` (porque la subpágina no vive en
la misma URL que esas secciones). El resto del archivo (hero, los 4
laboratorios, sección "Nuestro enfoque", CTA final, lógica de artefactos
pendientes) se conserva igual que lo entregado — **no se tocó nada más**.

**Pendiente de decisión con Jeimy** (no se hizo sin confirmación): las
subpáginas ya entregadas antes de esta regla (las 4 de DQUILIBRIO y
"Contenidos") siguen con su propio menú original, distinto al de la home.
Por consistencia con la nueva regla, probablemente deban actualizarse de la
misma forma — pero esto implica modificar archivos que la regla del
proyecto protege como "no tocar sin confirmación explícita". Antes de
aplicarlo, preguntar a Jeimy si quiere que las 5 subpáginas anteriores se
actualicen también con el menú de la home.

### 16.2 Contenido de la subpágina (sin cambios respecto al archivo entregado)
- Hero: "La inteligencia artificial empieza cuando la llevas a la
  práctica." con dos CTA ("Explorar laboratorios ↘" ancla interna a la
  grilla, "Conoce ConcienTIC ↗" → home).
- Grilla de 4 laboratorios, cada uno con tag, número y enlace a su propio
  artefacto (actualmente todos vacíos en `ARTIFACT_URLS`, por lo que el
  clic muestra un aviso "pendiente de configurar" en vez de navegar — no
  simular un enlace funcional que no existe, coherente con la regla de no
  fingir resultados):
  1. **SIGINEX** — Sistema de Gestión (SST, gestión inteligente de riesgos).
  2. **EmprendeCreativo** — creatividad y emprendimiento con IA.
  3. **DQ-Nexus** — autodiagnóstico de Inteligencia Digital.
  4. **TutorIA** — aprendizaje acompañado por tutor de IA.
- Cada tarjeta tiene un `logo-slot` con ícono genérico de línea y el texto
  "Logo oficial por incorporar" — **no inventar ni descargar logos de
  terceros aquí tampoco** (misma regla ya aplicada a los proveedores de la
  subpágina "Contenidos", spec §12).
- Sección "Nuestro enfoque" (4 principios) y CTA final "Encuentra el
  laboratorio que conecta con tu reto." — sin cambios.

### 16.3 Relación con la sección "Ecosistema" de la home v13
La tarjeta "03 · Experimentación y aplicación — Laboratorios IA" de la
sección Ecosistema (spec §14.4) actualmente enlaza a `#contacto`. **Ahora
que existe esta subpágina, ese CTA debe actualizarse** para abrir
`https://www.concientic.com/ecosistema/laboratoriosia` en pestaña nueva
(mismo patrón `target="_blank" rel="noopener noreferrer"` que las demás
subpáginas), en vez de la ancla a Contacto.

### 16.4 Paleta — misma observación que en §14.10
Este archivo reutiliza los mismos tokens de v13, incluida la misma
ausencia de Poppins y las mismas variantes de `--pink`/`--paper` ya
señaladas. No se repite la corrección aquí: aplica la misma pauta de
§14.10 (usar los valores oficiales del Manual de Marca hasta que Jeimy
confirme lo contrario).

---

## 15. Criterios de aceptación

**Vigentes para la página principal (reemplazados por §14 — ver nota):**
estos primeros puntos describían la página principal en su estado v12.
Desde v13, el orden de secciones, el logo y la sección Equipo que describen
ya NO aplican a la página principal (ver §14.1, §14.5, §14.7 para el estado
vigente); se conservan aquí sin borrar porque documentan la historia y
porque las reglas de interacción/accesibilidad/responsive sí siguen
aplicando igual.

- `npm run build` exitoso, sin errores de TypeScript ni lint.
- El visual del Hero y el diagrama de Metodología son las imágenes finales de
  `assets/diagrams/` (no CSS/SVG reconstruido).
- Botones, enlaces y tarjetas tienen los estados de hover descritos en §7;
  todos respetan `prefers-reduced-motion`.
- Existe skip link, `:focus-visible` global, y el formulario de contacto usa
  un mensaje de estado accesible en vez de `alert()`.
- Responsive en 360, 768, 1024 y 1440 px.
- No placeholders visibles salvo casos reales aún no disponibles, claramente
  marcados.
- Vercel deployment sin configuración innecesaria.
- Las 4 tarjetas de DQUILIBRIO son enlaces funcionales que abren
  `https://www.concientic.com/dquilibrio/{atencion,informacion,discernimiento,autonomia}.html`
  en una pestaña nueva (`target="_blank"`), y las 4 subpáginas están
  desplegadas sin alterar su contenido, estilo ni comportamiento originales.
- La subpágina "Contenidos" (en `https://www.concientic.com/servicios/contenidos`)
  tiene un solo hero fusionado ("¿Qué quieres aprender hoy?" + 4 tarjetas de
  ruta), sin la sección "Explora por necesidad" duplicada ni la sección de
  Guardianes; cada tarjeta del catálogo muestra el avatar y color del
  Guardián real que le corresponde según sus datos.

**Nuevos, específicos de v13 (página principal):**
- El orden de secciones y del menú de la página principal coincide
  exactamente con §14.1/§14.2 (Hero, Ecosistema, Guardianes, Recursos,
  Metodología, Experiencia, DQUILIBRIO, Contacto) — ya no existen como
  secciones independientes El desafío, Desinfoxicación, el bloque de 5
  tarjetas de Servicios, Centro de Evidencia, Casos, Referentes ni el
  Manifiesto de cierre, salvo que Jeimy confirme reubicarlos (ver aviso en
  §14.1).
- La sección Ecosistema muestra las 3 tarjetas de §14.4 con la nota de
  honestidad ("no presupone funcionalidades ya publicadas") visible y sin
  resumir.
- La sección Guardianes de la página principal es la franja única de §14.5
  (imagen de grupo + 7 competencias + cierre), no la grilla de 7 tarjetas
  con bio individual de §5 — salvo que Jeimy confirme mantener ambas
  versiones en páginas distintas.
- La sección Experiencia implementa la demo de §14.8 como componente de
  cliente puramente ilustrativo, con el aviso de "no es el diagnóstico
  oficial" visible siempre, sin guardar ni enviar respuestas.
- El enlace a la Academia ConcienTIC en Hotmart usa la URL real confirmada
  por Jeimy, no el placeholder genérico `hotmart.com` del archivo de
  referencia.
- Las cuatro desviaciones de marca de §14.10 (hex de `--navy`/`--pink`,
  `--paper`, ausencia de Poppins) y el cambio de logo-imagen a
  logo-texto de §14.7 están resueltas con una respuesta explícita de Jeimy
  antes de publicar en producción; hasta entonces, la implementación usa
  los valores oficiales del Manual de Marca.
- El dominio de producción usado en todo el código, metadata y enlaces
  absolutos es `https://www.concientic.com` (ver §14.6).

**Nuevos, específicos de la subpágina Laboratorios IA (§16):**
- La subpágina está desplegada en `https://www.concientic.com/ecosistema/laboratoriosia`
  (o la ruta que Jeimy confirme), con el menú de header y footer igual al
  de la home vigente (§14.2), no el menú propio que traía el archivo
  original.
- El resto de su contenido (hero, 4 laboratorios, sección "Nuestro
  enfoque", CTA final) es idéntico al archivo entregado, sin reescribirlo.
- Los 4 enlaces de artefacto (`SIGINEX`, `EmprendeCreativo`, `DQ-Nexus`,
  `TutorIA`) siguen mostrando el aviso "pendiente de configurar" hasta que
  Jeimy entregue las URLs reales — no se simula una navegación que no
  existe.
- La tarjeta "Laboratorios IA" de la sección Ecosistema de la home (§14.4)
  enlaza a esta subpágina en pestaña nueva, no a `#contacto`.
- Está pendiente de confirmación con Jeimy si las 5 subpáginas entregadas
  antes de esta versión (DQUILIBRIO ×4 y "Contenidos") deben actualizarse
  también para usar el menú de la home, conforme a la regla nueva de §16.1.
