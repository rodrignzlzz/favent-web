---
version: alpha
name: Favent-design-system
description: "Lienzo oscuro de producto B2B construido sobre #0B0F17 (azul casi negro), texto gris claro (#E9EEF6) y dos acentos con funciones separadas: rosa señal (#FF4F9A) para la marca y el progreso, y azul eléctrico suave (#4DA8FF / #7CC4FF) para la energía, el movimiento y el énfasis. La web se lee como un canal de ventas técnico y serio: Geist en titulares (500, tracking negativo), Geist Mono en etiquetas, códigos e importes, y el logotipo en Newsreader con punto rosa. La profundidad viene del vidrio esmerilado (glassmorfismo) sobre una textura de puntos, de algunos relieves neumórficos y de interfaces de ejemplo claras, tratadas como «pantallas encendidas». En el inicio, pistas de procesador recorridas por pulsos de energía azul."

colors:
  primary: "#FF4F9A"
  on-primary: "#0B0F17"
  primary-deep: "#C2185B"
  electric: "#4DA8FF"
  electric-soft: "#7CC4FF"
  electric-glow: "#D4ECFF"
  ink: "#E9EEF6"
  ink-muted: "#A7B1C2"
  ink-subtle: "#8592A6"
  ink-reveal-dim: "#66707F"
  canvas: "#0B0F17"
  canvas-deep: "#06080D"
  surface-1: "#121826"
  surface-2: "#172036"
  surface-active: "#263047"
  glass: "rgba(18,24,38,0.50)"
  glass-line: "rgba(255,255,255,0.09)"
  hairline: "#1C2333"
  hairline-strong: "#2A3346"
  field-border: "#5A657E"
  neu-shadow-low: "rgba(0,0,0,0.62)"
  neu-shadow-high: "rgba(255,255,255,0.04)"
  screen-canvas: "#F6F6F3"
  screen-surface: "#FFFFFF"
  screen-tint: "#EAF2F8"
  screen-ink: "#1E2226"
  screen-ink-muted: "#50565C"
  screen-ink-subtle: "#656B71"
  screen-hairline: "#E6E7E3"
  screen-accent: "#2B6CA8"
  screen-accent-deep: "#0B2A4A"
  semantic-error: "#FF8A9A"
  semantic-error-on-screen: "#A12A1F"

typography:
  display-xl:
    fontFamily: Geist
    fontSize: clamp(42px, 7vw, 84px)
    fontWeight: 500
    lineHeight: 0.98
    letterSpacing: -0.04em
  display-lg:
    fontFamily: Geist
    fontSize: clamp(32px, 4.5vw, 52px)
    fontWeight: 500
    lineHeight: 1.05
    letterSpacing: -0.035em
  statement:
    fontFamily: Geist
    fontSize: clamp(28px, 4vw, 48px)
    fontWeight: 500
    lineHeight: 1.20
    letterSpacing: -0.03em
  headline:
    fontFamily: Geist
    fontSize: clamp(24px, 3vw, 32px)
    fontWeight: 500
    lineHeight: 1.10
    letterSpacing: -0.025em
  card-title:
    fontFamily: Geist
    fontSize: 22px
    fontWeight: 500
    lineHeight: 1.20
    letterSpacing: -0.02em
  subhead:
    fontFamily: Geist
    fontSize: clamp(17px, 2vw, 20px)
    fontWeight: 400
    lineHeight: 1.55
    letterSpacing: 0
  body:
    fontFamily: Geist
    fontSize: 17px
    fontWeight: 400
    lineHeight: 1.55
    letterSpacing: 0
  body-sm:
    fontFamily: Geist
    fontSize: 15px
    fontWeight: 400
    lineHeight: 1.55
    letterSpacing: 0
  caption:
    fontFamily: Geist
    fontSize: 13px
    fontWeight: 400
    lineHeight: 1.50
    letterSpacing: 0
  button:
    fontFamily: Geist
    fontSize: 15px
    fontWeight: 600
    lineHeight: 1.20
    letterSpacing: 0
  eyebrow:
    fontFamily: Geist Mono
    fontSize: 13px
    fontWeight: 500
    lineHeight: 1.30
    letterSpacing: 0
  mono:
    fontFamily: Geist Mono
    fontSize: 13px
    fontWeight: 400
    lineHeight: 1.50
    letterSpacing: 0
  logo:
    fontFamily: Newsreader
    fontSize: 29px
    fontWeight: 500
    lineHeight: 1.00
    letterSpacing: -0.02em

rounded:
  sm: 12px
  md: 16px
  lg: 20px
  xl: 28px
  xxl: 32px
  pill: 9999px

spacing:
  section: clamp(96px, 11vw, 168px)
  section-mobile: 80px
  gutter: 24px
  container: 1200px
  stack-lg: 56px
  stack-md: 24px
  stack-sm: 14px

components:
  button-primary:
    backgroundColor: "{colors.ink}"
    textColor: "{colors.canvas}"
    typography: "{typography.button}"
    rounded: "{rounded.pill}"
    padding: 0 26px
    height: 52px
  button-secondary:
    backgroundColor: "{colors.screen-accent}"
    textColor: "#FFFFFF"
    typography: "{typography.button}"
    rounded: "{rounded.pill}"
    padding: 0 20px
    height: 44px
  button-chip:
    backgroundColor: "{colors.canvas}"
    textColor: "{colors.ink-muted}"
    typography: "{typography.mono}"
    rounded: "{rounded.pill}"
    padding: 0 12px
    height: 30px
  nav-bar-stuck:
    backgroundColor: "rgba(11,15,23,0.62)"
    textColor: "{colors.ink}"
    border: "1px {colors.glass-line} bottom"
    backdrop: blur(16px) saturate(140%)
  eyebrow:
    textColor: "{colors.ink-muted}"
    typography: "{typography.eyebrow}"
    marker: "7px square {colors.primary}"
  glass-card:
    backgroundColor: "{colors.glass}"
    border: "1px {colors.glass-line}"
    backdrop: blur(16px) saturate(140%)
    rounded: "{rounded.xl}"
    padding: 24px
  trust-panel:
    backgroundColor: "{colors.glass}"
    border: "1px {colors.glass-line}"
    rounded: "{rounded.lg}"
    padding: 20px
  neu-icon-tile:
    backgroundColor: "{colors.canvas}"
    textColor: "{colors.electric-soft}"
    rounded: "{rounded.sm}"
    size: 36px
    shadow: "4px 4px 10px {colors.neu-shadow-low}, -4px -4px 10px {colors.neu-shadow-high}"
  neu-field:
    backgroundColor: "{colors.canvas}"
    border: "1px {colors.field-border}"
    rounded: 32px
    padding: 6px
    shadow: "inset 4px 4px 12px {colors.neu-shadow-low}, inset -4px -4px 12px {colors.neu-shadow-high}"
  route-node:
    backgroundColor: "{colors.canvas}"
    border: "2px {colors.hairline-strong}"
    size: 16px
  route-node-done:
    backgroundColor: "{colors.primary}"
    border: "2px {colors.primary}"
  ticker:
    backgroundColor: "rgba(11,15,23,0.50)"
    textColor: "{colors.ink-muted}"
    typography: "{typography.mono}"
    height: 52px
  screen-panel:
    backgroundColor: "{colors.screen-tint}"
    textColor: "{colors.screen-ink}"
    rounded: "{rounded.xxl}"
    padding: clamp(16px, 4vw, 40px)
  status-pill:
    backgroundColor: "transparent"
    border: "1px {colors.hairline-strong}"
    textColor: "{colors.electric-soft}"
    typography: "{typography.mono}"
    rounded: "{rounded.pill}"
    padding: 6px 12px
---

> Estructura basada en el `DESIGN.md` de Linear de [voltagent/awesome-design-md](https://github.com/voltagent/awesome-design-md) (licencia MIT). El contenido es propio de Favent. Este archivo es la fuente de verdad del diseño de la web: si el código y este documento no coinciden, se corrige uno de los dos en el mismo cambio.

## Overview

Favent es el canal de ventas profesional B2B entre empresas de servicios: quien recomienda clientes y quien presta el servicio pactan una comisión, el cliente paga una señal al reservar y la comisión se libera sola cuando se presta el servicio. El diseño tiene que transmitir eso: **un sistema técnico, fiable y en movimiento**, no una campaña de marketing.

El lienzo es oscuro: `{colors.canvas}` (#0B0F17), un azul casi negro, nunca negro puro. Encima, una textura de puntos de 22 px en blanco al 7 % y un grano muy suave le dan materia. Las tarjetas y paneles de contenido son de **vidrio esmerilado** (`{colors.glass}` con `backdrop-filter`), así que la textura y los circuitos se intuyen a través. Unos pocos elementos tienen **relieve neumórfico**: el campo de email, el selector de idioma, los iconos de confianza y los puntos del recorrido.

Hay dos acentos con funciones que no se mezclan:
- **Rosa señal** `{colors.primary}` (#FF4F9A): marca y progreso. Punto del logotipo, cuadrado de las etiquetas, línea y puntos completados del recorrido, foco de puntos que sigue al ratón.
- **Azul eléctrico** `{colors.electric}` / `{colors.electric-soft}`: energía y énfasis. Pulsos del circuito del inicio, la palabra «cobrado.» del titular, estados en mono y etiquetas sobre fondo oscuro.

Las **interfaces de ejemplo** (panel del producto, mapa, ranking, equipo y bloque final de acceso) son «pantallas encendidas»: conservan una paleta clara propia (`screen-*`) dentro del lienzo oscuro. Son las protagonistas visuales, como las capturas de producto en Linear, y siempre llevan la etiqueta «Vista de ejemplo».

**Características clave:**
- Lienzo oscuro `{colors.canvas}` con textura de puntos y grano; nunca un fondo plano sin materia.
- Rosa para la marca y el progreso, azul eléctrico para la energía. Ningún otro color de acento en el lienzo.
- Vidrio esmerilado para tarjetas y paneles de contenido; relieve neumórfico solo en controles e iconos.
- Geist 500 con tracking negativo en titulares; Geist Mono en todo lo que es dato, código o estado.
- Interfaces de ejemplo claras, siempre marcadas como ejemplo.
- Movimiento ligado al scroll o al ratón; nada se mueve solo de forma indefinida sin poder pausarse.

## Colors

> Fuente: `index.html` (variables en `:root`, `.screen`, y los estilos de cada componente).

### Brand & Accent
- **Rosa señal** ({colors.primary}): marca y progreso (logotipo, etiquetas, recorrido, foco). Como texto sobre el lienzo da unos 6,1:1, pero se reserva para acentos, no para párrafos.
- **Rosa profundo** ({colors.primary-deep}): versión para rellenos con texto blanco encima (categoría Ciclismo del mapa, unos 5,9:1).
- **Azul eléctrico** ({colors.electric}): pulsos y estelas del circuito; foco de los botones.
- **Azul eléctrico suave** ({colors.electric-soft}): texto de énfasis («cobrado.»), etiquetas de sección sobre bloques oscuros, estados en mono.
- **Destello** ({colors.electric-glow}): solo la cabeza de los pulsos del circuito.

### Surface
- **Canvas** ({colors.canvas}): fondo de toda la página.
- **Canvas profundo** ({colors.canvas-deep}): barra superior y la tarjeta oscura «Quien recomienda».
- **Surface 1** ({colors.surface-1}): base de las tarjetas cuando no hay vidrio (y valor de `--card`).
- **Surface 2** ({colors.surface-2}): fondo de iconos y elementos levantados.
- **Surface active** ({colors.surface-active}): opción activa del selector de idioma.
- **Glass** ({colors.glass}) + **Glass line** ({colors.glass-line}): vidrio esmerilado y su borde.
- **Hairline** ({colors.hairline}) y **Hairline strong** ({colors.hairline-strong}): divisores y bordes de cápsulas.
- **Field border** ({colors.field-border}): borde de los campos de formulario; mantiene 3:1 con el lienzo (WCAG 1.4.11).

### Text
- **Ink** ({colors.ink}): titulares y texto principal.
- **Ink muted** ({colors.ink-muted}): texto secundario, entradillas, etiquetas.
- **Ink subtle** ({colors.ink-subtle}): metadatos, notas pequeñas, pasos pendientes (unos 6:1).
- **Ink reveal dim** ({colors.ink-reveal-dim}): palabras todavía no reveladas de la frase grande (unos 3,8:1; solo en texto grande).

### Screens (interfaces de ejemplo)
- `screen-canvas`, `screen-surface`, `screen-tint`: fondos claros de las pantallas.
- `screen-ink`, `screen-ink-muted`, `screen-ink-subtle`: texto dentro de las pantallas.
- `screen-accent` (#2B6CA8) y `screen-accent-deep` (#0B2A4A): acentos azules dentro de las pantallas (barras, estados, enlaces).
- En CSS, cualquier elemento con `.screen`, `.fx-win` o `#demo` recupera automáticamente estos valores a través de las variables.

### Semantic
- **Error** ({colors.semantic-error}): mensajes de error sobre el lienzo.
- **Error en pantalla** ({colors.semantic-error-on-screen}): mensajes de error dentro de una pantalla clara.
- No hay verde de éxito en el lienzo: la confirmación del formulario usa una cápsula `screen-tint`.

## Typography

### Font Family
- **Geist** (Google Fonts, 400/500/600): titulares, texto y botones.
- **Geist Mono** (400/500): etiquetas de sección, códigos (FV-7K2Q), importes, estados, cinta de actividad, selector de idioma.
- **Newsreader** (500; 600 en el icono): solo el logotipo «favent.».

### Hierarchy

| Token | Tamaño | Peso | Interlineado | Tracking | Uso |
|---|---|---|---|---|---|
| `display-xl` | clamp(42px, 7vw, 84px) | 500 | 0.98 | -0.04em | Titular del inicio |
| `display-lg` | clamp(32px, 4.5vw, 52px) | 500 | 1.05 | -0.035em | H2 de sección |
| `statement` | clamp(28px, 4vw, 48px) | 500 | 1.20 | -0.03em | Frase que se revela |
| `headline` | clamp(24px, 3vw, 32px) | 500 | 1.10 | -0.025em | H3 de bloque |
| `card-title` | 22px | 500 | 1.20 | -0.02em | Títulos de tarjeta |
| `subhead` | clamp(17px, 2vw, 20px) | 400 | 1.55 | 0 | Entradilla del inicio |
| `body` | 17px | 400 | 1.55 | 0 | Párrafos de sección |
| `body-sm` | 15px | 400 | 1.55 | 0 | Texto de tarjetas |
| `caption` | 13px | 400 | 1.50 | 0 | Notas bajo formularios |
| `button` | 15px | 600 | 1.20 | 0 | Botones |
| `eyebrow` | 13px | 500 (mono) | 1.30 | 0 | Etiquetas de sección |
| `mono` | 13px | 400 (mono) | 1.50 | 0 | Datos, códigos, estados |
| `logo` | 29px | 500 (Newsreader) | 1.00 | -0.02em | Logotipo |

### Principles
- Titulares a 500, nunca a 700: el peso lo da el tamaño y el tracking negativo.
- Todo lo que es dato, código o estado va en Geist Mono. Nada de mono en párrafos.
- Las etiquetas de sección van en minúsculas (sentence case), con el cuadrado rosa delante. Nunca en mayúsculas.
- Interlineado de 1,55 en texto largo; líneas de menos de 80 caracteres (`max-width` de 520–760 px).
- Un solo énfasis de color por titular, y solo en el del inicio («cobrado.» en azul eléctrico suave).

### Note on Font Substitutes
Las tres familias son libres (Google Fonts). Si alguna no carga, el CSS cae en `sans-serif`, `monospace` y `serif`. No sustituir por Inter ni por IBM Plex: ya se probaron y se descartaron.

## Layout

### Spacing System
- Separación entre secciones: `{spacing.section}` (de 96 a 168 px según el ancho), 80 px en móvil (`--sp`).
- Dentro de una sección: 56 px entre bloques grandes, 20–24 px entre título y contenido, 14 px entre etiqueta y título.
- Tarjetas: 20–28 px de relleno interior.

### Grid & Container
- Contenedor de 1200 px con 24 px de margen lateral; el panel inicial se reduce a 12 px de margen en móvil.
- Rejillas con `auto-fit` y `minmax()`: tarjetas de 200–300 px, dúo de perfiles en 2 columnas (1 por debajo de 720 px), pasos del recorrido en 6 columnas (vertical por debajo de 860 px).

### Whitespace Philosophy
Minimalista: mucho aire entre secciones y pocas cajas. Un bloque tiene que justificar su borde: si basta con el espacio, no se dibuja contorno.

## Elevation & Depth

| Nivel | Tratamiento | Uso |
|---|---|---|
| 0 (lienzo) | `{colors.canvas}` + textura de puntos + grano | Fondo, titulares, texto suelto |
| 1 (vidrio) | `{colors.glass}`, blur 16 px, borde `{colors.glass-line}`, brillo interior de 1 px arriba, sombra 0 24px 60px rgba(0,0,0,.35) | Tarjetas, panel de confianza, detalle del recorrido, cinta, menú fijo |
| 2 (relieve) | Mismo color que el lienzo con sombra doble (oscura abajo a la derecha, clara arriba a la izquierda) o inset | Campo de email, selector de idioma, iconos, puntos del recorrido, botón «Pausar fondo» |
| 3 (pantalla encendida) | Panel claro `screen-*` con sombra larga | Interfaces de ejemplo |
| Foco | Contorno de 2 px `#2B6CA8` con 2 px de separación | Botones, enlaces y campos con `:focus-visible` |

### Decorative Depth
- **Circuito del inicio** (canvas `#net`): pistas de procesador en ángulos de 45° y 90° (`{colors.electric}` al 13 %) con contactos cuadrados y circulares. Pulsos de energía azul con estela en tres tramos y destello al llegar al contacto final. El centro va enmascarado para que el texto se lea limpio.
- **Foco de puntos rosas**: sigue al ratón por detrás del contenido (solo con ratón).
- **Paralaje**: el circuito se desplaza a un cuarto de la velocidad del scroll.
- **No usar** degradados de color visibles como fondo ni brillos de neón alrededor del texto.

## Shapes

### Border Radius Scale

| Token | Valor | Uso |
|---|---|---|
| `sm` | 12px | Iconos de confianza, pasos del recorrido |
| `md` | 16px | Filas y tarjetas pequeñas dentro de pantallas |
| `lg` | 20px | Panel de confianza, detalle del recorrido, tarjetas pequeñas |
| `xl` | 28px | Tarjetas de perfil, bloque «Entre colegas», tarjetas de reputación |
| `xxl` | 32px | Paneles de pantalla (interfaces de ejemplo, bloque de acceso) |
| `pill` | 9999px | Botones, cápsulas, campo de email, selector de idioma |

### Photography & Illustration Geometry
- Fotos solo en las tarjetas de perfil, recortadas con `object-fit: cover` en la parte superior de una tarjeta `xl`.
- Las fotos y logotipos son marcadores: sustituirlos solo con material real y con permiso.
- Iconos de trazo de 1,8 px, en línea, dentro de una baldosa neumórfica de 36 px.

## Components

### Buttons
**`button-primary`**: cápsula clara sobre el lienzo («Solicitar acceso»). Fondo `{colors.ink}`, texto `{colors.canvas}`, 52 px de alto en formularios y 40 px en el menú. Magnético con ratón (se desplaza un poco hacia el cursor).

**`button-secondary`**: cápsula azul `{colors.screen-accent}` con texto blanco («Ofrezco servicios»). 44 px.

**`button-chip`**: cápsula pequeña en mono con relieve («Pausar fondo»). 30 px.

Todos los botones: verbo al principio, 1–3 palabras, `transform: scale(.97)` al pulsar.

### Navigation
- Barra superior en `{colors.canvas-deep}` con un enlace a «Solicita acceso».
- Menú fijo (`.topnav`, sticky): transparente arriba; en cuanto la página se desplaza (`.stuck`) se vuelve de vidrio (`nav-bar-stuck`).
- Selector de idioma ES/EN con relieve hundido; la opción activa en `{colors.surface-active}`.
- Por debajo de 1020 px desaparecen los enlaces del menú; por debajo de 640 px también el botón del menú.

### Eyebrow
Etiqueta de sección en `{typography.eyebrow}` con un cuadrado rosa de 7 px delante (`.eyebrow::before`). Se «descifra» una vez al aparecer (0,65 s, caracteres aleatorios que se resuelven en el texto).

### Cards & Containers
- **`glass-card`**: tarjetas de perfil, tarjetas de reputación, funciones de equipo y bloque «Entre colegas». Se inclinan hasta 5° hacia el ratón.
- **`trust-panel`**: las cinco señales de confianza en un solo panel de vidrio con divisores; en móvil, filas con el icono a la izquierda.
- **`screen-panel`**: contenedor claro de las interfaces de ejemplo, con la etiqueta «Vista de ejemplo».

### Inputs & Forms
- **`neu-field`**: el formulario del inicio es una cápsula hundida con borde `{colors.field-border}`; el campo va transparente dentro y el botón, a la derecha (debajo en móvil).
- El formulario del bloque final vive en una pantalla clara: campo blanco y botón grafito.
- Error en `{colors.semantic-error}` (o `semantic-error-on-screen` dentro de pantallas), con `role="alert"`.
- Nota de privacidad bajo cada formulario en `{typography.caption}`.

### Route (Así se mueve una reserva)
Seis pasos unidos por una línea de 2 px. La parte recorrida y los puntos completados (`route-node-done`) en rosa; los pendientes con relieve y borde `{colors.hairline-strong}`. Debajo, el detalle del paso activo en un panel de vidrio con una `status-pill`.

### Statement (texto que se revela)
Frase en `{typography.statement}`: las palabras pasan de `{colors.ink-reveal-dim}` a `{colors.ink}` con el scroll. El texto real vive en un elemento solo para lectores de pantalla y se traduce como el resto.

### Ticker (cinta de actividad)
Franja de 52 px de vidrio con eventos de ejemplo en mono y un cuadrado rosa delante de cada uno. Se desplaza con el scroll, no sola. Siempre con la etiqueta «Actividad de ejemplo».

### Footer
Palabra gigante «favent.» en Newsreader (clamp(96px, 23vw, 320px)) con el punto rosa, el lema y «B2B SERVICE · MALLORCA». Debajo, el logotipo pequeño. Los enlaces legales están ocultos hasta que existan las páginas.

## Motion

| Elemento | Disparador | Detalle |
|---|---|---|
| Entrada del titular | Carga | Líneas que suben desde una máscara, 900 ms |
| Circuito del inicio | Continuo mientras se ve | Pulsos cada 0,2–0,6 s; más cerca del ratón; se para fuera de pantalla, con la pestaña oculta o con «Pausar fondo» |
| Panel inicial | Scroll | De inclinado 12° en 3D a plano |
| Frase que se revela | Scroll | Palabra a palabra |
| Línea de recorrido | Scroll | Fija en escritorio (240vh); vertical en móvil |
| Cinta de actividad | Scroll | Desplazamiento horizontal |
| Etiquetas | Al aparecer | Descifrado de 0,65 s, una vez |
| Tarjetas de vidrio | Ratón | Inclinación de hasta 5° |
| Botones principales | Ratón | Efecto magnético |

- Curva estándar `cubic-bezier(.23,1,.32,1)` (ease-out). Nunca `ease-in` en la interfaz.
- Animar solo `transform` y `opacity` (y el color de las palabras de la frase). Nada de animar `width`, `top` o `box-shadow` en bucle.
- Nada se mueve solo durante más de 5 s sin control para pausarlo (WCAG 2.2.2): el circuito tiene «Pausar fondo» y el panel inicial, «Pausar animación».
- Con `prefers-reduced-motion`: nada se fija, el circuito se dibuja estático, la frase aparece completa, la línea del recorrido dibujada entera, sin foco, sin inclinaciones y sin efecto magnético.

## Do's and Don'ts

### Do
- Mantener `{colors.canvas}` como única base de la página y darle materia con la textura de puntos.
- Usar el rosa solo para marca y progreso, y el azul eléctrico solo para energía y énfasis.
- Poner el contenido en vidrio y los controles con relieve; reservar las pantallas claras para las interfaces de ejemplo.
- Escribir datos, códigos y estados en Geist Mono.
- Marcar siempre los datos inventados como «Vista de ejemplo», «Actividad de ejemplo» o «servicios de ejemplo».
- Comprobar el contraste: 4.5:1 en texto normal, 3:1 en texto grande y en bordes de controles.

### Don't
- No volver a un tema claro ni a una transición de día y noche (ya se probaron y se descartaron).
- No usar naranja ni un tercer color de acento en el lienzo.
- No usar el rosa en párrafos ni como fondo de secciones.
- No usar `#000000` puro ni degradados de color visibles como fondo.
- No aplicar neumorfismo a tarjetas grandes ni a texto: solo a controles e iconos.
- No añadir apariciones con fundido en cada sección.
- No inventar cifras, clientes, testimonios ni condiciones de Favent (tarifas, plazos) en ningún componente.

## Responsive Behavior

### Breakpoints

| Nombre | Ancho | Cambios clave |
|---|---|---|
| Desktop | ≥ 1021px | Menú completo, recorrido horizontal fijo |
| Laptop | ≤ 1020px | Desaparecen los enlaces del menú |
| Tablet | ≤ 960px | Panel de confianza en filas |
| Tablet-sm | ≤ 860px | Recorrido vertical sin fijar; panel interactivo sin barra lateral |
| Mobile-lg | ≤ 720px | Perfiles en una columna |
| Mobile | ≤ 640px | Separación de 80 px, sin botón en el menú, mapa compacto, «Pausar fondo» en línea |
| Mobile-sm | ≤ 440px | Desaparece la cápsula «B2B SERVICE» |

### Touch Targets
- Botones principales de 44–52 px de alto; cápsulas de filtro de 38–44 px.
- Pins del mapa con área táctil ampliada de 28 px.
- Sin efectos hover en pantallas táctiles (`@media (hover: hover)`).

### Collapsing Strategy
- Menú: los enlaces se ocultan por debajo de 1020 px (el contenido está a un scroll).
- Recorrido: de 6 columnas fijas a lista vertical con la línea a la izquierda.
- Panel inicial: se escala para que quepa y pasa a un diseño compacto por debajo de 760 px.
- Nunca scroll horizontal, ni siquiera a 320 px.

### Image Behavior
- Fotos con `object-fit: cover` y `loading="lazy"`, con texto alternativo descriptivo.
- El mapa de Mallorca es SVG propio con la atribución «© OpenStreetMap» siempre visible.

## Iteration Guide

1. Antes de diseñar algo nuevo, elegir su nivel de elevación (lienzo, vidrio, relieve o pantalla).
2. Referenciar componentes por su nombre de token (`glass-card`, `neu-field`, `route-node`…).
3. Usar las variables CSS (`--bg`, `--ink`, `--ink-2`, `--ink-3`, `--line`, `--card`, `--eyebrow`, `--chipline`, `--signal`, `--glass`) en vez de colores escritos a mano.
4. Todo texto nuevo, también los `aria-label`, necesita su entrada en el diccionario `EN` del script.
5. Verificar en 1280 px y 390 px, en español y en inglés, y con movimiento reducido.
6. Si cambia un token, actualizar este archivo en el mismo cambio.

## Known Gaps

- Los favicons e iconos se generan a partir de HTML con las fuentes reales; si cambia el logotipo, hay que regenerarlos.
- No hay páginas legales (privacidad, condiciones) ni email de contacto: los enlaces del pie están ocultos.
- El formulario no está conectado (`FORM_ENDPOINT` vacío): muestra error en cada envío.
- Las interfaces de ejemplo tienen su propio sistema visual claro, heredado de versiones anteriores; no está documentado componente a componente.
- No se ha validado con `npx @google/design.md lint DESIGN.md`.
