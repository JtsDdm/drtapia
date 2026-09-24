# Landing "Micro-Odontología" — Swiss Dental / Dr. Arturo Ramírez Tapia

Landing de una sola oferta. Tráfico 100% pagado desde Meta Ads.
Conversión = clic al botón de WhatsApp. Sin formularios, sin menú, sin ofertas compitiendo.

👉 **Para publicarla, sigue [PUBLICAR.md](PUBLICAR.md).** Son tres datos y cuatro comprobaciones.
👉 **Para entender por qué está hecha así, lee [ESTRUCTURA.md](ESTRUCTURA.md).**

## Archivos

| Archivo | Qué es |
|---|---|
| `index.html` | La landing completa (HTML + CSS + JS en un solo archivo) |
| `logo-swiss-dental.svg` | Marca apilada (isotipo + SWISS DENTAL), en el header |
| `logo-swiss-dental-completo.svg` | Igual, con el eslogan "Precisión odontológica", en el pie |
| `isotipo-swiss-dental.svg` | Solo la "S", recortada al contenido |
| `logo1.svg` · `Logo2.svg` · `ICONO.svg` | Originales tal como los entregó el cliente (1080×1080, con márgenes) |
| `favicon.svg` · `favicon-32.png` · `apple-touch-icon.png` | Iconos de pestaña y de pantalla de inicio |
| `og-image.jpg` | Imagen de la vista previa al compartir el enlace (1200×630) |
| `hero-bg.webp` · `hero-bg-800.webp` | Foto de fondo del hero — el equipo en el consultorio real |
| `dr-tapia.webp` · `dr-tapia-560.webp` | Retrato del doctor en el recuadro del hero |
| `dr-tapia-amed.webp` · `dr-tapia-amed-480.webp` | El doctor en su microscopio + emblema AMED (sección 05) |
| `fonts/*.woff2` | Manrope auto-alojada: cero peticiones a terceros |

Sin build, sin dependencias, sin peticiones externas. Se sube tal cual a cualquier hosting.

## Configuración — un solo bloque

Los tres datos variables (`whatsapp`, `pixelId`, `cedula`) viven en el objeto
`window.SWISS_CONFIG`, al final de `index.html`. Todo lo demás los lee de ahí.

Valores actuales:

- `whatsapp`: `522461441431`
- `pixelId`: `1258416829427122` — "Swiss Dental Pixel", del portfolio comercial Swiss Dental en Meta
- `cedula`: `3637698 · 6075426` — las dos cédulas del doctor; el pie las muestra como "Cédulas profesionales"

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

## Iconos

Salen de `ICONO.svg`, el isotipo oficial, **sin retocar ni un color**.

Van sobre una placa blanca, no sueltos: el icono es azul marino sobre transparente y
en las pestañas con tema oscuro desaparecería. La placa lo deja visible en claro y en
oscuro conservando los colores de marca.

- `favicon.svg` — el que usan los navegadores modernos
- `favicon-32.png` — respaldo para los que no admiten favicon en SVG
- `apple-touch-icon.png` — 180×180, **cuadrado a sangre**: iOS aplica sus propias
  esquinas redondeadas, así que el archivo no debe traerlas o se redondea dos veces

## Paleta (extraída del logo oficial, no inventada)

Del logo (`logo1.svg` / `Logo2.svg`):

- Azul marino `#071C39` — tinta del texto y fondo de todas las secciones oscuras
- Azul eléctrico `#103CE1` — acento sobre fondo claro (iconos, cifras, destacados)
- Gradiente de marca: horizontal `#060A79 → #103CE1`
- Azul claro `#8FB4FF` — aclarado del anterior, para acentos sobre el marino,
  donde el azul de marca no alcanza el contraste mínimo

Fuera del logo, y a propósito:

- Magenta `#E31B6D` — **exclusivamente los botones de WhatsApp**

### Por qué el magenta no está en el logo y aun así se queda

Es el único color de la página que significa "aquí se hace clic". Sobre una página que ya
es azul de arriba abajo, ningún azul de marca logra separarse igual: el botón se leería
como un elemento más de la interfaz. Mientras el magenta no aparezca en ningún otro sitio,
es imposible confundir el CTA con un link secundario.

La regla se aplica literalmente: iconos de credenciales, cifras de precio, numeración de
tarjetas y hover de redes pasaron a azul cuando se repintó la página. Si el magenta vuelve
a aparecer en cualquier otro elemento, el CTA pierde ese privilegio.

No es el `#FF2E88` del logo anterior sino un tono algo más profundo: con texto blanco
encima, el magenta brillante daba 3.5:1 de contraste y el mínimo AA para ese tamaño de
texto es 4.5:1. `#E31B6D` da 4.52:1 sin perder fuerza. Todos los pares de color de la
página cumplen AA.

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

HTML estático en Vercel: cada push a `main` se publica solo en
**https://micro.drarturotapia.com/** (y en `drtapia.vercel.app`). Esa dirección es la que
llevan `canonical`, `og:url`, `og:image` y el JSON-LD; si algún día cambia, hay que
actualizarla en esos cuatro sitios — está explicado en [PUBLICAR.md](PUBLICAR.md).
