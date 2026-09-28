# Prompt 08 — Subpáginas DQUILIBRIO (Atención, Información, Discernimiento, Autonomía)

Implementa la nueva funcionalidad de subpáginas para la sección DQUILIBRIO,
descrita en detalle en `kiro/specs/concientic-web-redesign.md` (§10).

## 1. Copiar los 4 archivos tal cual
Copia estos 4 archivos exactamente como están, sin modificar su HTML, CSS ni
JS interno, a `public/dquilibrio/`:
- `assets/dquilibrio-subpaginas/atencion.html`
- `assets/dquilibrio-subpaginas/informacion.html`
- `assets/dquilibrio-subpaginas/discernimiento.html`
- `assets/dquilibrio-subpaginas/autonomia.html`

Son diseños ya aprobados y autocontenidos (incluyen su propio `<html>`,
`<style>` y `<script>`, con imágenes en base64). **No los reescribas como
componentes React, no los "optimices" ni les cambies nada** — trátalos como
un asset estático, igual que un PDF o una imagen. Cualquier ajuste a su
contenido requiere confirmación explícita antes de aplicarse.

Next.js sirve cualquier archivo dentro de `public/` directamente por su
ruta, así que no hace falta crear rutas ni páginas para esto: con copiar los
4 archivos ya quedan disponibles en `/dquilibrio/atencion.html`,
`/dquilibrio/informacion.html`, `/dquilibrio/discernimiento.html` y
`/dquilibrio/autonomia.html`.

## 2. Convertir las 4 tarjetas de DQUILIBRIO en enlaces
En la sección `#dquilibrio`, cada una de las 4 tarjetas (`.card`) pasa de ser
un `<article>` a un `<a>` que abre la subpágina correspondiente en una
pestaña nueva:

```html
<a class="card" href="/dquilibrio/atencion.html" target="_blank" rel="noopener noreferrer" aria-label="Abrir la experiencia Recuperar presencia en una pestaña nueva">
  <div class="num">01 · Atención</div>
  <h3>Recuperar presencia</h3>
  <p>Reconocer que la atención es limitada y diseñar experiencias que la respeten.</p>
</a>
```

Repite el patrón para las otras 3 (Información→informacion.html,
Criterio→discernimiento.html, Autonomía→autonomia.html), conservando el
texto exacto que ya tiene cada tarjeta.

Ese `target="_blank"` es intencional y es la respuesta a "cómo regresa el
usuario al sitio": al abrirse en una pestaña nueva, la pestaña original del
sitio queda abierta detrás, así que volver es tan simple como cambiar de
pestaña o cerrar la nueva. Por eso **no se agrega ningún botón o enlace de
"volver" dentro de las 4 subpáginas** — eso implicaría tocar su contenido, lo
cual está fuera de alcance de este prompt (ver punto 1).

## 3. Estilo del enlace
El componente `Card`/`.card` no debe cambiar de aspecto visual al volverse
clicable (mismo fondo, borde, padding y elevación al hover que ya tiene). Sí
agrega, solo visible al hover/focus, un texto discreto "Abrir →" en la
esquina inferior derecha con el color primario, como el que ya existe en la
sección Referentes ("Visitar referente ↗"). Este afordance debe respetar
`prefers-reduced-motion`.

## 4. Verificación
- Cada una de las 4 tarjetas abre su subpágina correspondiente en una pestaña
  nueva (verificar con clic normal y con clic central/cmd+clic).
- Las subpáginas cargan igual que los archivos originales entregados: sin
  errores de consola, sin imágenes rotas, con su experiencia interactiva
  funcionando (temporizador, curador, verificador, diseñador de decisión,
  según corresponda).
- Los 4 archivos en `public/dquilibrio/` son idénticos byte a byte a los
  entregados en `assets/dquilibrio-subpaginas/` (no reescritos).
- Accesibilidad: cada tarjeta-enlace tiene `aria-label` que indica que abre
  en una pestaña nueva; focus visible al tabular hasta la tarjeta.
- No se modificó nada dentro de las 4 subpáginas, incluido el logo (que
  todavía usa el isotipo original — ver nota en el spec §10, es una
  inconsistencia conocida y aceptada por ahora, no la corrijas sin
  confirmación).
