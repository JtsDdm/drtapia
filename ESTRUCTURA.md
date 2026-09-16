# Estructura y racional de diseño
### Landing "Micro-Odontología" — Swiss Dental / Dr. Arturo Ramírez Tapia

Este documento explica **qué** se construyó y, sobre todo, **por qué**. Sirve para defender
decisiones ante el cliente, para que cualquiera que toque la página después entienda la lógica,
y para saber qué se puede cambiar sin romper el embudo.

---

## 1. La premisa que condiciona todo lo demás

Tres hechos del brief determinan cada decisión de la página:

| Hecho | Consecuencia de diseño |
|---|---|
| Tráfico **100% pagado desde Meta Ads** | El visitante llega frío, sin intención previa, desde el scroll de un feed. No busca — fue interrumpido. |
| Conversión = **un clic a WhatsApp** | Una sola acción. Todo lo que no empuje hacia ese clic es ruido que resta. |
| Regulación **COFEPRIS** | No se puede vender con promesas. El persuasor tiene que ser el *mecanismo*, no el resultado. |

De ahí sale el principio rector: **una sola oferta, una sola acción, cero salidas.**
La página no es un sitio web. Es un embudo de una pantalla de ancho.

---

## 2. Arquitectura de la página

Diez bloques en un orden que no es decorativo — es una **escalera de compromiso**. Cada sección
resuelve la objeción que impide avanzar a la siguiente.

```
┌─ 01  HEADER ─────────── logo, cero navegación
│
├─ 02  HERO ───────────── promesa + mecanismo + CTA + prueba de exclusividad
│                          ↓  "¿esto es para mí?"
├─ 03  PROBLEMA ───────── reconocer el miedo, reencuadrarlo como límite técnico
│                          ↓  "¿y cómo lo resuelven?"
├─ 04  MECANISMO ──────── 30× de magnificación → 3 consecuencias concretas
│                          ↓  "¿pero quién me lo va a hacer?"
├─ 05  AUTORIDAD ──────── credenciales verificables del doctor
│                          ↓  "¿cuánto me va a costar?"
├─ 06  PRECIO ─────────── $900 transparente + financiamiento
│                          ↓  "¿le funcionó a alguien más?"
├─ 07  PRUEBA SOCIAL ──── experiencia de pacientes reales
│                          ↓  "me queda una duda…"
├─ 08  FAQ ────────────── barrido final de objeciones
│                          ↓
├─ 09  CTA FINAL ──────── misma acción, mismo texto que el hero
│
└─ 10  FOOTER LEGAL ───── COFEPRIS, cédula, dirección
```

**Y superpuesto a todo: el botón de WhatsApp flotante**, visible desde el primer píxel hasta el
último. El usuario nunca tiene que buscar cómo convertir — decida cuando decida.

---

## 3. Sección por sección: el porqué

### 01 · Header — solo logo, sin menú

**Por qué no hay navegación:** cada link de un menú es una puerta de salida. En una landing de
tráfico pagado, un visitante que se va a "Servicios" o "Nosotros" es dinero publicitario perdido.
El logo existe para dar contexto de marca en el primer segundo, nada más — ni siquiera lleva a
la home, lleva al inicio de la misma página.

El único elemento clicable además del logo es el CTA de WhatsApp, y aparece **solo en desktop**:
en móvil ya está la barra flotante abajo y dos botones compitiendo a la vez es fricción.

### 02 · Hero — la promesa antes que la tecnología

El headline vende **el resultado emocional** ("sin dolor, sin estrés"), no la tecnología.
"Micro-odontología" aparece al final de la frase, en gradiente de marca: primero te importa,
después te explico qué es.

El subheadline hace tres trabajos en una sola oración: define el mecanismo, lista tres beneficios
concretos, y cierra con **exclusividad geográfica** ("la única clínica en Tlaxcala"). Esa última
parte es la que convierte la página en algo que no puedes comparar con el dentista de la esquina.

**El badge de credibilidad va pegado al CTA, no en otra sección.** El instante de mayor duda es
el medio segundo antes del clic — ahí es donde hay que poner la prueba, no 2000px más abajo.

**El visual óptico:** anillos concéntricos animados con el gradiente de marca, sobre azul profundo.
Es un placeholder, pero *diseñado* — comunica magnificación y precisión. Una caja gris con
"imagen aquí" habría matado la percepción premium del prototipo. Se reemplaza por foto real
del microscopio o del consultorio.

### 03 · Problema — reconocer antes de vender

La tentación en salud es abrir vendiendo. Aquí se abre **nombrando el miedo del visitante**:
"Sabemos por qué no te gusta ir al dentista."

Dos razones:

1. **Rapport.** El lector se siente visto, no vendido. Es el único momento en que la página habla
   de él y no de la clínica.
2. **Reencuadre — la jugada estratégica de toda la página.** El miedo al dentista se explica como
   un **límite técnico** ("el ojo humano no puede ver con precisión"), no como una debilidad
   personal ni como mala práctica de otros dentistas.

Ese reencuadre hace dos cosas a la vez: quita la vergüenza al paciente que lleva años evitando
la consulta, y **abre el hueco exacto que el microscopio viene a llenar** — sin desprestigiar a
nadie, lo cual sería una violación directa de COFEPRIS.

Las cuatro *pills* al cierre ("Miedo al dolor", "Estrés de la cita"…) permiten que quien escanea
en vez de leer se reconozca en un segundo.

### 04 · Mecanismo — el corazón persuasivo

**Fondo azul profundo.** Es la única sección oscura de la página: rompe el ritmo visual y marca
"aquí está lo importante".

**El dato `30×` como pieza tipográfica de gran tamaño.** Una cifra concreta es infinitamente más
creíble que un adjetivo. "Alta precisión" no significa nada; "30 aumentos" es verificable.

Las tres tarjetas **traducen tecnología en consecuencias para el paciente**. Nadie compra
magnificación óptica — compran conservar su diente, menos tiempo en el sillón y una cita sin
sorpresas. Esa traducción es todo el trabajo de esta sección.

> Hay un comentario en el HTML marcando exactamente dónde iría la línea de "sin anestesia" si el
> doctor la confirma. **No se asumió.** Sería la afirmación más persuasiva de la página, y por eso
> mismo la más riesgosa si no está respaldada.

### 05 · Autoridad — después del mecanismo, no antes

**Por qué el doctor va en quinto lugar y no en segundo:** las credenciales solo importan una vez
que el lector ya quiere el tratamiento. Presentarlas antes es hablar de la clínica mientras el
visitante todavía no sabe por qué debería importarle.

El orden interno de las credenciales está jerarquizado por **poder de diferenciación**, no por
prestigio académico:

1. **Fundador de la primera clínica con microscopio de la zona (2018)** — destacado en bloque azul.
   Es el único dato que nadie más en Tlaxcala–Puebla puede decir.
2. **Academy of Microscope Enhanced Dentistry (EE.UU.)** — la prueba de que la especialización
   en microscopio es real y está avalada internacionalmente, no un argumento de marketing.
3. Títulos, especialidad y recertificación — la base de confianza estándar.
4. Membresías gremiales — refuerzo, en último lugar.

La foto va en formato vertical 4:5 porque es el encuadre que mejor sostiene un retrato profesional
y el que mejor aprovecha el espacio en la retícula de dos columnas.

### 06 · Precio — la objeción que nadie escribe en WhatsApp

**Por qué el precio está en la página y no "se dice por mensaje":** el costo es la duda #1 y la
que más gente hace abandonar en silencio. Ocultarlo no la elimina, solo mueve la fricción al chat
—donde ya cuesta dinero atenderla— y filtra al revés: espanta a quien sí podía pagar.

Los $900 se presentan como **tarjeta destacada con etiqueta "Empieza aquí"**, y el desglose
(microscopio + cámara intraoral + radiografías) convierte un precio en un paquete. Es el mismo
precio, percibido como más.

El financiamiento a meses sin intereses va inmediatamente después, con su propio CTA: es el
desactivador de la objeción económica para quien el monto sí le pesa.

**Va antes de los testimonios a propósito.** Primero se resuelve la objeción racional; después se
pide confianza emocional. Al revés, el lector lee los testimonios con la calculadora en la cabeza.

### 07 · Prueba social — experiencia, nunca resultado

Tres reseñas públicas reales, 5 estrellas, con espacio para foto.

**El detalle de cumplimiento más delicado de la página:** las tres citas hablan de *trato,
puntualidad, limpieza y acompañamiento* — nunca de resultados clínicos. Eso no es casualidad ni
limitación: es exactamente lo que COFEPRIS permite, y además es lo que responde al miedo planteado
en la sección 03. El visitante no teme al resultado, teme **la experiencia**. Los testimonios
atacan justo eso.

Debajo va una nota legal explícita aclarando que son experiencias individuales y no promesa de
resultado. Está en gris pequeño pero **es visible, no escondida** — la transparencia aquí suma
confianza en vez de restarla.

### 08 · FAQ — el último filtro antes del clic

Seis preguntas que barren las objeciones que sobreviven a todo lo anterior. Formato acordeón
nativo (`<details>`), con la primera abierta para que se vea que hay contenido.

Dos decisiones:
- **La pregunta de anestesia responde "depende del caso"** en vez de tranquilizar de más.
  Es honesto, es lo único defendible legalmente, y no genera una expectativa que el doctor tenga
  que desmontar en consulta.
- **La duración de consulta lleva un badge naranja "Pendiente" visible en la página.**
  Deliberado: es un recordatorio imposible de ignorar antes de lanzar. Se quita al completar el dato.

### 09 · CTA final — repetición, no variación

Mismo texto exacto que el hero: *"Agenda tu valoración por WhatsApp"*.

**Por qué no un texto distinto:** variar el copy del CTA obliga al lector a reevaluar la decisión.
La repetición literal la refuerza. Debajo, un recordatorio discreto del precio y el financiamiento
—los dos datos que quitan fricción— y nada más alrededor que pueda competir por el clic.

### 10 · Footer legal — cumplimiento como señal de confianza

Aviso de Publicidad COFEPRIS, cédula profesional, dirección física y disclaimer.

Cumple el requisito regulatorio, pero también hace un trabajo de conversión: **una dirección real
y un número de registro visible son señales de legitimidad** en una categoría donde abunda la
clínica improvisada.

---

## 4. Decisiones técnicas

| Decisión | Motivo |
|---|---|
| **Un solo archivo HTML, sin framework ni build** | El costo por clic de Meta se paga antes de que cargue la página. Cada décima de segundo de carga se traduce en abandono y en presupuesto quemado. No hay nada aquí que justifique React. |
| **Mobile-first real** | El tráfico de Meta Ads es abrumadoramente móvil. El diseño se construyó primero para 390px y después se expandió, no al revés. |
| **CTA flotante = barra completa en móvil, pill en desktop** | En móvil, la barra inferior de ancho completo es el área de mayor tasa de clic y cae bajo el pulgar. En desktop sería invasiva, así que se reduce a pill en la esquina. `body` reserva 96px abajo en móvil para no tapar el footer. |
| **`target="_blank"` + evento `Lead` en el clic** | Al abrir WhatsApp en pestaña nueva, la página sigue viva y la petición del pixel alcanza a completarse. Es más fiable que `preventDefault()` + redirect manual, donde el navegador puede cancelar la petición al navegar. |
| **`source` en cada evento `Lead`** | Cada CTA reporta de dónde salió (`header`, `floating`, `section`, `footer`). Permite saber qué punto de la página convierte y dónde vale la pena insistir. |
| **Número de WhatsApp en una sola variable** | Los 7 CTAs lo leen de un único lugar. Cambiar el número es editar una línea, no cazar siete. |
| **FAQ con `<details>` nativo** | Cero JavaScript, accesible por teclado por defecto, funciona sin JS e indexable por Google. |
| **JSON-LD (`Dentist` + `FAQPage`)** | Aunque el tráfico sea pagado, no cuesta nada y habilita resultados enriquecidos si la página gana tracción orgánica. |
| **`prefers-reduced-motion` respetado** | Las animaciones de entrada se desactivan por completo para quien lo pide a nivel sistema. Accesibilidad básica. |
| **Sin dependencias externas salvo Google Fonts** | Única petición a terceros. Se puede auto-alojar la fuente para eliminarla del todo. |

---

## 5. Decisiones de marca y diseño

**La paleta se extrajo del SVG del logo oficial, no se inventó.**
Azul `#0000B6` (wordmark sólido) y magenta `#FF2E88` (extremo superior del gradiente del isotipo),
con el gradiente de marca vertical `#FF2E88 → #0000B6`. Cualquier color nuevo habría roto la
consistencia con el resto de los materiales del cliente.

**El magenta está reservado exclusivamente para CTAs.** Aparece en los botones y en detalles mínimos
de acento — nunca en texto de cuerpo, nunca en elementos decorativos grandes. Es un presupuesto de
color: mientras el magenta signifique "aquí se hace clic" y nada más, el botón es imposible de
confundir con un link secundario. Es lo que el brief pedía como "alto contraste", resuelto con la
marca en vez de con un verde WhatsApp genérico que habría abaratado el conjunto.

**Tipografía Manrope, retícula amplia, secciones numeradas 01–06.**
El nombre "Swiss Dental" invita literalmente al diseño suizo: rejilla estricta, mucho aire,
jerarquía por tamaño y peso en vez de por adorno. Es la decisión que más aleja la página del
estándar visual de "dentista amigable" — sin ilustraciones, sin dientes caricaturizados, sin
degradados aleatorios.

**Los placeholders están diseñados, no vacíos.** El visual óptico, el marco de foto del doctor y
los avatares de testimonios son elementos intencionales con las líneas punteadas y etiquetas de la
marca. Un prototipo con cajas grises se presenta mal ante el cliente y hace difícil juzgar el
diseño real.

---

## 6. Lo que deliberadamente NO se incluyó

| Elemento omitido | Motivo |
|---|---|
| Menú de navegación | Puertas de salida en una página de una sola acción. |
| Formulario de contacto | Compite con WhatsApp y convierte peor en este canal. Dos vías de conversión dividen la decisión. |
| Pop-up de salida / cuenta regresiva | Táctica agresiva incompatible con el tono premium y con el criterio de publicidad en salud. |
| Fotos de antes/después | Prohibido por COFEPRIS. |
| Otros servicios de la clínica | Una landing, una oferta. Ortodoncia, blanqueamiento, etc. merecen sus propias landings con sus propios anuncios. |
| Chatbot / widget de terceros | Peso extra, riesgo de privacidad y compite con el CTA principal. |
| Comparaciones con otras clínicas | Prohibido por COFEPRIS. La exclusividad se afirma como hecho verificable ("primera clínica de la zona"), nunca como superioridad. |

---

## 7. Cómo medir si funciona

1. **CTR a WhatsApp** — eventos `Lead` ÷ `PageView`. Es la métrica de la página.
2. **Qué CTA convierte** — segmentar `Lead` por el parámetro `source`. Si el flotante domina,
   el contenido no está cerrando y la gente decide por impulso; si domina el CTA final, la página
   está haciendo el trabajo de convencer.
3. **Profundidad de scroll** — dónde se cae la lectura indica qué sección está fallando.
4. **Calidad del lead en WhatsApp** — cuántos de los que escriben agendan de verdad. Si el volumen
   es alto y el agendamiento bajo, el problema está en el anuncio, no en la landing.

---

## 8. Qué se puede cambiar sin romper nada

**Seguro de tocar:** copy dentro de cada sección, fotos, orden de las FAQ, textos de las tarjetas
del mecanismo, testimonios.

**Cambiar con cuidado:** el orden de las secciones (la escalera de compromiso está calculada;
mover Precio antes de Autoridad, por ejemplo, invierte la lógica de la objeción).

**No tocar sin revisar cumplimiento:** cualquier redacción sobre resultados, dolor, garantías o
comparaciones, y el bloque legal del footer.
