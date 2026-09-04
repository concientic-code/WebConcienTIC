# ConcienTIC — Entregables para Kiro + Next.js + Vercel (v3)

Fecha: 2026-09-04

## Qué contiene esta versión del paquete
Este paquete reemplaza a los entregados el 2026-09-03 y a una primera
actualización parcial del 2026-09-04. Esta vez el spec y los prompts cubren
**todo** el recorrido de diseño, desde el prototipo original
(`concientic_v5_reference.html`) hasta el estado final vigente
(`concientic_v10_reference.html`) — no solo el último ajuste puntual. Si tu
repositorio en Kiro quedó en cualquier punto intermedio de esa evolución,
`prompts/07_ACTUALIZACION_CAMBIOS.md` lo cubre igual.

## Changelog completo (v5 → v10)

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
Migrar y reconstruir el sitio `https://concientic.vercel.app/` como una
aplicación Next.js moderna, manteniendo la arquitectura conceptual de
ConcienTIC y aplicando el Manual de Marca v2.0, el Sistema de Diseño Web v1.0
y todos los ajustes descritos arriba.

## Fuente visual de referencia
`docs/concientic_v10_reference.html` es el prototipo visual aprobado y
vigente (`concientic_v5_reference.html` se conserva solo como histórico, para
poder entender el "antes" de cada cambio). No debe copiarse como arquitectura
final: debe convertirse en componentes Next.js reutilizables.

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

## Cómo ejecutar esto en Kiro

**Si el repositorio ya tiene una versión de ConcienTIC implementada** (de
cualquier iteración anterior, aunque sea la basada en v5): pega directamente
`prompts/07_ACTUALIZACION_CAMBIOS.md`. Cubre todo el recorrido v5→v10; Kiro
puede saltarse los puntos que ya estén aplicados.

**Si es una construcción nueva o el repositorio solo tiene placeholders**:
1. Ejecutar Prompt 00 — Auditoría.
2. Instalar/usar los steering files de `kiro/steering/` y `AGENTS.md`.
3. Ejecutar Prompt 01 — Base Next.js y arquitectura.
4. Ejecutar Prompt 02 — Design System y componentes (incluye patrones de
   interacción y accesibilidad).
5. Ejecutar Prompt 03 — Construcción de páginas/secciones (orden final).
6. Ejecutar Prompt 04 — Equipo / Guardianes (estructura simplificada).
7. Ejecutar Prompt 05 — QA, accesibilidad, performance y Vercel.
8. Ejecutar Prompt 06 — Revisión visual contra `concientic_v10_reference.html`.

También puedes pegar `prompts/MASTER_KIRO.md` directamente: incluye el
contexto completo y decide internamente si debe reconstruir o solo aplicar el
Prompt 07.

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
