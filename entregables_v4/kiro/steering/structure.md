---
inclusion: always
---
# Estructura objetivo

Preferir una estructura equivalente a:

- `app/`
  - `layout.tsx`
  - `page.tsx`
  - `globals.css`
  - rutas legales si existen
- `components/`
  - `layout/` (Header con `Logo`, Footer)
  - `sections/` (Hero, Dquilibrio, Servicios, Desafio, Desinfoxicacion,
    Metodologia, Evidencia, Equipo, Casos, Referentes, Manifiesto, Contacto)
  - `ui/` (Button, Card, Badge, SectionHeader, QuoteCard)
  - `guardians/` (GuardianCard, datos tipados)
- `content/`
- `lib/`
- `public/`
  - `brand/` (`concientic-nexus-wordmark-fondo-claro.png`,
    `concientic-nexus-wordmark-fondo-oscuro.png`, `logo-concientic.png`)
  - `guardians/` (los 7 PNG transparentes)
  - `diagrams/` (`equilibrio-concientic-mejorado.png`,
    `ciclo-dquilibrio-mejorado.png`)
  - `dquilibrio/` (las 4 subpáginas estáticas: `atencion.html`,
    `informacion.html`, `discernimiento.html`, `autonomia.html` — copiadas
    tal cual desde `assets/dquilibrio-subpaginas/`, servidas directamente
    por Next.js sin pasar por `app/`)
  - `icons/`
- `.kiro/steering/`
- `.kiro/specs/`

No es obligatorio usar exactamente esta estructura si el repositorio existente
tiene una convención mejor; documentar cualquier desviación.
