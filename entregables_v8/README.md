# ConcienTIC — Entregables para Kiro + Next.js + Vercel (v8)

Fecha: 2026-10-26

## Qué contiene esta versión del paquete
Este paquete reemplaza al entregado hoy mismo (v7). Todo lo de esa versión
sigue vigente; esta entrega agrega la subpágina **"Laboratorios IA"**
(`assets/ecosistema-subpaginas/laboratoriosia.html`), con sus 4
laboratorios (SIGINEX, EmprendeCreativo, DQ-Nexus, TutorIA), enlazada desde
la tarjeta "Laboratorios IA" de la sección Ecosistema de la home. También
introduce una **regla nueva y transversal**: todas las subpáginas deben
usar el mismo menú de la página central en vez de un menú propio. Ya se
aplicó a "Laboratorios IA"; las 5 subpáginas entregadas antes (DQUILIBRIO
×4 y "Contenidos") **no se modificaron** — queda pendiente confirmar con
Jeimy si también deben actualizarse. Detalle completo en
`kiro/specs/concientic-web-redesign.md` §16 y en
`prompts/11_LABORATORIOS_SUBPAGINA.md`.

## Changelog v8 (nuevo respecto a v7) — Subpágina "Laboratorios IA" + regla de menú
- Nueva subpágina estática con hero, 4 tarjetas de laboratorio (cada una
  con tag, descripción y enlace a su artefacto — hoy todos pendientes de
  configurar, sin URLs inventadas), sección "Nuestro enfoque" y CTA final.
- Se sustituyó el menú propio del archivo original (header y footer) por
  el menú vigente de la home v13 (Ecosistema · Guardianes · Aprende ·
  Metodología · DQUILIBRIO), con enlaces absolutos a
  `https://www.concientic.com/#<id>` — el resto del contenido no se tocó.
- La tarjeta "Laboratorios IA" de la sección Ecosistema (home) debe
  enlazar a esta subpágina en pestaña nueva en vez de a `#contacto`.
- Ruta de publicación propuesta: `https://www.concientic.com/ecosistema/laboratoriosia`
  — a confirmar con Jeimy.
- **Pendiente de confirmación, no aplicado todavía**: si las 5 subpáginas
  anteriores (DQUILIBRIO ×4 y "Contenidos") deben actualizar su menú propio
  al de la home, siguiendo la misma regla.

## Changelog v7 — rediseño completo de la página principal (heredado, sigue vigente)
Este paquete anterior (entregado hoy mismo antes de esta versión) sigue
vigente (subpáginas de DQUILIBRIO, subpágina "Contenidos" con
su rediseño); esta entrega documenta e implementa un **rediseño completo de
la página principal** a partir del archivo `ConcienTIC_redisenio_v9.html`
entregado por Jeimy — nueva arquitectura de información de 8 secciones
(Hero, Ecosistema, Guardianes, Aprende/Recursos, Metodología, Experiencia,
DQUILIBRIO, Contacto), que reemplaza a la de 14 secciones vigente desde la
v2. El dominio de producción queda confirmado como `concientic.com` (el
propio archivo de Jeimy ya usa enlaces absolutos a ese dominio). El spec
(`kiro/specs/concientic-web-redesign.md`) conserva **todo** el recorrido
histórico v5→v12 en sus secciones §1-§13, y añade la §14 con el detalle
completo del rediseño v12→v13. El nuevo prompt
`prompts/10_REDISENIO_HOME_V13.md` cubre la aplicación paso a paso sobre un
repo que ya esté en v12; si tu repositorio quedó en un punto anterior,
aplica primero `07_ACTUALIZACION_CAMBIOS.md` / `08_SUBPAGINAS_DQUILIBRIO.md`
/ `09_SERVICIOS_SUBPAGINAS.md` según corresponda, y luego el prompt 10.

**Puntos que requieren tu confirmación antes de publicar en producción**
(detallados en spec §14 y en `prompts/10_REDISENIO_HOME_V13.md`): (1) qué
pasa con el contenido eliminado de la home — El desafío, Desinfoxicación,
Centro de Evidencia, Casos, Referentes, el bloque de 5 tarjetas de
Servicios y el Manifiesto de cierre (¿se descartan o se reubican en otra
página?); (2) si la sección Equipo con las 7 bios individuales debe
conservarse en alguna otra página, ya que la home ahora solo muestra una
franja compacta de Guardianes; (3) la URL real de la Academia ConcienTIC en
Hotmart (el archivo trae el dominio genérico `hotmart.com`); (4) si el
cambio del logo-imagen a un logo de texto en CSS en el header es
intencional; (5) cuatro pequeñas desviaciones de paleta/tipografía frente
al Manual de Marca v2.0 (hex de `--navy` y `--pink`, tono de `--paper`, y
ausencia total de Poppins — todo el texto del archivo usa Inter).

## Changelog v7 (nuevo respecto a v6) — Rediseño completo de la página principal
- **Nueva arquitectura de información** (8 secciones en vez de 14): Hero →
  Ecosistema → Guardianes → Aprende/Recursos → Metodología → Experiencia →
  DQUILIBRIO → Contacto. Detalle completo en spec §14.1-§14.9.
- **Secciones eliminadas** (pendientes de confirmar destino): El desafío,
  Desinfoxicación, el bloque de 5 tarjetas de Servicios, Centro de
  Evidencia, Casos, Referentes, Manifiesto de cierre.
- **Sección "Ecosistema" (nueva)**: presenta DQnexus, TutorIA y
  Laboratorios IA (con SIGINEX como aplicación especializada) como "tres
  territorios" del ecosistema, con nota explícita de que ningún producto
  se presupone ya publicado.
- **Sección "Guardianes" simplificada**: pasa de una grilla de 7 tarjetas
  con foto/rol/bio individual a una sola franja con imagen de grupo y
  lista de 7 competencias, sin bios.
- **Sección "Aprende/Recursos" (nueva)**: absorbe el enlace a la subpágina
  "Contenidos" (que antes vivía en Servicios) junto con Academia ConcienTIC
  (Hotmart) y "Programas y acompañamiento".
- **Sección "Experiencia" (nueva)**: demo interactiva de una pregunta con 4
  opciones y una recomendación orientativa, explícitamente marcada como
  demostrativa y sin guardar respuestas.
- **DQUILIBRIO y Metodología** se conservan con el mismo contenido; los
  enlaces de las 4 tarjetas de DQUILIBRIO y de la subpágina "Contenidos"
  ahora usan el dominio absoluto `https://www.concientic.com/...`.
- **Dominio de producción confirmado**: `concientic.com` (reemplaza la
  referencia a `concientic.vercel.app` usada en versiones anteriores del
  paquete).
- Se documentan (sin corregir de forma automática) 4 desviaciones de marca
  del archivo de referencia frente al Manual de Marca v2.0 y el cambio de
  logo-imagen a logo-texto en el header — ver spec §14.7 y §14.10.

## Changelog v6 (nuevo respecto a v5) — Rediseño de la subpágina "Contenidos"
- **Header simplificado**: se quitó el menú de navegación de esta
  subpágina; queda solo el logo (ya enlazaba a `concientic.com`) y el botón
  "Hablemos".
- **Hero reemplazado**: "Aprender a habitar el mundo digital..." (con un
  visual decorativo de órbita) desapareció. El nuevo hero es
  "¿Qué quieres aprender hoy?", con los mismos dos botones que ya existían
  ("Explorar contenidos" / "Conocer Academia") y las 4 tarjetas de ruta
  (Entender Internet, Empezar con IA, Protegerme, Crear y colaborar) ahora
  fusionadas dentro del hero, en una sola fila de 4. La sección donde antes
  vivían esas tarjetas, más abajo en la página, se eliminó para no
  duplicarlas.
- **Sección "Guardianes" eliminada** de esta subpágina (la grilla con las
  iniciales de los 7 Guardianes).
- **Tarjetas del catálogo con personaje y color reales**: cada tarjeta ahora
  muestra la imagen oficial del Guardián que le corresponde (según sus
  propios datos) y el color de su etiqueta de categoría es el color oficial
  de ese Guardián en el Manual de Marca — antes eran colores genéricos sin
  relación con ningún personaje.
- **Insignias de proveedor**: cada tarjeta identifica su fuente (Google,
  Microsoft, IBM, Cisco, MinTIC, Meta, OpenLearn, Comisión Europea, DQ
  Institute, UNESCO, Santander) con su nombre en el color de marca de ese
  proveedor.
  **Nota importante**: no se reprodujo el logotipo/ícono real de cada
  empresa (el círculo de Google, las casillas de Microsoft, etc.) — ver el
  porqué en `kiro/specs/concientic-web-redesign.md` (§12, punto 5).
- Se limpió el CSS que quedó sin uso tras estos cambios.
- La sección "Academia ConcienTIC" y el cierre con el ciclo DQUILIBRIO no se
  tocaron.

## Changelog v5 (nuevo respecto a v4) — Servicios: Contenidos y tarjetas en construcción
- La sección Servicios tiene 5 tarjetas; cada una cambia de forma distinta:
  - **Competencias Digitales** → enlace, abre en pestaña nueva la subpágina
    "Contenidos" (`assets/servicios-subpaginas/contenidos.html`, un catálogo
    filtrable de recursos gratuitos de aprendizaje digital por categoría,
    con buscador, y una sección "Academia ConcienTIC" marcada
    "Próximamente"). Se copia tal cual, sin modificar, igual que las
    subpáginas de DQUILIBRIO.
  - **DQUILIBRIO** → enlace ancla a `#dquilibrio` (misma página, sin pestaña
    nueva); muestra "Ver ↓" en vez de "Abrir →" al hover/focus.
  - **Desinfoxicación** y **Transformación cultural** → deshabilitadas: fondo
    gris, borde discontinuo, sin hover, etiqueta "En construcción",
    `aria-disabled="true"`. No son clicables ni tienen subpágina planeada
    todavía.
  - **IA consciente** → sin cambios por ahora. Tendrá una subpágina llamada
    "Laboratorios" cuando se entregue su HTML.
- Ver el detalle completo en `kiro/specs/concientic-web-redesign.md` (§11) y
  en `prompts/09_SERVICIOS_SUBPAGINAS.md`.
- **Nota**: a diferencia de las subpáginas de DQUILIBRIO, "Contenidos" sí
  trae su propio mecanismo de regreso (el logo y el menú de su header
  enlazan a `https://www.concientic.com/` y a las anclas reales del sitio).
  Usa el dominio `concientic.com`; confirmar cuál es el dominio de
  producción real antes de publicar.

## Changelog v4 (nuevo respecto a v3) — Subpáginas DQUILIBRIO
- Las 4 tarjetas de la sección DQUILIBRIO (Recuperar presencia, Reducir
  saturación, Decidir con criterio, Elegir conscientemente) pasaron de ser
  texto estático a **enlaces clicables**, cada uno con su propia experiencia
  interactiva (temporizador, curador de información, verificador de
  afirmaciones, diseñador de decisión) y su propia pareja de Guardianes.
- Cada tarjeta abre su subpágina en una **pestaña nueva**
  (`target="_blank" rel="noopener noreferrer"`), dejando la pestaña original
  del sitio abierta detrás — así el regreso es simplemente cambiar de
  pestaña o cerrar la nueva. No se agregó ningún botón de "volver" dentro de
  las subpáginas.
- Al pasar el mouse o enfocar una tarjeta, aparece un afordance discreto
  "Abrir →" (mismo lenguaje visual que "Visitar referente ↗" en Referentes),
  para dejar claro que ahora son clicables.
- Las 4 subpáginas (`assets/dquilibrio-subpaginas/*.html`) se entregaron ya
  diseñadas y se conservan **tal cual, sin modificar** — se copian byte a
  byte a `public/dquilibrio/` en Next.js. Ver el detalle completo en
  `kiro/specs/concientic-web-redesign.md` (§10) y en
  `prompts/08_SUBPAGINAS_DQUILIBRIO.md`.
- **Inconsistencia detectada y señalada, no corregida**: las 4 subpáginas
  usan el isotipo original (árbol/cerebro) en su header, no el wordmark
  "ConcienTIC Nexus" ya vigente en el resto del sitio. Queda pendiente de tu
  confirmación para una futura iteración.

## Changelog v5 → v10 (heredado de la versión anterior del paquete)

### Logo
- Se reemplazó el isotipo (árbol/cerebro) + texto CSS "concienTIC" del header
  por el wordmark imagen "ConcienTIC Nexus" (sin el ícono), en dos variantes
  (fondo claro / fondo oscuro), también agregado al footer.
- Tamaño aumentado a 58px de alto en header y 38px en footer para que
  "NEXUS" y el tagline sean legibles.

### Hero
- Texto del párrafo lead actualizado.
- El visual (composición CSS de anillos + píldoras flotantes) se reemplazó
  por la ilustración final `equilibrio-concientic-mejorado.png`, mostrada más
  grande (hasta 600px de ancho).

### Metodología
- El diagrama SVG dibujado a mano se reemplazó por la ilustración final
  `ciclo-dquilibrio-mejorado.png` (con "DQ" en verde y "UILIBRIO" en blanco).

### Orden de secciones
- "Servicios" se movió de después de "Desinfoxicación" a inmediatamente
  después de "DQUILIBRIO". Menú de header y footer actualizado.

### Equipo / Guardianes
- Las dos secciones originales (`.team-hero` + `.guardians`, con dos tonos de
  fondo oscuro distintos) se unificaron en una sola sección de fondo oscuro
  uniforme.
- Se eliminó el segundo encabezado ("Equipo virtual / Conoce a los
  Guardianes") y las dos cajas de estadística ("7 agentes" / "1 inteligencia
  colectiva").
- Se eliminó la línea "Agente virtual · Equipo ConcienTIC" de cada tarjeta.
- Se agregó una tarjeta de cita como 8º elemento de la grilla (junto a las 7
  tarjetas de Guardián), con texto grande.
- El cierre de sección pasó de un solo color a un color distinto por
  adjetivo.

### Manifiesto
- El titular se redujo de tamaño para equilibrar la columna izquierda con la
  grilla de 6 recuadros de principios de la derecha.

### Interacción y microanimaciones (nuevo respecto a v5, que casi no tenía)
- Botones: relleno deslizante desde la izquierda al hover/focus.
- Enlaces de texto: subrayado animado que crece al hover/focus.
- Tarjetas genéricas: elevación leve al hover.
- Tarjetas de Guardián: elevación más notoria + intensificación de borde y
  resplandor.
- Todo desactivado bajo `prefers-reduced-motion`.

### Accesibilidad (nuevo respecto a v5, que no tenía nada de esto)
- Skip link "Saltar al contenido" al inicio del `<body>`.
- `:focus-visible` global con contorno visible.
- Formulario de contacto: mensaje de estado accesible (`aria-live="polite"`)
  en vez de `alert()` del navegador.

El detalle completo, con el "antes" y "después" de cada punto y los criterios
de aceptación, está en `kiro/specs/concientic-web-redesign.md`.

## Objetivo
Migrar y reconstruir el sitio `https://www.concientic.com/` como una
aplicación Next.js moderna, manteniendo la arquitectura conceptual de
ConcienTIC y aplicando el Manual de Marca v2.0, el Sistema de Diseño Web v1.0
y todos los ajustes descritos arriba.

## Fuente visual de referencia
`docs/concientic_v13_reference.html` es el prototipo visual vigente de la
**página principal** (reemplaza a `docs/concientic_v12_reference.html` desde
la v7 de este paquete — ver spec §14). `concientic_v12_reference.html` y
`concientic_v5_reference.html` se conservan solo como histórico, para poder
entender el "antes" de cada cambio. Ningún archivo de referencia debe
copiarse como arquitectura final: debe convertirse en componentes Next.js
reutilizables.

## Documentos de autoridad
- `docs/Manual_de_Marca_ConcienTIC_v2_0.docx`
- `docs/Sistema_de_Diseno_Web_ConcienTIC_v1_0.docx`
- `kiro/steering/*`
- `kiro/specs/concientic-web-redesign.md`

## Assets
- `assets/` — logo original (isotipo, conservado para favicon), los 7
  Guardianes con transparencia real, y el nuevo wordmark "ConcienTIC Nexus"
  en variante clara y oscura.
- `assets/diagrams/` — las dos ilustraciones DQUILIBRIO finales (Hero y
  Metodología), listas para usar tal cual vía `next/image`.
- `assets/dquilibrio-subpaginas/` — las 4 subpáginas interactivas
  (`atencion.html`, `informacion.html`, `discernimiento.html`,
  `autonomia.html`), entregadas ya terminadas y autocontenidas. Se copian
  tal cual a `public/dquilibrio/` en Next.js — no se reescriben.
- `assets/servicios-subpaginas/` — la subpágina "Contenidos"
  (`contenidos.html`), entregada ya terminada y autocontenida. Se copia tal
  cual a `public/servicios/` — no se reescribe.
- `assets/ecosistema-subpaginas/` — la subpágina "Laboratorios IA"
  (`laboratoriosia.html`), entregada terminada; a diferencia de las
  demás subpáginas, **ya se le actualizó el menú** (header y footer) para
  que coincida con el de la home, por la nueva regla transversal de §16.1
  — el resto de su contenido no se tocó. Se copia a `public/ecosistema/`.

## Nota — "Laboratorios IA" ya resuelta; regla de menú pendiente para las subpáginas anteriores
La subpágina "Laboratorios IA" ya fue entregada y se enlaza desde la
tarjeta "Laboratorios IA" de la sección Ecosistema de la home (antes
pendiente, ver v7). Lo que queda abierto es distinto: Jeimy pidió que
**todas** las subpáginas compartan el menú de la home, pero esa regla solo
se aplicó a "Laboratorios IA" (la más reciente). Las 5 subpáginas
anteriores (DQUILIBRIO ×4 y "Contenidos") siguen con su menú propio
original — confirmar con Jeimy si también deben actualizarse antes de
tocarlas.

## Cómo ejecutar esto en Kiro

**Si el repositorio ya está en el estado v13** (home con las 8 secciones
vigentes): pega directamente `prompts/11_LABORATORIOS_SUBPAGINA.md` — es lo
único que falta.

**Si el repositorio ya está en el estado v12** (home de 14 secciones, ya con
subpáginas DQUILIBRIO y "Contenidos"): pega `prompts/10_REDISENIO_HOME_V13.md`
y luego `prompts/11_LABORATORIOS_SUBPAGINA.md`.

**Si el repositorio tiene una versión anterior a v12** (de cualquier
iteración basada en v5): pega primero `prompts/07_ACTUALIZACION_CAMBIOS.md`
(y `08_SUBPAGINAS_DQUILIBRIO.md` / `09_SERVICIOS_SUBPAGINAS.md` si faltan),
luego `prompts/10_REDISENIO_HOME_V13.md`, y por último
`prompts/11_LABORATORIOS_SUBPAGINA.md`.

**Si es una construcción nueva o el repositorio solo tiene placeholders**:
1. Ejecutar Prompt 00 — Auditoría.
2. Instalar/usar los steering files de `kiro/steering/` y `AGENTS.md`.
3. Ejecutar Prompt 01 — Base Next.js y arquitectura.
4. Ejecutar Prompt 02 — Design System y componentes (incluye patrones de
   interacción y accesibilidad).
5. Ejecutar Prompt 10 — Construir la página principal directamente en su
   arquitectura vigente de 8 secciones (usar `03_IMPLEMENTACION.md` y
   `04_EQUIPO_GUARDIANES.md` solo como referencia de patrones de componente,
   no de orden de secciones — esos prompts describen el estado v12, ya
   superado).
6. Ejecutar Prompt 08 — Subpáginas DQUILIBRIO (enlaces + assets estáticos).
7. Ejecutar Prompt 09 — Servicios: subpágina "Contenidos" (enlazada ahora
   desde la sección "Aprende/Recursos", ver Prompt 10 punto G).
8. Ejecutar Prompt 11 — Subpágina "Laboratorios IA" (enlazada desde la
   tarjeta "Laboratorios IA" de Ecosistema) y nueva regla de menú para
   subpáginas.
9. Ejecutar Prompt 05 — QA, accesibilidad, performance y Vercel.
10. Ejecutar Prompt 06 — Revisión visual contra `concientic_v13_reference.html`,
    incluyendo las preguntas abiertas listadas al final de los Prompts 10 y 11.

También puedes pegar `prompts/MASTER_KIRO.md` directamente: incluye el
contexto completo y decide internamente qué prompts aplicar según el estado
real del repositorio.

## Regla de trabajo
No empezar por "embellecer" el HTML existente. Primero comprender el
repositorio actual, preservar lo útil y migrar hacia componentes, tokens y
contenido estructurado.

## Stack objetivo
Next.js + TypeScript + React + CSS/Tailwind solo si ya existe o si Kiro
justifica su incorporación. App Router.

## Principio de producto
ConcienTIC no debe competir por atención. El sitio debe ser claro, pausado,
útil y fácil de abandonar. No usar infinite scroll, autoplay, streaks,
rankings, contadores artificiales, FOMO, dark patterns ni animaciones que
busquen retención.
