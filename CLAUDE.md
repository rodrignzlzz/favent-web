# Favent — web pública (favent.app)

## Qué es Favent
Favent es el canal de ventas profesional B2B entre empresas de servicios. Quien recomienda clientes y quien presta el servicio pactan una comisión; la reserva se paga por adelantado con una señal (vía Stripe), queda retenida y la comisión se libera automáticamente cuando se presta el servicio (canje por código QR).

- Mercado inicial: Mallorca (náutico: chárter privado, yates, catamaranes; también ciclismo, eventos, alquiler de material). Test en Varsovia en estudio.
- Dos flujos: (1) quien recomienda → quien presta el servicio; (2) entre colegas: un proveedor lleno pasa la reserva (o parte) a otro y cobra comisión.
- Fundadores: Rodrigo (negocio) y un socio ingeniero (producto).

## Este repositorio
- Solo contiene la **web pública de presentación y lista de espera**. La app (PWA en Next.js + Supabase + Stripe Connect) irá en otro repositorio y en un subdominio (p. ej. app.favent.app). No construir la app aquí.
- Alojamiento: **GitHub Pages**, rama `main`, carpeta raíz. Cada push a `main` se publica en https://www.favent.app.
- **No borrar ni modificar el archivo `CNAME`** (contiene `www.favent.app`).
- Web estática: un único `index.html` con CSS y JS en línea, sin build ni dependencias. Mantenerlo así salvo que se pida lo contrario. Si se añaden páginas (privacidad, aviso legal, cookies), crear archivos `.html` en la raíz con el mismo estilo.
- El mapa es un SVG propio: costa de Mallorca y Dragonera de OpenStreetMap (paquete `@geo-maps/earth-lands-100m`, ODbL; atribución «© OpenStreetMap» obligatoria en el mapa), con Serra de Tramuntana, carreteras principales esquemáticas, pueblos y bahías. Los pins se colocan por latitud/longitud con `proj()`. Sin librerías ni mosaicos externos.
- GitHub Pages no permite backend ni pagos: los formularios deben enviar a un servicio externo (Formspree, Supabase, etc.).

## Marca
Sistema «Grafito y señal» (noviembre de 2026): grafito, blanco hueso frío, azul cielo y un toque de naranja señal.

- Nombre: siempre **favent** en minúscula en el logotipo, "Favent" en el texto.
- Logotipo: «favent» en **Newsreader** 500 (serif, tracking −0,02 em) con un punto final naranja redondo (`.logo` + `.logo-cur`, en HTML y CSS, no en imagen). En la cabecera, en pequeño en el pie y como palabra gigante al final de la página.
- Etiqueta secundaria: **B2B SERVICE** (en mono).
- Icono: «f.» en Newsreader 600 color hueso con el punto naranja, sobre un cuadrado grafito (`img/favicon-32.png`, `img/icon-192.png` e `img/icon-512.png` con esquinas redondeadas y transparencia; `img/apple-touch-icon.png` cuadrado y opaco porque iOS redondea solo).
- Imagen social `img/og-image.png` (1200 × 630): fondo hueso con retícula, logotipo, «B2B SERVICE», el titular «Cada cliente que envías, cobrado.» y la línea de recorrido con los seis pasos.
- El monograma antiguo «fv» (`img/logo-mark.png`) ya no se usa.
- Colores (día):
  - Fondo (blanco hueso): `#F6F6F3` · Tarjetas: `#FFFFFF`
  - Tinta (grafito): `#1E2226` · Texto secundario: `#50565C` · Terciario: `#656B71`
  - Líneas: `#E6E7E3`, `#D5D7D3`
  - Acento azul: `#2B6CA8` (rellenos, barras, estados; texto blanco encima) · Azul profundo: `#0B2A4A` (texto de acento)
  - Cielo: `#A9D3F0` (sobre fondo oscuro) · Tinte: `#EAF2F8` · Suave: `#D3E6F4`
  - Naranja señal: `#F2551C` (`--signal`). Solo como acento: punto del logotipo, viñeta de las etiquetas, línea y puntos del recorrido. Nunca en texto pequeño: sobre blanco hueso no llega a 4.5:1. Para la categoría Ciclismo del mapa (con texto blanco encima) se usa `#C2410C`.
- Los colores van como variables CSS (`--bg`, `--ink`, `--ink-2`, `--ink-3`, `--line`, `--card`, `--eyebrow`, `--chipline`) en `:root`. Toda la página es clara; los únicos bloques oscuros son «Entre colegas» y la tarjeta «Quien recomienda» (grafito `#1E2226`).
- Tipografías (Google Fonts): **IBM Plex Sans** (titulares 500 con tracking −0,035 em; texto 400), **IBM Plex Mono** (etiquetas, códigos, importes, estados) y **Newsreader** (solo el logotipo).
- Etiquetas de sección: `.eyebrow`, en mono 13 px, con un cuadrado naranja de 7 px delante. En minúsculas, nunca en mayúsculas.
- Efectos ligados al scroll:
  - **Texto que se revela** (`#idea`): la frase «Quien recomienda y quien presta el servicio pactan la comisión…» pasa de gris `#7C8288` (3,6:1, texto grande) a grafito palabra a palabra al bajar. Las palabras se generan en JS desde un texto oculto para lectores de pantalla, que también se traduce.
  - **Línea de recorrido** (`#como`): una línea naranja une los seis pasos de «Así se mueve una reserva» y se dibuja con el scroll; cada punto se rellena al llegar la línea y el paso activo muestra su detalle. En escritorio la sección se queda fija (240vh); en móvil la línea es vertical y no fija nada.
- Elementos interactivos:
  - **Red de empresas** (`#net`, canvas en el fondo del inicio): nodos y conexiones en grafito muy suave. Cerca del ratón se encienden en naranja y por la red viajan «referencias» (puntos naranjas). Al cargar viajan unas pocas (menos de 3 s); después solo se mueve con el ratón y con un paralaje ligado al scroll. Nada se mueve solo de forma continua, para cumplir WCAG 2.2.2.
  - **Cinta de actividad de ejemplo** (`.ticker`, bajo el formulario del inicio): eventos de ejemplo en mono que se desplazan con el scroll, no solos. Marcada como «Actividad de ejemplo».
  - **Calculadora** (`#calcula`, «Haz la cuenta»): precio y comisión pactada con deslizadores; muestra la comisión y la señal (igual a la comisión, retenida hasta el canje), con el número animado. «Simular la reserva» recorre los cuatro estados. Es un cálculo orientativo: no añadir tarifas ni condiciones de Favent sin validarlas.
  - **Etiquetas que se descifran**: las `.eyebrow` (mono) se descifran una vez al aparecer, en 0,65 s.
  - **Tarjetas `.lift`**: se inclinan hasta 5° hacia el ratón.
- Estilo: minimalista y técnico; mucho aire entre secciones (`--sp`: de 96 a 168 px en escritorio, 80 px en móvil), un solo acento de color y el naranja como señal, esquinas redondeadas (tarjetas 20–32 px, botones en forma de cápsula), sombras suaves, sin degradados de color visibles ni emojis.
- Texturas: retícula de puntos de 22 px en todo el fondo, con un foco de puntos naranjas que sigue al ratón (`.spot`, capa con `z-index:-1` detrás del contenido; solo con ratón), y grano muy suave (`body::after`, SVG `feTurbulence`). Siempre sutiles; nunca por encima de la legibilidad.
- Movimiento: pocas escenas y bien orquestadas:
  - entrada del titular por líneas al cargar;
  - panel inicial que pasa de inclinado en 3D a plano al hacer scroll;
  - el texto que se revela y la línea de recorrido;
  - la red de empresas, el foco de puntos, la cinta de actividad, las etiquetas que se descifran y las tarjetas que se inclinan;
  - botones magnéticos (solo con ratón).

  Curva `cubic-bezier(.23,1,.32,1)`, animar solo `transform` y `opacity`, sin apariciones al hacer scroll en cada sección. Con `prefers-reduced-motion` no se fija nada: el texto se muestra completo y la línea dibujada entera; la red se dibuja estática, sin foco ni inclinación; la cinta se puede desplazar a mano y la simulación salta al estado final.
- Referencias de estilo: Linear, Vercel, Stripe, Mercury, Attio.

## Textos y tono
- Idioma principal: **español**. Directo, profesional, cercano.
- Expresión clave: "canal de ventas profesional".
- **No usar** "comisionistas", "prescriptores" ni "proveedores" en la web. Usar: "quien recomienda", "quien ofrece / presta el servicio", "las dos empresas", "Si recomiendas", "Si ofreces servicios".
- No mencionar WhatsApp ni el efectivo como problema en el copy; hablar de "la forma profesional de gestionar tus comisiones".
- Ubicación en el copy: **Mallorca** (no Pollença/Alcúdia).
- Lema corto: "Cada cliente que envías, cobrado."
- Inglés (para futuras versiones): "Favent is the B2B sales channel for service businesses: partners agree on a commission, every referred booking is prepaid, and the commission is released automatically once the service is delivered."

## Honestidad del contenido
- No inventar clientes, logos, cifras, reseñas ni testimonios presentados como reales.
- Los datos del panel del producto y del mapa son **de ejemplo** y deben seguir marcados como tales ("Vista de ejemplo", "servicios de ejemplo") hasta tener datos reales autorizados.
- Los huecos de logos y fotos son marcadores: sustituirlos solo con material real y con permiso.

## Accesibilidad y calidad
- HTML semántico: `<button>`, `<a href>`, `<label>` en formularios; `aria-label` en botones solo con icono.
- Contraste de texto mínimo 4.5:1.
- Debe funcionar en móvil (390 px) sin scroll horizontal.
- Respetar `prefers-reduced-motion`.

## Pendientes conocidos
1. Conectar el formulario de acceso: rellenar `FORM_ENDPOINT` en el script (Formspree o Supabase).
2. Páginas legales: aviso legal, política de privacidad y cookies (RGPD/LSSI). Enlazarlas desde el pie.
3. Sustituir marcadores de logos y fotos cuando haya material real.
4. Versión en inglés (y quizá polaco) de la web.
5. Metadatos para compartir (Open Graph, imagen social).

## Contexto legal y de negocio (no reflejar en la web sin validar)
- Marca: existe una marca española registrada "Faventy" (clase 42). Pendiente opinión de un agente de marcas antes de registrar "Favent".
- Pagos previstos: Stripe Connect (cargos y transferencias separados). En Polonia, BLIK (solo PLN).
- Estructura prevista: sp. z o.o. en Polonia, venta principal en España.
