# Antes de publicar — checklist

Lista pensada para alguien que **no programa**. Son cuatro datos que hay que escribir
y un par de comprobaciones. Nada más.

> **Estado actual:** los cuatro datos ya están puestos (WhatsApp, pixel `1434057772157943`,
> cédulas `3637698 · 6075426` y Clarity `ynysww2ac2`) y la dirección ya es
> `https://micro.drarturotapia.com/`. Los pasos 1 y 3 solo hacen falta si algo cambia.

---

## Paso 1 · Rellenar los cuatro datos

Abre `index.html` con cualquier editor de texto y busca esta parte
(está casi al final del archivo, busca la palabra **CONFIGURACIÓN**):

```js
window.SWISS_CONFIG = {
  whatsapp:  '',
  pixelId:   '',
  cedula:    '',
  clarityId: '',
  ...
};
```

Escribe cada valor **entre las comillas**:

| Dato | Qué poner | Ejemplo |
|---|---|---|
| `whatsapp` | El número que va a recibir los mensajes, en formato internacional, **sin `+`, sin espacios y sin guiones** | `'522462410157'` |
| `pixelId` | El ID del pixel de Meta, solo los números | `'123456789012345'` |
| `cedula` | La cédula profesional del Dr. Arturo Ramírez Tapia | `'1234567'` |
| `clarityId` | El ID de proyecto de Microsoft Clarity, que sale en su panel | `'abc123xyz'` |

Ese bloque es **el único lugar del archivo que hay que tocar**. Los 6 botones de
WhatsApp, la medición de Meta, las grabaciones de Clarity y la línea legal del pie
toman los datos de ahí.

### Qué pasa si te falta un dato

La página está hecha para no publicarse rota en silencio:

- **Sin `whatsapp`** → aparece una **franja roja arriba** que dice "SIN PUBLICAR" y
  los botones quedan desactivados. Imposible no darse cuenta.
- **Sin `pixelId`** → no se carga nada de Meta. La página funciona, pero **no mide**:
  no sabrás qué anuncio trae pacientes.
- **Sin `cedula`** → la línea de la cédula simplemente no se muestra
  (antes se imprimía el texto `{{CEDULA_PROFESIONAL}}` a la vista del paciente).
- **Sin `clarityId`** → no se carga Clarity. La página funciona igual, pero no se
  graban las sesiones ni los mapas de calor.

---

## Paso 2 · Subir los archivos

Sube **todo el contenido de la carpeta** a tu hosting (Netlify, Vercel, Hostinger,
o una subcarpeta del WordPress actual). No hay que compilar ni instalar nada.

Archivos necesarios:

```
index.html
logo-swiss-dental.svg
logo-swiss-dental-completo.svg
favicon.svg
favicon-32.png
apple-touch-icon.png
og-image.jpg
hero-bg.webp        hero-bg-800.webp
dr-tapia.webp       dr-tapia-560.webp
dr-tapia-amed.webp  dr-tapia-amed-480.webp
fonts/manrope-latin.woff2
fonts/manrope-latin-ext.woff2
```

---

## Paso 3 · Ajustar la dirección definitiva

La página vive en `https://micro.drarturotapia.com/`. Si algún día se muda,
hay que cambiar esa dirección en 4 líneas del `index.html`. Busca
`micro.drarturotapia.com` y reemplaza por la dirección nueva.

Si no se hace, dos cosas fallan:

- Google puede indexar la página equivocada (etiqueta `canonical`).
- La vista previa al compartir el enlace en WhatsApp o Facebook sale sin imagen.

---

## Paso 4 · Comprobaciones finales

- [ ] Abrir la página en el móvil y tocar el botón de WhatsApp: debe abrir el chat
      con el número correcto y el mensaje ya escrito.
- [ ] Repetir con los 6 botones (arriba, hero, precio, testimonios, final, y la barra fija).
- [ ] Verificar en el Administrador de eventos de Meta que llegan `PageView` y `Lead`.
- [ ] Pegar el enlace en un chat de WhatsApp y comprobar que sale la vista previa con foto.

---

## Pendientes de contenido (no bloquean, pero conviene)

- [ ] **Precio del tratamiento de caries con microscopio.** Hoy la página dice
      "el costo exacto se confirma en tu primera valoración".
- [ ] **Duración de la consulta de valoración.** La FAQ contesta "se confirma al agendar".
- [ ] **Confirmar con el doctor si aplica "sin anestesia"** en la mayoría de casos.
      Si lo confirma, hay un comentario en la sección 02 marcando dónde va la línea.
      No se asumió: sería la frase más persuasiva de la página y la más riesgosa
      si no está respaldada.
- [ ] **Fotos de pacientes con consentimiento firmado** para los testimonios
      (hoy llevan un icono neutro).
- [ ] **Aviso de privacidad formal.** La página lleva un párrafo corto en el pie,
      pero la clínica debería tener un aviso completo y enlazarlo ahí.
- [ ] **Verificar que el Aviso de Publicidad COFEPRIS 2529012002A00051** cubre
      este contenido específico.
