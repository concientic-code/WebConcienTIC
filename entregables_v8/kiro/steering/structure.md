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
  - `sections/` — vigente desde v13 (ver `kiro/specs/concientic-web-redesign.md`
    §14): `Hero`, `Ecosistema`, `Guardianes` (franja única, ya no grilla de
    7 tarjetas), `Recursos`, `Metodologia`, `Experiencia` (demo cliente),
    `Dquilibrio`, `Contacto`. Las secciones de v12 (`Servicios`, `Desafio`,
    `Desinfoxicacion`, `Evidencia`, `Casos`, `Referentes`, `Manifiesto`)
    quedan pendientes de confirmación de destino — no borrar sus archivos
    todavía, ver spec §14.1.
  - `ui/` (Button, Card, Badge, SectionHeader, QuoteCard)
  - `guardians/` (datos tipados; `GuardianCard` individual ya no se usa en
    la home desde v13, solo en la franja de grupo — conservar el
    componente por si se reutiliza en otra página)
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
    por Next.js sin pasar por `app/`, accesibles en producción como
    `https://www.concientic.com/dquilibrio/*.html`)
  - `servicios/` (la subpágina estática `contenidos.html` — copiada tal cual
    desde `assets/servicios-subpaginas/`, accesible en producción como
    `https://www.concientic.com/servicios/contenidos`)
  - `ecosistema/` (la subpágina estática `laboratoriosia.html` — copiada
    tal cual desde `assets/ecosistema-subpaginas/`, con el menú ya
    actualizado al de la home; accesible en producción como
    `https://www.concientic.com/ecosistema/laboratoriosia`, ruta
    propuesta a confirmar con Jeimy — ver spec §16)
  - `icons/`
- `.kiro/steering/`
- `.kiro/specs/`

No es obligatorio usar exactamente esta estructura si el repositorio existente
tiene una convención mejor; documentar cualquier desviación.
