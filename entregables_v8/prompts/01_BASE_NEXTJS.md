# Prompt 01 — Base técnica y arquitectura Next.js

Implementa la base del nuevo sitio ConcienTIC en Next.js + TypeScript usando
App Router, respetando la arquitectura existente si ya es compatible.

Objetivos:
- Mantener el deployment en Vercel.
- Crear una arquitectura de componentes limpia (ver `.kiro/steering/structure.md`).
- Crear design tokens globales (`reference-code/styles/design-tokens.css` como
  base).
- Separar contenido, componentes y assets.
- Configurar metadata SEO básica.
- Incorporar los assets entregados desde `assets/` a `public/`, incluyendo las
  subcarpetas nuevas: `public/brand/` (wordmark claro/oscuro + isotipo) y
  `public/diagrams/` (las dos ilustraciones DQUILIBRIO).

No diseñes todavía cada sección en detalle. Primero deja funcionando una shell
con Header (con el componente `Logo`), Main y Footer, más tokens y componentes
base.

Al finalizar ejecuta lint/typecheck/build y reporta exactamente qué quedó
listo.
