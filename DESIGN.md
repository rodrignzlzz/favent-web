---
version: alpha
name: Favent-design-system
description: "Lienzo oscuro de producto B2B construido sobre #0B0F17 (azul casi negro), texto gris claro (#E9EEF6) y dos acentos con funciones separadas: rosa señal (#FF4F9A) para la marca y el progreso, y azul eléctrico suave (#4DA8FF / #7CC4FF) para la energía, el movimiento y el énfasis. La web se lee como un canal de ventas técnico y serio: Funnel Display en titulares (500, tracking negativo), Geist Mono en etiquetas, códigos e importes, y el logotipo formado por el monograma «fv» en negativo con el punto rosa (img/logo-mark-neg.png) y la palabra «favent.» en Michroma. La profundidad viene del vidrio esmerilado (glassmorfismo) sobre una textura de puntos, de algunos relieves neumórficos y de interfaces de ejemplo claras, tratadas como «pantallas encendidas». La página alterna secciones oscuras y claras. En el inicio, una rejilla de puntos que respira desde el centro, del azul al rosa."

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
    fontFamily: Funnel Display
    fontSize: clamp(42px, 7vw, 84px)
    fontWeight: 500
    lineHeight: 0.98
    letterSpacing: -0.04em
  display-lg:
    fontFamily: Funnel Display
    fontSize: clamp(32px, 4.5vw, 52px)
    fontWeight: 500
    lineHeight: 1.05
    letterSpacing: -0.035em
  statement:
    fontFamily: Funnel Display
    fontSize: clamp(28px, 4vw, 48px)
    fontWeight: 500
    lineHeight: 1.20
    letterSpacing: -0.03em
  headline:
    fontFamily: Funnel Display
    fontSize: clamp(24px, 3vw, 32px)
    fontWeight: 500
    lineHeight: 1.10
    letterSpacing: -0.025em
  card-title:
    fontFamily: Funnel Display
    fontSize: 22px
    fontWeight: 500
    lineHeight: 1.20
    letterSpacing: -0.02em
  subhead:
    fontFamily: Funnel Display
    fontSize: clamp(17px, 2vw, 20px)
    fontWeight: 400
    lineHeight: 1.55
    letterSpacing: 0
  body:
    fontFamily: Funnel Display
    fontSize: 17px
    fontWeight: 400
    lineHeight: 1.55
    letterSpacing: 0
  body-sm:
    fontFamily: Funnel Display
    fontSize: 15px
    fontWeight: 400
    lineHeight: 1.55
    letterSpacing: 0
  caption:
    fontFamily: Funnel Display
    fontSize: 13px
    fontWeight: 400
    lineHeight: 1.50
    letterSpacing: 0
  button:
    fontFamily: Funnel Display
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
    fontFamily: Michroma
    fontSize: 19px
    fontWeight: 400
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
  map-badge:
    backgroundColor: "#FFFFFF"
    textColor: "{colors.screen-ink-muted}"
    rounded: "{rounded.pill}"
    padding: 3px 10px
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

La página **alterna secciones oscuras y claras** («dark & white»). Oscuras: inicio y panel, perfiles, confianza, acceso y pie. Claras (`.light`): la frase, «Así se mueve una reserva», el panel interactivo y equipos. El lienzo oscuro es `{colors.canvas}` (#0B0F17), un azul casi negro, nunca negro puro; el claro, `{colors.screen-canvas}` (#F6F6F3). Encima, una textura de puntos de 22 px en blanco al 7 % y un grano muy suave le dan materia. Las tarjetas y paneles de contenido son de **vidrio esmerilado** (`{colors.glass}` con `backdrop-filter`), así que la textura y los circuitos se intuyen a través. Unos pocos elementos tienen **relieve neumórfico**: el campo de email, el selector de idioma, los iconos de confianza y los puntos del recorrido.

Hay dos acentos con funciones que no se mezclan:
- **Rosa señal** `{colors.primary}` (#FF4F9A): marca y progreso. Punto del logotipo, cuadrado de las etiquetas, línea y puntos completados del recorrido.
- **Azul eléctrico** `{colors.electric}` / `{colors.electric-soft}`: energía y énfasis. La rejilla del inicio (junto al rosa), la palabra «cobrado.» del titular, estados en mono y etiquetas sobre fondo oscuro.

Las **interfaces de ejemplo** (panel del producto, mapa, ranking, equipo y bloque final de acceso) son «pantallas encendidas»: conservan una paleta clara propia (`screen-*`) dentro del lienzo oscuro. Son las protagonistas visuales, como las capturas de producto en Linear, y siempre llevan la etiqueta «Vista de ejemplo».

**Características clave:**
- Secciones oscuras y claras alternas, ambas con textura de puntos (blanca al 7 % sobre oscuro, grafito al 9 % sobre claro); nunca un fondo plano sin materia.
- Rosa para la marca y el progreso, azul eléctrico para la energía. Ningún otro color de acento en el lienzo.
- Vidrio esmerilado para tarjetas y paneles de contenido; relieve neumórfico solo en controles e iconos.
- Funnel Display 500 con tracking negativo en titulares; Geist Mono en todo lo que es dato, código o estado.
- Interfaces de ejemplo claras, siempre marcadas como ejemplo.
- Movimiento ligado al scroll o al ratón, salvo la pancarta del inicio y el panel de ejemplo, que se animan solos y se pausan con un único botón de icono.

## Colors

> Fuente: `index.html` (variables en `:root`, `.screen`, y los estilos de cada componente).

### Brand & Accent
- **Rosa señal** ({colors.primary}): marca, progreso y selección (logotipo, etiquetas, recorrido, lo seleccionado en el mapa). Como texto sobre el lienzo da unos 6,1:1, pero se reserva para acentos, no para párrafos.
- **Rosa profundo** ({colors.primary-deep}): versión para rellenos con texto blanco encima (categoría Ciclismo del mapa, unos 5,9:1).
- **Azul eléctrico** ({colors.electric}): centro azul de la rejilla del inicio.
- **Azul eléctrico suave** ({colors.electric-soft}): texto de énfasis («cobrado.»), etiquetas de sección sobre bloques oscuros, estados en mono.

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
- **Funnel Display** (Google Fonts, 400/500/600): titulares, texto y botones.
- **Geist Mono** (400/500): etiquetas de sección, códigos (FV-7K2Q), importes, estados, selector de idioma.
- **Michroma** (400, único grosor): solo la palabra «favent.» del logotipo.

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
| `logo` | 19px (14px en el pie) | 400 (Michroma) | 1.00 | -0.02em | Logotipo |

### Principles
- Titulares a 500, nunca a 700: el peso lo da el tamaño y el tracking negativo.
- Todo lo que es dato, código o estado va en Geist Mono. Nada de mono en párrafos.
- Las etiquetas de sección van en minúsculas (sentence case), con el cuadrado rosa delante. Nunca en mayúsculas.
- Interlineado de 1,55 en texto largo; líneas de menos de 80 caracteres (`max-width` de 520–760 px).
- Un solo énfasis de color por titular, y solo en el del inicio («cobrado.» en azul eléctrico suave).

### Note on Font Substitutes
Las tres familias (Funnel Display, Geist Mono y Michroma) son libres (Google Fonts). Si alguna no carga, el CSS cae en `sans-serif` y `monospace`. No sustituir por Inter, IBM Plex, Geist ni Plus Jakarta Sans, ni el logotipo por Newsreader o Funnel Display: ya se probaron y se descartaron.

## Layout

### Spacing System
- Separación entre secciones: `{spacing.section}` (de 96 a 168 px según el ancho), 80 px en móvil (`--sp`).
- Dentro de una sección: 56 px entre bloques grandes, 20–24 px entre título y contenido, 14 px entre etiqueta y título.
- Tarjetas: 20–28 px de relleno interior.

### Grid & Container
- Contenedor de 1200 px con 24 px de margen lateral; el panel inicial se reduce a 12 px de margen en móvil.
- Rejillas con `auto-fit` y `minmax()`: tarjetas de 200–300 px, tres tarjetas de perfil en 3 columnas iguales (1 por debajo de 720 px), pasos del recorrido en 4 columnas (vertical por debajo de 860 px).

### Whitespace Philosophy
Minimalista: mucho aire entre secciones y pocas cajas. Un bloque tiene que justificar su borde: si basta con el espacio, no se dibuja contorno.

## Elevation & Depth

| Nivel | Tratamiento | Uso |
|---|---|---|
| 0 (lienzo) | `{colors.canvas}` + textura de puntos + grano | Fondo, titulares, texto suelto |
| 1 (vidrio) | `{colors.glass}`, blur 16 px, borde `{colors.glass-line}`, brillo interior de 1 px arriba, sombra 0 24px 60px rgba(0,0,0,.35) | Tarjetas, panel de confianza, detalle del recorrido, cinta, menú fijo |
| 2 (relieve) | Mismo color que el lienzo con sombra doble (oscura abajo a la derecha, clara arriba a la izquierda) o inset | Campo de email, selector de idioma, iconos, puntos del recorrido |
| 3 (pantalla encendida) | Panel claro `screen-*` con sombra larga | Interfaces de ejemplo |
| Foco | Contorno de 2 px `#2B6CA8` con 2 px de separación | Botones, enlaces y campos con `:focus-visible` |

### Decorative Depth
- **Rejilla que respira** (canvas `#net`, a todo el ancho): puntos cada 22 px alineados con la textura de la página; una onda radial sale del centro y los hace crecer (hasta 2,2 px de radio) y brillar, con color del azul eléctrico en el centro al rosa en los bordes. Simétrica a izquierda y derecha; el centro va enmascarado para que el texto se lea limpio. El lienzo no debe heredar la animación de entrada del titular (`.cine .intro > canvas{animation:none}`): si lo hace, pierde el centrado y solo cubre la mitad derecha. Ya se probaron y descartaron los circuitos (demasiado tech) y las ondas (asimétricas).
- **Paralaje**: la rejilla se desplaza a un cuarto de la velocidad del scroll.
- **No usar** degradados de color visibles como fondo ni brillos de neón alrededor del texto.

## Shapes

### Border Radius Scale

| Token | Valor | Uso |
|---|---|---|
| `sm` | 12px | Iconos de confianza, pasos del recorrido |
| `md` | 16px | Filas y tarjetas pequeñas dentro de pantallas |
| `lg` | 20px | Panel de confianza, detalle del recorrido, tarjetas pequeñas |
| `xl` | 28px | Tarjetas de perfil, tarjetas de reputación |
| `xxl` | 32px | Paneles de pantalla (interfaces de ejemplo, bloque de acceso) |
| `pill` | 9999px | Botones, cápsulas, campo de email, selector de idioma |

### Photography & Illustration Geometry
- Fotos solo en las tres tarjetas de perfil («Si recomiendas clientes», «Si ofreces servicios» y «Entre colegas»; `img/recomiendas.jpg`, `img/ofreces.jpg`, `img/colegas.jpg`), recortadas con `object-fit: cover` a 320 px de alto en la parte superior de una tarjeta `xl`. Las tres tarjetas son simétricas: foto, título, texto y botón alineado abajo.
- Las fotos y logotipos son marcadores: sustituirlos solo con material real y con permiso.
- Iconos de trazo de 1,8 px, en línea, dentro de una baldosa neumórfica de 36 px.

## Components

### Buttons
**`button-primary`**: cápsula clara sobre el lienzo («Solicitar acceso»). Fondo `{colors.ink}`, texto `{colors.canvas}`, 52 px de alto en formularios y 40 px en el menú.

**`button-secondary`**: cápsula azul `{colors.screen-accent}` con texto blanco («Ofrezco servicios»). 44 px.

**`button-chip`**: cápsula pequeña en mono con relieve. 30 px.

**`motion-btn`**: círculo de 36 px con relieve, abajo a la derecha del inicio, **solo con el icono** de pausa o reproducir. Pausa a la vez la rejilla y el panel de ejemplo. Es un botón conmutado: etiqueta fija «Pausar animaciones» (`aria-label`, traducida) y estado en `aria-pressed`. Oculto con movimiento reducido.

Todos los botones: verbo al principio, 1–3 palabras, `transform: scale(.97)` al pulsar.

### Logo
- **Monograma «fv»** en negativo: trazo `{colors.ink}` y punto interior `{colors.primary}`, fondo transparente (`img/logo-mark-neg.png`, 194 × 128 px, generado a partir del original `img/logo-mark.png`). Es el símbolo de la marca: se usa como icono de la pestaña, de la app y en la imagen social, pero **no** va pegado a la palabra en la cabecera ni en el pie.
- **Palabra** «favent.» en Michroma con el punto final rosa (`.logo` + `.logo-cur`, en HTML/CSS).
- **Iconos** (`img/icon-192.png`, `img/icon-512.png`, `img/apple-touch-icon.png`): el monograma «fv» en negativo al 70 % del ancho sobre `{colors.canvas}`; esquinas redondeadas y transparencia, salvo el de Apple, que es cuadrado y opaco.
- **Favicon** (`img/favicon-32.png` y `favicon.ico` con 16, 32 y 48 px): el monograma al 90 % del ancho con el punto rosa agrandado para que se vea en la pestaña.
- Los enlaces a iconos e imagen social llevan `?v=N` para que navegadores y redes descarguen la versión nueva; súbelo cada vez que cambien los archivos.
- **Imagen social** (`img/og-image.png`): monograma, palabra, «B2B SERVICE», el titular y los 4 pasos del recorrido unidos por la curva rosa, sobre el lienzo oscuro (Funnel Display).

### Navigation
- Barra superior en `{colors.canvas-deep}` con un enlace a «Solicita acceso».
- Menú fijo (`.topnav`, sticky): transparente arriba; en cuanto la página se desplaza (`.stuck`) se vuelve de vidrio (`nav-bar-stuck`).
- Selector de idioma ES/EN con relieve hundido; la opción activa en `{colors.surface-active}`.
- El menú no tiene enlaces a secciones: solo el logotipo, el botón «Solicitar acceso» y el selector de idioma. Por debajo de 640 px también se oculta el botón.

### Eyebrow
Etiqueta de sección en `{typography.eyebrow}` con un cuadrado rosa de 7 px delante (`.eyebrow::before`). Se «descifra» una vez al aparecer (0,65 s, caracteres aleatorios que se resuelven en el texto).

### Cards & Containers
- **`glass-card`**: las tres tarjetas de perfil, tarjetas de reputación y funciones de equipo. Se inclinan hasta 5° hacia el ratón.
- **`trust-panel`**: las cinco señales de confianza en un solo panel de vidrio con divisores; en móvil, filas con el icono a la izquierda.
- **`screen-panel`**: contenedor claro de las interfaces de ejemplo, con la etiqueta «Vista de ejemplo».

### Inputs & Forms
- **`neu-field`**: el formulario del inicio es una cápsula hundida con borde `{colors.field-border}`; el campo va transparente dentro y el botón, a la derecha (debajo en móvil). En móvil (≤ 640 px) el campo y el botón van separados: el campo es su propia cápsula hundida y el botón queda debajo.
- El formulario del bloque final vive en una pantalla clara: campo blanco y botón grafito.
- Error en `{colors.semantic-error}` (o `semantic-error-on-screen` dentro de pantallas), con `role="alert"`.
- Nota de privacidad bajo cada formulario en `{typography.caption}`.

### Route (Así se mueve una reserva)
Cuatro pasos (Acuerdo, Reserva y señal, Canje, Liberación; antes eran seis, se fusionaron reserva, señal y confirmación) unidos por una **curva suave** (SVG, curvas de Bézier): los pasos se alternan a dos alturas (en móvil, a dos sangrías) y la curva ondula de uno a otro. La parte recorrida se rellena en rosa y en su punta va un punto rosa luminoso con halo. Los puntos completados (`route-node-done`) en rosa con halo; los pendientes con relieve y borde `{colors.hairline-strong}`. La curva se calcula en JS a partir de la posición real de los puntos (`routeLayout`). Sin quiebros de circuito. Debajo, el detalle del paso activo en un panel de vidrio con una `status-pill`.

### Statement (texto que se revela)
Frase en `{typography.statement}`: las palabras pasan de `{colors.ink-reveal-dim}` a `{colors.ink}` con el scroll. El texto real vive en un elemento solo para lectores de pantalla y se traduce como el resto.

### Map (mapa de servicios)
**La sección «Mapa de servicios» está oculta** (`hidden`): el mapa solo se ve dentro del panel interactivo, en la vista «Buscar servicios». No se borra porque esa vista reutiliza lo que pinta la sección (`fxMap()` toma sus puntos, categorías y lista) y comparte su estado.

**Menú de los dos paneles (el animado del inicio y el interactivo, perfil «Si recomiendas»):** Inicio, Buscar servicios, Reservas, Colaboradores, Mensajes e Informes, y al pie de la barra lateral, separados por una línea, Ajustes y Cuenta (no navegan). El Inicio del panel interactivo repite el del inicio: saludo, cifras de comisión (de ejemplo), últimas reservas y botón «Ver todas las reservas». Sin «Acuerdos», «Socios» ni listas de categorías.

**Colaboradores (los dos perfiles):** dos empresas colaboran solo cuando ambas aceptan la solicitud. La vista «Colaboradores» muestra arriba un bloque «Solicitudes» (`cl-req`, pantalla con tinte `screen-tint` claro): las recibidas con «Aceptar» (botón `fx-btn accent`) y «Rechazar» (`fx-btn ghost`), las enviadas con «Esperando respuesta», y la nota «Las dos empresas deben aceptar la solicitud para colaborar.»; debajo, la tabla de colaboradores con la etiqueta «Colaborador» en `screen-tint` / `screen-accent-deep`, y «+ Invitar empresa» en la barra. En el perfil «Si ofreces servicios», la Agenda termina con «Colaboradores para pasar reservas» (`cl-pass`, tarjetas `cl-card`): solo colegas con estado de colaborador y el botón «Pasar reserva». En «Buscar servicios», el filtro «Solo colaboradores» va en la barra superior, junto al número de servicios; activo va en rosa (es una elección del usuario) y deja en el mapa y en la lista solo las empresas colaboradoras, que llevan la etiqueta «Colaborador» en su tarjeta. En «Buscar servicios» cada servicio visible lleva una etiqueta pequeña azul (`fx-tag`, fondo `{colors.screen-accent}`, sin foto): arriba el lugar y debajo «precio | %» en Geist Mono, con una flecha hacia su punto. `placeTags()` coloca cada etiqueta arriba, abajo o desplazada a un lado para que no se pisen. La seleccionada pasa a rosa. Al seleccionar un servicio, la columna derecha cambia la lista por una pestañita de detalle (`fx-detail`, borde rosa): foto o icono, nombre, servicio y lugar, descripción, precio total, comisión, señal y valoración, con «Ir al chat para reservar» (abre o crea la conversación con esa empresa en Mensajes) y «Ver todos» para volver a la lista; en móvil aparece bajo el mapa. Con «Solo colaboradores» activo solo quedan las etiquetas de las empresas colaboradoras. El panel animado del inicio, tras firmar el acuerdo y pasar por Colaboradores, vuelve a Buscar servicios, pulsa «Solo colaboradores» (mismas etiquetas, sin foto), elige Cala d’Or Charters y pulsa «Reservar», que lleva al Inicio con la reserva. En el perfil «Si ofreces servicios», la pestaña Colaboradores y la Agenda terminan con «Servicios disponibles de tus colaboradores» (`cl-svc`): las mismas tarjetas que la lista del mapa, con la señal del servicio y «Pasar reserva».

**Señal:** la ficha del mapa, las tarjetas de servicio y las fichas de reserva muestran la señal elegida por quien presta el servicio («Solo la comisión» o «50 % del total») y, en las reservas de quien presta el servicio, el desglose: comisión del socio, lo que recibe al canjear y lo que queda por cobrar en su oficina.

Solo filtros por categoría (sin botones de orden). **Todo va en azul** (`{colors.screen-accent}`). Al cargar no hay nada en rosa: la categoría y el punto seleccionados por defecto van en azul (`{colors.screen-accent}` / `{colors.screen-accent-deep}`). En cuanto el usuario pulsa una categoría o un punto (`S.mapPink`), el **rosa marca solo lo seleccionado** (en el mapa del panel de ejemplo del inicio, lo que selecciona la animación también va en rosa): la categoría elegida, el punto pulsado (fondo `{colors.primary}` con texto `{colors.canvas}`), el borde de su ficha emergente, su tarjeta en la lista y la etiqueta de comisión de la barra inferior. El mapa es una pantalla clara con la etiqueta «Servicios de ejemplo» (`map-badge`) arriba a la izquierda. En escritorio, la lista de servicios va a la derecha; en móvil se oculta, el mapa ocupa todo el ancho y las categorías van en una sola fila deslizable, sin contador.

### Footer
Palabra gigante «favent.» en Michroma (clamp(52px, 14.5vw, 205px), interlineado 1,25 para que no se corte) con el punto rosa, el lema y «B2B SERVICE · MALLORCA». Debajo, el logotipo pequeño. Los enlaces legales están ocultos hasta que existan las páginas.

## Motion

| Elemento | Disparador | Detalle |
|---|---|---|
| Entrada del titular | Carga | Líneas que suben desde una máscara, 900 ms |
| Rejilla del inicio | Continuo mientras se ve | Dos ondas (radial desde el centro y diagonal) más un anillo brillante cada 3,2 s; se para fuera de pantalla, con la pestaña oculta o con el botón de pausa |
| Panel inicial | Scroll | De inclinado 12° en 3D a plano |
| Frase que se revela | Scroll | Palabra a palabra |
| Línea de recorrido | Scroll | Fija en escritorio (200vh); vertical en móvil |
| Etiquetas | Al aparecer | Descifrado de 0,65 s, una vez |
| Tarjetas de vidrio | Ratón | Inclinación de hasta 5° |

- Curva estándar `cubic-bezier(.23,1,.32,1)` (ease-out). Nunca `ease-in` en la interfaz.
- Animar solo `transform` y `opacity` (y el color de las palabras de la frase). Nada de animar `width`, `top` o `box-shadow` en bucle.
- Nada se mueve solo durante más de 5 s sin control para pausarlo (WCAG 2.2.2): la rejilla del inicio y el panel de ejemplo se pausan con el botón de icono `motion-btn`. Con `prefers-reduced-motion` todo queda estático, y las animaciones se paran fuera de pantalla y con la pestaña oculta.
- Con `prefers-reduced-motion`: nada se fija, la rejilla se dibuja estática, la frase aparece completa, la línea del recorrido dibujada entera y sin inclinaciones.

## Do's and Don'ts

### Do
- Mantener `{colors.canvas}` como única base de la página y darle materia con la textura de puntos.
- Usar el rosa solo para marca y progreso, y el azul eléctrico solo para energía y énfasis.
- Poner el contenido en vidrio y los controles con relieve; reservar las pantallas claras para las interfaces de ejemplo.
- Escribir datos, códigos y estados en Geist Mono.
- Marcar siempre los datos inventados como «Vista de ejemplo», «Servicios de ejemplo» o «Ejemplo».
- Comprobar el contraste: 4.5:1 en texto normal, 3:1 en texto grande y en bordes de controles.

### Don't
- No volver a un tema todo claro ni todo oscuro, ni a la transición de día y noche ni a los circuitos de procesador (ya se probaron y se descartaron).
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
| Tablet | ≤ 960px | Panel de confianza en filas |
| Tablet-sm | ≤ 860px | Recorrido vertical sin fijar; panel interactivo sin barra lateral |
| Mobile-lg | ≤ 720px | Perfiles en una columna |
| Mobile | ≤ 640px | Separación de 80 px, sin botón en el menú, mapa a todo el ancho sin lista lateral |
| Mobile-sm | ≤ 440px | Desaparece la cápsula «B2B SERVICE» |

### Touch Targets
- Botones principales de 44–52 px de alto; cápsulas de filtro de 38–44 px.
- Pins del mapa con área táctil ampliada de 28 px.
- Sin efectos hover en pantallas táctiles (`@media (hover: hover)`).

### Collapsing Strategy
- Menú: sin enlaces a secciones en ningún tamaño; por debajo de 640 px tampoco el botón.
- Recorrido: de 4 columnas fijas a lista vertical con la línea a la izquierda.
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
