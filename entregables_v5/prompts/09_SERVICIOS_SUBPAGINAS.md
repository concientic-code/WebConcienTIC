# Prompt 09 — Servicios: subpágina "Contenidos" y tarjetas en construcción

Implementa los cambios de la sección Servicios descritos en
`kiro/specs/concientic-web-redesign.md` (§11).

## 1. Copiar la subpágina "Contenidos" tal cual
Copia `assets/servicios-subpaginas/contenidos.html` sin modificarlo a
`public/servicios/contenidos.html`. Es un diseño ya aprobado y autocontenido
(catálogo filtrable, buscador, sección Academia ConcienTIC marcada
"Próximamente", cierre con el ciclo DQUILIBRIO). No lo reescribas como
componente React ni le cambies nada — cualquier ajuste requiere confirmación
explícita antes de aplicarse.

Nota: esta subpágina ya trae su propio header con enlaces funcionales a
`https://www.concientic.com/` y a las anclas del sitio — no necesita nada
adicional para "volver". Antes de publicar, confirma si el dominio de
producción real es `concientic.com` o `concientic.vercel.app` y ajusta esos
enlaces del header **solo si te lo confirman explícitamente** (no lo hagas
por tu cuenta).

## 2. Las 5 tarjetas de Servicios cambian así
```html
<div class="service-grid">
  <a class="service" href="/servicios/contenidos.html" target="_blank" rel="noopener noreferrer" aria-label="Abrir Contenidos, la biblioteca de Competencias Digitales, en una pestaña nueva">
    <b>Competencias Digitales</b>
    <p>Rutas para desarrollar capacidades esenciales y transferibles.</p>
    <span class="tag">Aprendizaje</span>
  </a>
  <article class="service">
    <b>IA consciente</b>
    <p>Comprender, experimentar y adoptar IA con criterio humano.</p>
    <span class="tag">Inteligencia</span>
  </article>
  <article class="service disabled" aria-disabled="true">
    <span class="soon">En construcción</span>
    <b>Desinfoxicación</b>
    <p>Herramientas para navegar abundancia, fuentes y desinformación.</p>
    <span class="tag">Discernimiento</span>
  </article>
  <article class="service disabled" aria-disabled="true">
    <span class="soon">En construcción</span>
    <b>Transformación cultural</b>
    <p>Prácticas para integrar tecnología sin perder autonomía.</p>
    <span class="tag">Organizaciones</span>
  </article>
  <a class="service anchor" href="#dquilibrio" aria-label="Ir a la sección DQUILIBRIO de este sitio">
    <b>DQUILIBRIO</b>
    <p>Experiencias para recuperar atención, criterio y capacidad de elección.</p>
    <span class="tag">Equilibrio</span>
  </a>
</div>
```

Importante:
- La tarjeta **IA consciente** no cambia de nada — sigue como `<article>`
  de texto plano, sin enlace ni etiqueta. No es "en construcción" (eso es
  solo para las tarjetas 3 y 4): es un desarrollo activo que todavía no
  tiene su HTML de subpágina ("Laboratorios"). Cuando llegue ese archivo se
  actualizará igual que se hizo con "Contenidos".
- Las tarjetas deshabilitadas conservan su texto original (título,
  descripción, tag) — solo cambia el estilo visual y se agrega la etiqueta.

## 3. Estilos nuevos para el componente `Service`/`.service`
- `.service.disabled`: fondo gris (`#F1F3F5`), borde discontinuo, sin
  elevación ni sombra al hover, `cursor: not-allowed`. El título, texto y
  tag bajan a color `--muted`.
- `.service .soon` (la etiqueta "En construcción"): píldora con fondo
  `--muted` y texto blanco, antes del título.
- `a.service` (tarjetas 1 y 5): mismo aspecto visual que `.service`, con un
  afordance de texto que aparece solo al hover/focus: "Abrir →" en la
  tarjeta 1 (abre algo nuevo), "Ver ↓" en la tarjeta 5 (navega dentro de la
  misma página — usa la clase modificadora `anchor` para diferenciarlo).

## 4. Verificación
- La tarjeta "Competencias Digitales" abre `/servicios/contenidos.html` en
  una pestaña nueva; el archivo es idéntico byte a byte al entregado.
- La tarjeta "DQUILIBRIO" hace scroll a `#dquilibrio` en la misma pestaña
  (sin `target="_blank"`).
- Las tarjetas "Desinfoxicación" y "Transformación cultural" no reaccionan
  al clic ni al hover más allá de su estado visual gris, y no son
  alcanzables por teclado como elementos interactivos (siguen siendo
  `<article>`, no `<a>` ni `<button>`).
- La tarjeta "IA consciente" se ve exactamente igual que antes de este
  cambio.
- Responsive: la grilla de 5 columnas sigue funcionando igual en
  768/1024/1440px con la mezcla de tarjetas interactivas y deshabilitadas.
- `prefers-reduced-motion` sigue desactivando las transiciones de hover en
  las tarjetas activas.
