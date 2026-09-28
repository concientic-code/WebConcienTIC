# Prompt 05 — QA, accesibilidad, performance y Vercel

Haz una auditoría final del sitio ConcienTIC.

Checklist general:
- `npm run lint` o equivalente.
- `npm run typecheck` si existe.
- `npm run build`.
- Revisar consola del navegador.
- Revisar imágenes y tamaños (incluye los dos wordmarks del logo y las dos
  ilustraciones DQUILIBRIO en `public/diagrams/`).
- Confirmar que logo y Guardianes usan archivos locales transparentes.
- Confirmar que no existe ninguna imagen base64 en producción.
- Revisar alt text.
- Revisar headings y landmarks.
- Revisar keyboard navigation y visible focus.
- Revisar reduced motion.
- Revisar responsive 360/768/1024/1440.
- Revisar SEO title, description, canonical si aplica y Open Graph.
- Revisar enlaces externos.
- Revisar que no haya placeholders visibles.
- Revisar que el formulario no prometa un envío real si no existe backend.
- Revisar que no haya infinite scroll, autoplay, streaks, rankings, FOMO o
  dark patterns.

Checklist específico de esta iteración:
- El logo del header es legible: se distingue "NEXUS" y el tagline, no solo
  "ConcienTIC".
- El orden de secciones y del menú (header y footer) coincide con
  `kiro/specs/concientic-web-redesign.md` — en particular, Servicios aparece
  antes de El desafío.
- La sección Equipo es un solo bloque de fondo oscuro, sin las dos cajas de
  estadística, sin segundo encabezado, con la tarjeta de cita dentro de la
  grilla de 8 elementos y sin la línea "Agente virtual · Equipo ConcienTIC".
- El titular del Manifiesto no ocupa más espacio visual que la grilla de
  principios de al lado.
- Botones, enlaces y tarjetas muestran los estados de hover/focus definidos
  en `design-system.md` (relleno deslizante en botones, subrayado animado en
  enlaces, elevación en tarjetas), y todos se desactivan bajo
  `prefers-reduced-motion`.
- Existe skip link funcional al inicio del `<body>` y `:focus-visible` visible
  en todos los elementos interactivos.
- El formulario de contacto muestra un mensaje de estado accesible
  (`aria-live="polite"`) en vez de un `alert()` del navegador.

Después valida la configuración para Vercel. No agregues secretos al
repositorio. Si el formulario necesita una variable de entorno, crea
`.env.example` y documenta su uso.

Entrega un reporte final con errores encontrados, correcciones realizadas y
estado del build/deployment.
