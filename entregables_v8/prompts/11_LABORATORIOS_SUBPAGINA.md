# Prompt 11 — Subpágina "Laboratorios IA" + nueva regla de menú para subpáginas

Usa este prompt después de que la página principal ya esté en el estado
v13 (`prompts/10_REDISENIO_HOME_V13.md` aplicado). Lee
`kiro/specs/concientic-web-redesign.md` §16 antes de tocar código.

## A. Regla nueva y transversal (aplica a esta subpágina ya; a las demás, con confirmación)
1. Jeimy pidió que **todas las subpáginas usen el mismo menú de la página
   central**, no un menú propio por subpágina. En el archivo entregado
   para "Laboratorios IA" ya se sustituyó su header/nav y su footer por el
   menú vigente de la home (Ecosistema · Guardianes · Aprende ·
   Metodología · DQUILIBRIO · CTA "Encuentra tu ruta ↗"), con enlaces
   absolutos `https://www.concientic.com/#<id>` — está en
   `assets/ecosistema-subpaginas/laboratoriosia.html`, listo para copiar
   tal cual.
2. **No actualices todavía** el menú de las 4 subpáginas de DQUILIBRIO ni
   de "Contenidos" — fueron entregadas antes de esta regla y la política
   del proyecto es no modificarlas sin confirmación explícita. Pregunta a
   Jeimy si quiere que también se les aplique el nuevo menú antes de
   tocarlas.

## B. Publicar la subpágina
3. Copia `assets/ecosistema-subpaginas/laboratoriosia.html` tal cual (sin
   reescribir su contenido, solo ya tiene el menú corregido) a
   `public/ecosistema/laboratoriosia.html`, servida en
   `https://www.concientic.com/ecosistema/laboratoriosia`. Si Jeimy
   confirma otra ruta, usa esa en su lugar — no es una decisión final
   todavía.

## C. Conectar con la home (Ecosistema)
4. En la sección Ecosistema de la home (`id="ecosistema"`, spec §14.4), la
   tarjeta "03 · Experimentación y aplicación — Laboratorios IA" enlaza
   hoy a `#contacto`. Cámbialo para que abra la subpágina en pestaña nueva:
   `target="_blank" rel="noopener noreferrer"` hacia
   `https://www.concientic.com/ecosistema/laboratoriosia`.

## D. No fingir enlaces que no existen
5. Los 4 enlaces de artefacto dentro de la subpágina (SIGINEX,
   EmprendeCreativo, DQ-Nexus, TutorIA) están vacíos en
   `ARTIFACT_URLS` dentro del propio HTML — su clic muestra un aviso
   "pendiente de configurar". **No inventes URLs para completarlos.**
   Déjalos así hasta que Jeimy entregue cada artefacto real.
6. Los 4 `logo-slot` muestran un ícono de línea genérico y el texto "Logo
   oficial por incorporar" — no sustituyas por logos reales de terceros
   sin que Jeimy los entregue (misma regla ya aplicada a los proveedores
   de la subpágina "Contenidos").

## E. Paleta
7. El archivo reutiliza los mismos tokens de v13 (incluida la ausencia de
   Poppins y las variantes de `--pink`/`--paper` ya señaladas en spec
   §14.10). Implementa con los valores oficiales del Manual de Marca hasta
   que Jeimy confirme lo contrario — misma pauta que el resto del sitio.

## Verificación final
- La subpágina abre con el menú de la home, no con su menú original.
- El resto de su contenido (hero, 4 laboratorios, "Nuestro enfoque", CTA
  final) es idéntico al archivo entregado.
- La tarjeta "Laboratorios IA" de Ecosistema en la home enlaza a la
  subpágina en pestaña nueva.
- Ningún enlace de artefacto ni logo de proveedor fue inventado.
- Pendiente de confirmar con Jeimy: ruta final de la subpágina, y si las 5
  subpáginas anteriores deben actualizar su menú también.
