# Plan de migración a Next.js + Vercel

> Nota de estado (2026-09-04): el diseño y contenido ya están validados hasta
> el detalle (ver `docs/concientic_v11_reference.html` y
> `kiro/specs/concientic-web-redesign.md`). Si Kiro ya ejecutó una iteración
> previa de este plan sobre el repositorio, usa
> `prompts/07_ACTUALIZACION_CAMBIOS.md` para aplicar solo los cambios
> pendientes en vez de repetir las fases desde cero.

## Fase 1 — Descubrimiento
- Identificar stack actual.
- Identificar entrypoint.
- Revisar dependencias y configuración de Vercel.
- Ejecutar localmente.

## Fase 2 — Arquitectura
- App Router.
- Layout global.
- Header/Footer (con componente `Logo` claro/oscuro).
- Componentes UI.
- Secciones.
- Contenido tipado.
- Assets en `public/` (incluye `public/brand/` y `public/diagrams/`).

## Fase 3 — Design System
- Tokens.
- Tipografías.
- Botones.
- Cards.
- Badges.
- Evidence cards.
- Guardian cards.
- Quote card (nuevo).
- Diagramas (imágenes finales, no reconstruidas).

## Fase 4 — Contenido
Implementar las secciones del spec v4, en el orden definitivo (Servicios
después de DQUILIBRIO).

## Fase 5 — QA
- Responsive.
- Accesibilidad.
- SEO.
- Performance.
- Reduced motion.
- Links.
- Formularios.

## Fase 6 — Vercel
- Build.
- Variables de entorno.
- Preview deployment.
- Revisión visual.
- Producción.
