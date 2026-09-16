# Landing "Micro-Odontología" — Swiss Dental / Dr. Arturo Ramírez Tapia

Landing de una sola oferta. Tráfico 100% pagado desde Meta Ads.
Conversión = clic al botón de WhatsApp. Sin formularios, sin menú, sin ofertas compitiendo.

👉 **Para publicarla, sigue [PUBLICAR.md](PUBLICAR.md).** Son tres datos y cuatro comprobaciones.
👉 **Para entender por qué está hecha así, lee [ESTRUCTURA.md](ESTRUCTURA.md).**

## Archivos

| Archivo | Qué es |
|---|---|
| `index.html` | La landing completa (HTML + CSS + JS en un solo archivo) |
| `logo-swiss-dental.svg` | Logo oficial descargado de drarturotapia.com |
| `favicon.svg` · `apple-touch-icon.png` | Icono de pestaña, derivado del diente del logo |
| `og-image.jpg` | Imagen de la vista previa al compartir el enlace (1200×630) |
| `hero-bg.webp` · `hero-bg-800.webp` | Foto de fondo del hero — el equipo en el consultorio real |
| `dr-tapia.webp` · `dr-tapia-560.webp` | Retrato del doctor en el recuadro del hero |
| `dr-tapia-amed.webp` · `dr-tapia-amed-480.webp` | El doctor en su microscopio + emblema AMED (sección 05) |
| `fonts/*.woff2` | Manrope auto-alojada: cero peticiones a terceros |

Sin build, sin dependencias, sin peticiones externas. Se sube tal cual a cualquier hosting.

## Configuración — un solo bloque

Los tres datos variables (`whatsapp`, `pixelId`, `cedula`) viven en el objeto
`window.SWISS_CONFIG`, al final de `index.html`. Todo lo demás los lee de ahí.

La página **falla a la vista, no en silencio**: sin número de WhatsApp muestra una franja
roja de "SIN PUBLICAR" y desactiva los botones, en vez de dejar seis CTAs que parecen
funcionar y no llevan a ninguna parte. Sin cédula, esa línea del pie no se imprime en
lugar de mostrar un marcador de posición al paciente.

## Fotografía — todo es material real del cliente

Las imágenes provienen del sitio oficial del cliente (drarturotapia.com):
el consultorio real de San Diego Metepec, su equipo real y su microscopio real.

> **No usar imágenes generadas con IA en esta página.** Es publicidad sanitaria regulada
> por COFEPRIS sobre un profesional identificable: una escena fabricada de un médico real
> en un consultorio que no es el suyo es un riesgo legal y de credibilidad, y además
> es innecesario — el cliente ya tiene fotografía profesional propia.

Para regenerar desde otros originales:

```bash
# fondo del hero (1376 y 800 de ancho)
ffmpeg -i foto.jpg -vf "scale=1376:-2" tmp.png && cwebp -q 76 tmp.png -o hero-bg.webp
ffmpeg -i foto.jpg -vf "scale=800:-2"  tmp.png && cwebp -q 76 tmp.png -o hero-bg-800.webp

# retrato del hero (1:1 nativo)
ffmpeg -i retrato.jpg -vf "scale=920:920" tmp.png && cwebp -q 80 tmp.png -o dr-tapia.webp
ffmpeg -i retrato.jpg -vf "scale=560:560" tmp.png && cwebp -q 78 tmp.png -o dr-tapia-560.webp
```

El fondo del hero va como `<img class="hero-bg">` con `fetchpriority="high"`, no como
`background-image`: el navegador descubre un background-image tarde (tiene que construir
el CSSOM primero) y esta foto es el elemento LCP del sitio.

El retrato del hero **no** lleva `aria-hidden`: es contenido, no decoración, y su `alt`
describe al doctor. Hay que actualizarlo si cambia la foto.

## Paleta (extraída del logo oficial, no inventada)

- Azul `#0000B6` — color sólido del wordmark
- Magenta `#FF2E88` — extremo superior del gradiente del isotipo
- Gradiente de marca: vertical `#FF2E88 → #0000B6`

Los CTAs usan magenta porque es el único color de alto contraste contra el azul/blanco del
resto de la página: es imposible confundirlos con un link secundario.

## Tracking

El evento `Lead` de Meta se dispara en el clic, **antes** de salir a WhatsApp. Los links
abren en pestaña nueva (`target="_blank"`), así la petición del pixel alcanza a completarse
— es más fiable que `preventDefault` + redirect manual. Cada evento incluye `source`
(`header`, `floating`, `section`, `footer`) para saber qué CTA convierte mejor.

El pixel no se carga si `pixelId` está vacío, para no lanzar una petición inválida a Meta.
No hay etiqueta `<noscript>` del pixel: solo admitía el ID escrito a mano — rompiendo la
promesa de "un único lugar que editar" — y sin JavaScript tampoco se registra el `Lead`.

## Cumplimiento COFEPRIS

- Aviso de Publicidad **2529012002A00051** en el footer
- Sin promesas de resultado, sin "garantizado", sin "cura", sin comparación con otras clínicas
- Sin fotos de antes/después
- Testimonios presentados como experiencia del paciente + nota legal explícita debajo
- Disclaimer de que el sitio es orientativo y no sustituye consulta ni diagnóstico
- Tono educativo en todas las secciones
- Párrafo de aviso de privacidad en el pie (cookies, pixel de Meta, datos de WhatsApp)

## Deploy

HTML estático. Se suben todos los archivos de la lista de arriba a Netlify, Vercel,
Hostinger o una subcarpeta del WordPress actual. **Si la dirección final no es
`https://drarturotapia.com/micro-odontologia/`, hay que actualizarla** en `canonical`,
`og:url`, `og:image` y el JSON-LD — está explicado en [PUBLICAR.md](PUBLICAR.md).
