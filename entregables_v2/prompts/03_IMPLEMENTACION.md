# Prompt 03 — Implementar el sitio completo

Construye las secciones del sitio ConcienTIC utilizando exclusivamente los
componentes del Design System, **en este orden exacto** (cambió respecto a
iteraciones anteriores: Servicios ahora va después de DQUILIBRIO, no después
de Desinfoxicación):

1. Hero — "Aprender tecnología. Sin perder humanidad." Lead: "ConcienTIC
   desarrolla Inteligencia Digital mientras ayuda a personas y organizaciones
   a construir una relación consciente, autónoma y equilibrada con la
   tecnología." Visual: `assets/diagrams/equilibrio-concientic-mejorado.png`
   como imagen estática, tamaño generoso (ancho máx. ≈600px en desktop).
2. Banda de principio — "No queremos más tiempo de tu vida..."
3. DQUILIBRIO.
4. **Servicios** (posición nueva — inmediatamente después de DQUILIBRIO).
5. El desafío.
6. Desinfoxicación.
7. Metodología — usar `assets/diagrams/ciclo-dquilibrio-mejorado.png` como
   imagen estática (no reconstruir en SVG).
8. Centro de Evidencia.
9. Equipo (ver `prompts/04_EQUIPO_GUARDIANES.md` para la estructura completa).
10. Casos.
11. Referentes.
12. Manifiesto — el titular debe usar un tamaño de fuente reducido respecto al
    resto de H2 del sitio, de forma que la columna de texto ocupe un espacio
    visual similar al de la grilla de 6 recuadros de principios de al lado
    (no debe dominarla visualmente).
13. Contacto.
14. Footer.

El menú de navegación (header y footer) debe reflejar este mismo orden.

Usa contenido de los steering files y el HTML de referencia
(`docs/concientic_v10_reference.html`) como base. No copies estilos
monolíticos ni incrustes base64.

La metodología debe verse como un ciclo (ya resuelto en la imagen
proporcionada), no como una lista vertical numerada.

En Referentes enlaza solo a fuentes oficiales cuando corresponda.

En Casos no inventes clientes ni resultados.

Aplica en toda la página los estados de hover/focus de botones, enlaces y
tarjetas definidos en `.kiro/steering/design-system.md`, el skip link inicial
y el `:focus-visible` global.

Al finalizar, prueba todos los anchors, los estados responsive, y los estados
`:hover`/`:focus` de botones, enlaces y tarjetas.
