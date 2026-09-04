---
inclusion: always
---
# Sistema de Diseño ConcienTIC

## Color
- `--color-primary: #00C49A`
- `--color-secondary: #6C63FF`
- `--color-tech-blue: #0077FF`
- `--color-future-cyan: #00B4D8`
- `--color-dark: #0D1B2A`
- `--color-innovation: #FF7A00`
- `--color-yellow: #FFC857`
- `--color-pink: #FF6EB6`
- `--color-surface: #FFFFFF`
- `--color-soft: #F5F7F9`
- `--color-muted: #64748B`
- `--color-text: #1E293B`

## Tipografía
Poppins para marca, títulos y expresiones de identidad. Inter para UI,
navegación y texto de lectura.

## Logo (componente `Logo`)
Construir un componente `<Logo variant="light" | "dark" />` (o que reciba el
fondo de la sección y resuelva la variante automáticamente):
- `variant="light"` → `public/brand/concientic-nexus-wordmark-fondo-claro.png`
  (texto oscuro, para usar sobre `--surface`/`--soft`/blanco).
- `variant="dark"` → `public/brand/concientic-nexus-wordmark-fondo-oscuro.png`
  (texto claro, para usar sobre `--color-dark` o cualquier fondo oscuro).
- El isotipo (`logo-concientic.png`, el árbol/cerebro) se usa solo para
  favicon y aplicaciones muy pequeñas donde no cabe el wordmark completo.
- Tamaño mínimo del wordmark en header: debe permitirse leer "NEXUS" y el
  tagline "Conciencia Digital para un mundo mejor." — no reducir por debajo
  de ~52-58px de alto en desktop.

## Ilustraciones DQUILIBRIO
Dos piezas gráficas ya diseñadas y aprobadas, entregadas como PNG con
transparencia en `assets/diagrams/`:
- `equilibrio-concientic-mejorado.png` — visual del Hero (Atención, IA+Tech,
  Criterio, Autonomía, Humanidad alrededor del centro DQUILIBRIO).
- `ciclo-dquilibrio-mejorado.png` — diagrama de la Metodología (ciclo
  DETENER→OBSERVAR→DISCERNIR→ELEGIR→EQUILIBRAR).

Estas imágenes se usan tal cual, vía `next/image`, optimizadas a WebP si el
pipeline de build lo permite. No se reconstruyen como SVG/CSS a mano salvo que
una futura iteración lo pida explícitamente — son el diseño final, no un
placeholder.

## Componentes
Construir botones, cards, section headers, badges, navegación, footer,
guardian cards, quote card (para "Cada guardián tiene un territorio...") y
patrones de evidencia como componentes reutilizables.

## Movimiento
Patrones de interacción definidos (todos son "hover discreto" / "transición
de estado", permitidos por el Sistema de Diseño):
- **Botones**: relleno oscuro (`--color-dark`) que se desliza desde la
  izquierda al hacer hover/focus, cubriendo el botón; el texto cambia a
  blanco.
- **Enlaces de texto** (referentes, evidencia, footer, navegación):
  subrayado animado que crece de 0% a 100% de ancho al hacer hover/focus.
- **Tarjetas genéricas** (card, service, evidence-card, reference, case,
  principle): elevación leve (`translateY(-3px)` a `-4px`) + sombra más
  intensa al hacer hover.
- **Tarjetas de Guardián**: elevación más notoria (`translateY(-6px)`),
  borde que se intensifica al color territorial completo, y resplandor
  detrás del personaje que se intensifica.

No usar parallax continuo, auto-scroll, loops infinitos ni animación para
provocar permanencia o urgencia. Todas las transiciones anteriores deben
desactivarse por completo bajo `prefers-reduced-motion: reduce`.

## Accesibilidad
Contraste AA como mínimo, foco visible (`:focus-visible` con contorno azul,
2px, offset 3px — no depender solo del outline por defecto del navegador),
navegación por teclado, textos alternativos y jerarquía semántica correcta.
Además:
- Skip link "Saltar al contenido" al inicio del `<body>`, visible solo al
  recibir foco de teclado, enlazando a `#main`.
- El formulario de contacto debe comunicar su estado (éxito/error/demo) con
  un mensaje en la página (`role="status"`, `aria-live="polite"`), nunca con
  un `alert()` del navegador ni simulando un envío exitoso que no ocurrió.
