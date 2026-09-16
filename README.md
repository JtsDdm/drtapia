# Landing "Micro-Odontología" — Swiss Dental / Dr. Arturo Ramírez Tapia

Landing de una sola oferta. Tráfico 100% pagado desde Meta Ads.
Conversión = clic al botón de WhatsApp. Sin formularios, sin menú, sin ofertas compitiendo.

## Archivos
- `index.html` — la landing completa (HTML + CSS + JS en un solo archivo)
- `logo-swiss-dental.svg` — logo oficial descargado de drarturotapia.com

## ⚠️ Antes de publicar — 3 reemplazos obligatorios

| Variable | Dónde | Qué poner |
|---|---|---|
| `{{WHATSAPP_NUMBER}}` | `index.html` línea ~791 (bloque CONFIGURACIÓN) | Número nuevo en formato internacional **sin `+` ni espacios**, ej. `5212461234567` |
| `{{META_PIXEL_ID}}` | 3 ocurrencias, bloque META PIXEL | ID del pixel de Meta |
| `{{CEDULA_PROFESIONAL}}` | footer legal | Número exacto de cédula del doctor |

El número de WhatsApp está en **un solo lugar** — lo toman automáticamente los 7 CTAs de la página.

## Paleta (extraída del logo oficial, no inventada)
- Azul `#0000B6` — color sólido del wordmark
- Magenta `#FF2E88` — extremo superior del gradiente del isotipo
- Gradiente de marca: vertical `#FF2E88 → #0000B6`

Los CTAs usan magenta porque es el único color de alto contraste contra el azul/blanco del resto
de la página: es imposible confundirlos con un link secundario.

## Tracking
El evento `Lead` de Meta se dispara en el clic, **antes** de salir a WhatsApp. Los links abren en
pestaña nueva (`target="_blank"`), así la petición del pixel alcanza a completarse — es más fiable
que `preventDefault` + redirect manual. Cada evento incluye `source` (`header`, `floating`,
`section`, `footer`) para saber qué CTA convierte mejor.

## Cumplimiento COFEPRIS
- Aviso de Publicidad **2529012002A00051** en el footer
- Sin promesas de resultado, sin "garantizado", sin "cura", sin comparación con otras clínicas
- Sin fotos de antes/después
- Testimonios presentados como experiencia del paciente + nota legal explícita debajo
- Disclaimer de que el sitio es orientativo y no sustituye consulta ni diagnóstico
- Tono educativo en todas las secciones

## Placeholders visuales a sustituir
Todos están marcados en el HTML con `<!-- REEMPLAZAR: ... -->`:
1. **Hero** — el visual óptico animado es un placeholder de marca; sustituir por foto real del
   microscopio o del consultorio (cuadrada, `.webp`)
2. **Doctor** — foto real del Dr. Tapia (vertical 4:5); ya existe en su sitio actual
3. **Testimonios** — 3 avatares (`FOTO`): foto del paciente con consentimiento, o del consultorio
4. **Redes sociales** — los 3 iconos del footer apuntan a `#`; poner URLs reales

## Pendientes de contenido (bloquean lanzamiento, no el prototipo)
- [ ] Precio del tratamiento de eliminación de caries con microscopio
      *(mientras tanto la página usa: "El costo exacto de tu tratamiento se confirma en tu primera valoración")*
- [ ] Confirmar si aplica "sin anestesia" en la mayoría de los casos
      → si el doctor lo confirma, agregar la línea en la sección 02 (hay un comentario marcando el lugar)
- [ ] Duración de la consulta de valoración
      → FAQ #5 tiene un badge naranja "Pendiente" visible; quitarlo al completar
- [ ] Testimonios en video nuevos, con consentimiento firmado, específicos a micro-odontología
- [ ] Verificar que el Aviso de Publicidad COFEPRIS cubra este contenido específico

## Deploy
Es HTML estático: sube `index.html` + `logo-swiss-dental.svg` a cualquier hosting
(Netlify, Vercel, Hostinger, o una subcarpeta del WordPress actual).
Sin build, sin dependencias. Única petición externa: Google Fonts (Manrope).

Para máxima velocidad en Meta Ads, opcionalmente auto-alojar la fuente y quitar el `<link>`
a fonts.googleapis.com.
