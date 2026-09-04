# Prompt 07 — Aplicar TODOS los cambios acumulados (v5 → v10) sobre el repositorio ya desplegado

Usa este prompt si el repositorio que despliega `https://concientic.vercel.app/`
**ya tiene implementada** una versión del sitio basada en el prototipo
original `concientic_v5_reference.html` (con el que se construyó por primera
vez). Este prompt no reconstruye el sitio desde cero: aplica, uno por uno, los
cambios que se acumularon desde esa versión hasta la actual
(`docs/concientic_v10_reference.html`).

Antes de tocar código, lee `kiro/specs/concientic-web-redesign.md` (v3), que
tiene el detalle completo de cada punto de abajo con el "antes" y el
"después" exactos.

Ve aplicando cada cambio y verificándolo antes de pasar al siguiente.

## A. Logo
1. Reemplaza el isotipo (árbol/cerebro) + texto CSS "concienTIC" del header
   por el nuevo wordmark imagen "ConcienTIC Nexus": usa
   `assets/concientic-nexus-wordmark-transparente-fondo-claro.png` en fondos
   claros (header, footer) y `...-fondo-oscuro.png` si en algún momento se usa
   sobre un fondo oscuro.
2. Tamaño: debe leerse "NEXUS" y el tagline "Conciencia Digital para un mundo
   mejor." — usa 58px de alto en el header y 38px en el footer. No uses un
   tamaño menor (ilegible).
3. Aplica también el wordmark en el footer (antes solo había texto plano
   "ConcienTIC · Conciencia Digital para un mundo mejor.").

## B. Hero — texto
4. Reemplaza el párrafo lead por exactamente:
   "ConcienTIC desarrolla Inteligencia Digital mientras ayuda a personas y
   organizaciones a construir una relación consciente, autónoma y
   equilibrada con la tecnología."

## C. Hero — visual
5. Elimina la composición CSS del visual del Hero (caja con anillos
   `::before`/`::after`, círculo `.core` "DQUILIBRIO", píldoras `.node`
   ATENCIÓN/IA+TECH/CRITERIO/AUTONOMÍA/HUMANIDAD).
6. Reemplázala por la imagen `assets/diagrams/equilibrio-concientic-mejorado.png`,
   mostrada a un ancho máximo de ≈600px en desktop (antes el contenedor
   limitaba a ~460-510px).

## D. Metodología — diagrama
7. Elimina el `<svg>` dibujado a mano (arcos de colores, 5 círculos
   numerados, centro "DQUILIBRIO").
8. Reemplázalo por la imagen `assets/diagrams/ciclo-dquilibrio-mejorado.png`.
9. Elimina cualquier CSS que solo existiera para ese SVG (`.cycle-node-g`,
   `.cycle circle.node`, etc.) — ya no se usa.

## E. Orden de secciones
10. Mueve "Servicios" para que quede inmediatamente después de "DQUILIBRIO"
    (antes iba después de "Desinfoxicación").
11. Actualiza el menú de navegación del header y del footer para que
    reflejen este nuevo orden: DQUILIBRIO → Servicios → El desafío →
    Metodología → Evidencia → Equipo → Referentes.

## F. Sección Equipo — reestructuración completa
12. Unifica las dos secciones existentes (`.team-hero` de fondo `--dark` +
    `.guardians` de fondo casi negro `#050A12`) en **una sola sección**, con
    fondo `--dark` de principio a fin.
13. Deja un único encabezado: kicker "Nuestro equipo" + H2 "Guardianes de la
    Inteligencia Digital" + el párrafo descriptivo. Elimina por completo el
    segundo encabezado "Equipo virtual / Conoce a los Guardianes" y su
    párrafo "No son mascotas decorativas...".
14. Elimina las dos cajas de estadística "7 agentes..." / "1 inteligencia
    colectiva...".
15. Elimina la línea "Agente virtual · Equipo ConcienTIC" del pie de cada una
    de las 7 tarjetas de Guardián.
16. Agrega una tarjeta de cita como 8º elemento de la grilla de 4 columnas
    (junto a las 7 tarjetas), sin imagen, con el texto: "Cada guardián tiene
    un territorio de competencia y una función real dentro de las
    experiencias del Ecosistema ConcienTIC." en un tamaño de fuente
    notoriamente más grande que el texto descriptivo de las tarjetas de
    Guardián (~1.2rem).
17. En el cierre de sección, cambia "Juntos construyen una inteligencia
    digital consciente, crítica, creativa, colaborativa y transformadora."
    de un solo color (verde) a un color distinto por adjetivo: consciente
    (púrpura `#6C63FF`), crítica (cian `#00B4D8`), creativa (verde
    `#00C49A`), colaborativa (rosa `#FF6EB6`), transformadora (naranja
    `#FF7A00`).

## G. Manifiesto
18. Reduce el tamaño del titular "Si una experiencia necesita robarte
    atención para funcionar, debemos rediseñarla." (que hoy usa el tamaño
    global de H2) a `clamp(1.5rem, 2.3vw, 2.05rem)`, para que la columna
    izquierda no domine visualmente frente a la grilla de 6 recuadros de
    principios de la derecha. No cambies el tamaño de H2 en ninguna otra
    sección.

## H. Interacción y microanimaciones (nuevo — v5 no tenía casi ninguna)
19. Botones (`.btn-primary`, `.btn-secondary`): agrega un efecto de relleno
    que se desliza desde la izquierda al hacer hover/focus (fondo oscuro
    `--dark` cubriendo el botón, texto pasa a blanco). Antes eran planos sin
    ningún estado de interacción.
20. Enlaces de texto (tarjetas de Referentes, tarjetas de Evidencia, footer,
    navegación): agrega un subrayado animado que crece de 0% a 100% al hacer
    hover/focus.
21. Tarjetas (`.card`, `.service`, `.evidence-card`, `.reference`, `.case`,
    `.principle`): agrega una elevación leve al hacer hover
    (`translateY(-3px)` a `-4px`) con sombra más intensa.
22. Tarjetas de Guardián: al hacer hover, elevación más notoria
    (`translateY(-6px)`), el borde se intensifica al color territorial
    completo y el resplandor detrás del personaje se intensifica.
23. Todas estas transiciones deben desactivarse completamente bajo
    `prefers-reduced-motion: reduce`. No agregues parallax, auto-scroll ni
    loops — eso sigue prohibido por el Sistema de Diseño.

## I. Accesibilidad (nuevo — v5 no tenía nada de esto)
24. Agrega un skip link "Saltar al contenido" al inicio del `<body>`, visible
    solo al recibir foco de teclado, que enlaza a `#main`.
25. Agrega un estado `:focus-visible` global con contorno visible (azul, 2px,
    offset 3px) en vez de depender solo del outline por defecto del
    navegador.
26. Cambia el comportamiento del formulario de contacto: si hoy usa
    `alert()` al enviarlo, reemplázalo por un mensaje de estado no
    bloqueante en la página (`role="status"`, `aria-live="polite"`) con el
    texto: "Maqueta de demostración: conecta este formulario a un servicio
    real (por ejemplo, Resend) antes de producción." Nunca simules un envío
    exitoso real.

## Verificación final
- `npm run build`, lint y typecheck sin errores.
- Compara visualmente contra `docs/concientic_v10_reference.html` sección por
  sección, incluyendo los estados `:hover`/`:focus` de botones, enlaces y
  tarjetas.
- Revisa responsive en 360/768/1024/1440px, especialmente la sección Equipo
  (grilla de 4 columnas con 8 elementos) y el Hero (diagrama más grande).
- Confirma que el menú de navegación (header y footer) coincide con el nuevo
  orden de secciones.
- Confirma que `prefers-reduced-motion: reduce` desactiva todas las
  transiciones agregadas en la sección H.
- Reporta al finalizar: archivos modificados, resultado de build/lint, y
  cualquier punto de esta lista que ya estuviera aplicado en el repositorio
  (para no duplicar trabajo) o que haya requerido una decisión de tu parte.
