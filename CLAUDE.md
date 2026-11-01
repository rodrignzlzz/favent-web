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
- Logotipo: «favent» en **IBM Plex Mono** 500 (tracking −0,05 em) seguido de un bloque naranja tipo cursor (`.logo` + `.logo-cur`, en HTML y CSS, no en imagen). Al cargar, el cursor parpadea cuatro veces. En el pie va en pequeño y como palabra gigante al final de la página.
- Etiqueta secundaria: **B2B SERVICE** (en mono).
- Símbolo antiguo: el monograma «fv» de `img/logo-mark.png` ya no se usa en la web. Los favicons e iconos (`img/favicon-32.png`, `img/icon-192.png`, `img/icon-512.png`, `img/apple-touch-icon.png`) y la imagen social `img/og-image.png` aún son los antiguos y hay que rehacerlos con el logotipo nuevo.
- Colores (día):
  - Fondo (blanco hueso): `#F6F6F3` · Tarjetas: `#FFFFFF`
  - Tinta (grafito): `#1E2226` · Texto secundario: `#50565C` · Terciario: `#656B71`
  - Líneas: `#E6E7E3`, `#D5D7D3`
  - Acento azul: `#2B6CA8` (rellenos, barras, estados; texto blanco encima) · Azul profundo: `#0B2A4A` (texto de acento)
  - Cielo: `#A9D3F0` (sobre fondo oscuro) · Tinte: `#EAF2F8` · Suave: `#D3E6F4`
  - Naranja señal: `#F2551C` (`--signal`). Solo como acento: cursor del logotipo, viñeta de las etiquetas, sol de la escena, barra de progreso. Nunca en texto pequeño: sobre blanco hueso no llega a 4.5:1. Para un punto del mapa sobre blanco se usa `#D9480F`.
- Noche (zona inferior de la web, desde «Así se mueve una reserva»):
  - Fondo: `#0C1622` · Tarjetas: `#12202F` · Líneas: `#1E2E40`
  - Texto: `#EEF2F6`, secundario `#AEBBC8`, terciario `#8796A6` · Etiquetas: `#A9D3F0`
  - Los colores van como variables CSS (`--bg`, `--ink`, `--ink-2`, `--ink-3`, `--line`, `--card`, `--eyebrow`, `--chipline`) en `:root` (día) y `.night` (noche). Las interfaces de ejemplo (`.screen`, `.fx-win`) son «pantallas encendidas» y mantienen los colores de día dentro de la noche.
- Tipografías (Google Fonts): **IBM Plex Sans** (titulares 500 con tracking −0,035 em; texto 400) e **IBM Plex Mono** (logotipo, etiquetas, códigos, importes, estados).
- Etiquetas de sección: `.eyebrow`, en mono 13 px, con un cuadrado naranja de 7 px delante. En minúsculas, nunca en mayúsculas.
- Transición «ventana que se abre»: en la escena fijada «Así se mueve una reserva», el cielo empieza como una tarjeta (escala 0,8 y esquinas de 28 px) sobre la página de día y se abre a pantalla completa en el primer 22 % del recorrido. Después pasa del día a la noche (`#DCEEFA` → `#A9D3F0` → `#2B6CA8` → `#0B2A4A` → `#0C1622`). Dos capas de la Serra de Tramuntana suben a distinta velocidad para dar profundidad, el sol naranja se pone tras las montañas, sale la luna y aparecen las estrellas. El texto cambia de tinta cuando la luminancia del cielo baja de 0,18, para mantener 4.5:1 con ambas tintas. En móvil, el sol y la luna van por la franja superior para no cruzar el titular.
- Estilo: minimalista y técnico; mucho aire entre secciones (`--sp`: de 96 a 168 px en escritorio, 80 px en móvil), un solo acento de color y el naranja como señal, esquinas redondeadas (tarjetas 20–32 px, botones en forma de cápsula), sombras suaves, sin degradados de color visibles ni emojis.
- Texturas: grano muy suave en toda la página (`body::after`, SVG `feTurbulence`) y retícula de 56 px detrás del titular. Siempre sutiles; nunca por encima de la legibilidad.
- Movimiento: pocas escenas y bien orquestadas:
  - entrada del titular por líneas al cargar;
  - parpadeo del cursor del logotipo;
  - panel inicial que pasa de inclinado en 3D a plano al hacer scroll;
  - la escena de la ventana;
  - botones magnéticos (solo con ratón).

  Curva `cubic-bezier(.23,1,.32,1)`, animar solo `transform` y `opacity`, sin apariciones al hacer scroll en cada sección. Con `prefers-reduced-motion` no se fija nada y la escena se muestra estática de noche.
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
