# Prompt 10 — Rediseño completo de la página principal (v12 → v13)

Usa este prompt cuando el repositorio ya tenga implementada la página
principal según `docs/concientic_v12_reference.html` (es decir, ya aplicaste
`03_IMPLEMENTACION.md` y, si corresponde, `07_ACTUALIZACION_CAMBIOS.md`,
`08_SUBPAGINAS_DQUILIBRIO.md` y `09_SERVICIOS_SUBPAGINAS.md`). Este prompt
**no es un ajuste puntual**: reemplaza la arquitectura de información
completa de la página principal por la de `docs/concientic_v13_reference.html`.
Antes de tocar código, lee `kiro/specs/concientic-web-redesign.md` §14
completa — ahí está el detalle exacto de cada sección con su copy literal.

No toques: las subpáginas de DQUILIBRIO (`assets/dquilibrio-subpaginas/`) ni
la subpágina de Servicios "Contenidos" (`assets/servicios-subpaginas/`) — su
contenido no cambia, solo cambia desde dónde se enlazan en la nueva home.

## A. Dominio
1. Actualiza toda referencia de dominio en metadata, `sitemap`, `robots`,
   Open Graph y enlaces absolutos a `https://www.concientic.com` (confirmado
   por el propio archivo v13, que ya usa ese dominio en sus enlaces
   absolutos). Si el proyecto en Vercel sigue usando `concientic.vercel.app`
   como alias, puede conservarse como alias secundario, pero el dominio
   canónico pasa a ser `concientic.com`.

## B. Eliminar secciones (con confirmación antes de borrar contenido)
2. Antes de borrar código, pregúntale a Jeimy si el contenido de "El
   desafío", "Desinfoxicación", "Centro de Evidencia", "Casos" y
   "Referentes" se descarta definitivamente o se reubica (spec §14.1). Si no
   hay respuesta todavía, comenta el código de esas secciones en vez de
   borrarlo (o muévelo a un archivo `_archivo-v12-secciones-removidas.tsx`),
   para no perder el trabajo ya hecho mientras se confirma.
3. Elimina de la navegación (header y footer) los enlaces a `#desafio`,
   `#desinfoxicacion`, `#servicios`, `#evidencia`, `#casos`, `#referentes`.
4. Elimina el bloque de 5 tarjetas de Servicios (`id="servicios"`) de la
   página principal — su único enlace que seguía siendo necesario
   (Contenidos) se recrea en la nueva sección Recursos (punto F). El enlace
   ancla a DQUILIBRIO ya no hace falta porque DQUILIBRIO queda en el menú
   principal.
5. Elimina la banda de principio ("No queremos más tiempo de tu vida...") y
   el Manifiesto de cierre sin ancla, si existían como secciones propias.

## C. Nuevo menú (header y footer)
6. Implementa el menú en este orden exacto: Ecosistema (`#ecosistema`) ·
   Guardianes (`#guardianes`) · Aprende (`#recursos`) · Metodología
   (`#metodologia`) · DQUILIBRIO (`#dquilibrio`) · botón-CTA "Encuentra tu
   ruta ↗" (`#experiencia`). El footer repite los primeros 5, sin el CTA.

## D. Hero — copy (reemplaza el copy vigente, spec §14.3)
7. Reemplaza el copy del Hero con el texto literal de §14.3: etiqueta
   "Aprende con intención. Aplica con criterio.", titular "La inteligencia
   digital empieza contigo.", cuerpo sobre reconocer lo que importa, dos CTA
   ("Descubre tu siguiente paso ↗" → `#experiencia`, "Conoce nuestra
   metodología" → `#metodologia`), frase de cierre "Menos ruido. Más
   criterio. Aprendizaje que se convierte en acción."

## E. Nueva sección Ecosistema (spec §14.4)
8. Crea la sección `id="ecosistema"` con las 3 tarjetas (DQnexus, TutorIA,
   Laboratorios IA) con el copy literal de §14.4, incluida la nota de
   honestidad al pie ("La disponibilidad y el alcance de cada producto...")
   — no resumirla ni quitarla, es una regla de contenido, no decorativa.

## F. Guardianes — reemplazo de la sección Equipo (spec §14.5)
9. Reemplaza la grilla de 7 tarjetas de Equipo (con foto/rol/bio individual)
   por la franja única `id="guardianes"` descrita en §14.5: encabezado,
   cuerpo, una imagen compuesta de los 7 Guardianes juntos (compónla con los
   7 PNG ya existentes en `assets/` si no hay un archivo de grupo nuevo),
   lista de las 7 competencias con su glifo, y la frase de cierre.
10. Pregunta explícitamente a Jeimy (no asumas) si esto reemplaza
    definitivamente la sección Equipo de v12 o si esa versión con bios debe
    vivir en otra página.

## G. Nueva sección Aprende/Recursos (spec §14.6)
11. Crea la sección `id="recursos"` con las 3 tarjetas de §14.6. La primera
    tarjeta reemplaza al enlace que antes vivía en Servicios: debe abrir
    `https://www.concientic.com/servicios/contenidos` en pestaña nueva
    (`target="_blank" rel="noopener noreferrer"`), sirviendo el contenido ya
    existente de `assets/servicios-subpaginas/contenidos.html` sin alterarlo.
12. La segunda tarjeta (Academia ConcienTIC) enlaza a Hotmart — **no
    publiques el placeholder `https://hotmart.com/` tal cual**; pide a Jeimy
    la URL real del curso/academia en Hotmart antes de publicar.

## H. Logo del header (spec §14.7 — requiere confirmación)
13. El archivo v13 usa un lockup de texto en CSS en vez de la imagen del
    wordmark. **No implementes este cambio todavía.** Mantén el wordmark de
    imagen ya vigente (`concientic-nexus-wordmark-transparente-fondo-*.png`)
    sobre la nueva estructura de header/menú, y pregunta a Jeimy si el
    cambio a logo de texto es intencional antes de aplicarlo.

## I. Nueva sección Experiencia (spec §14.8)
14. Crea la sección `id="experiencia"` como un componente de cliente: una
    pregunta con 4 opciones y una recomendación simple por opción (texto
    estático, sin backend ni persistencia). Debe mostrar siempre, sin
    posibilidad de ocultarlo, el aviso "No es el diagnóstico oficial DQnexus
    ni guarda respuestas..." — es una regla de contenido (no prometer una
    evaluación real que no existe), igual que la regla ya vigente para
    Casos/Evidencia.

## J. Contacto (spec §14.9)
15. Actualiza el encabezado y CTA de la sección de contacto con el copy
    literal de §14.9. El formulario de contacto en sí (campos, envío,
    mensaje de estado accesible) no cambia.

## K. Desviaciones de marca — NO corregir sin confirmación (spec §14.10)
16. El archivo v13 trae 4 diferencias frente al Manual de Marca v2.0: hex de
    `--navy` (`#0D182A` vs. `#0D1B2A` oficial), hex de `--pink` (`#FF68B4`
    vs. `#FF6EB6` oficial), `--paper` (`#f5f7f3` vs. `#F5F7F9` oficial), y
    ausencia total de Poppins (todo el texto usa Inter, incluidos
    titulares). Implementa con los valores OFICIALES del Manual de Marca
    (no los del archivo v13) mientras Jeimy no confirme que el cambio es
    intencional, y deja la pregunta anotada para `06_REVISION_VISUAL.md`.

## L. Accesibilidad — no se pierde nada de lo ya exigido (spec §14.11)
17. El archivo v13 no incluye skip link. Impleméntalo igual — sigue siendo
    un requisito del Design System v1.0, independiente del archivo de
    referencia de esta sección.
18. Verifica que se mantengan `:focus-visible` global, `aria-live` en
    mensajes de estado y `prefers-reduced-motion` en toda animación nueva de
    esta sección (en particular el componente de Experiencia).

## Verificación final
- `npm run build` limpio.
- Navegación, orden de secciones y copy coinciden con spec §14.1-§14.9.
- Ningún enlace absoluto usa `concientic.vercel.app`; todos usan
  `https://www.concientic.com`.
- Las 4 subpáginas de DQUILIBRIO y la subpágina "Contenidos" siguen
  funcionando exactamente igual que antes, solo cambia desde qué sección de
  la home se enlazan.
- Lista aparte, para revisar con Jeimy antes de publicar: (1) destino del
  contenido eliminado (desafío/desinfoxicación/evidencia/casos/referentes),
  (2) sección Equipo con bios — ¿se conserva en otra página?, (3) URL real
  de Hotmart, (4) logo imagen vs. logo texto en el header, (5) las 4
  desviaciones de paleta/tipografía del punto K.
