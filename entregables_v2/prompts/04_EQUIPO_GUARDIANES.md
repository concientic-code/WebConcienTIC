# Prompt 04 — Equipo: Guardianes de la Inteligencia Digital

Implementa la sección "Equipo" con esta estructura simplificada (cambió
respecto a iteraciones anteriores):

## Estructura de la sección
- **Una sola sección**, fondo `--color-dark` de principio a fin. No uses un
  tono casi negro adicional solo para la grilla de tarjetas — todo el bloque
  comparte el mismo azul oscuro.
- **Un único encabezado**: kicker "Nuestro equipo" + H2 "Guardianes de la
  Inteligencia Digital" + párrafo: "Los Guardianes son los integrantes
  virtuales del equipo ConcienTIC: agentes especializados que educan,
  acompañan, protegen, investigan, conectan e impulsan la innovación." No
  agregues un segundo encabezado ni las cajas de estadística "7 agentes" / "1
  inteligencia colectiva".
- Grilla de **4 columnas en desktop con 8 elementos**: las 7 tarjetas de
  Guardián + 1 tarjeta de cita en la 8ª posición.

## Tarjeta de cita (nuevo elemento)
Texto: "Cada guardián tiene un territorio de competencia y una función real
dentro de las experiencias del Ecosistema ConcienTIC." Debe usar un tamaño de
fuente notoriamente más grande que el texto descriptivo de las tarjetas de
Guardián (no debe leerse como texto secundario/pequeño). Estilo: tarjeta con
borde sutil sobre el fondo oscuro, texto centrado, sin imagen.

## Tarjetas de Guardián
Assets disponibles en `assets/`:
emi.png, locky.png, lex.png, byte.png, detective-dq.png, nexo.png, nova.png.
Todos son PNG con transparencia real. No agregar fondos blancos/cuadriculados.

Datos por Guardián (nombre — rol — competencia — descripción — color):
- Emi — Agente de Empatía Digital — Empatía y bienestar digital — "Acompaña
  conversaciones sobre bienestar, convivencia y relaciones humanas en
  entornos digitales." — #FF6EB6
- Locky — Agente de Seguridad Digital — Seguridad y protección — "Ayuda a
  proteger información, privacidad, identidad y prácticas seguras en línea."
  — #0077FF
- Lex — Agente de Pensamiento Crítico — Pensamiento crítico y ética —
  "Formula preguntas, explora dilemas y ayuda a tomar decisiones digitales
  con criterio." — #FFC857
- Byte — Agente de Alfabetización Digital — Aprendizaje e inteligencia
  digital — "Hace comprensible lo complejo y acompaña el desarrollo de
  capacidades para aprender con tecnología." — #00C49A
- Detective DQ — Agente de Discernimiento Digital — Investigación y
  verificación — "Investiga, contrasta fuentes y ayuda a distinguir
  evidencia, interpretación y desinformación." — #6C63FF
- Nexo — Agente de Conexión Digital — Colaboración y comunidad — "Conecta
  personas, conocimientos y oportunidades para construir soluciones
  colectivas." — #00B4D8
- Nova — Agente de Innovación Digital — Innovación y transformación —
  "Impulsa ideas, experimentación y proyectos que convierten posibilidades
  tecnológicas en impacto." — #FF7A00

Cada tarjeta muestra: imagen, nombre, rol, competencia y descripción.
**Ya no incluyas** la línea "Agente virtual · Equipo ConcienTIC" al pie de la
tarjeta — se eliminó en esta iteración.

## Cierre de sección
"Juntos construyen una inteligencia digital consciente, crítica, creativa,
colaborativa y transformadora." — aplica un color distinto de la paleta a
cada adjetivo (por ejemplo: consciente en púrpura, crítica en cian, creativa
en verde, colaborativa en rosa, transformadora en naranja), no un único color
para toda la frase.

No tratar a los Guardianes como mascotas. Presentarlos como agentes virtuales
especializados. En desktop usar la composición de 4 columnas descrita arriba;
en tablet/móvil pasar a grid responsive (2 o 1 columna). No usar carrusel
automático.
