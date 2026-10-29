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
- Única dependencia externa: el mapa real usa **Leaflet 1.9.4** (unpkg, con `integrity`) y mosaicos **CARTO Voyager** (atribución OpenStreetMap/CARTO obligatoria). Si Leaflet no carga, el listado del mapa sigue funcionando.
- GitHub Pages no permite backend ni pagos: los formularios deben enviar a un servicio externo (Formspree, Supabase, etc.).

## Marca
- Nombre: siempre **favent** en minúscula en el logotipo (con un punto azul al final), "Favent" en el texto.
- Etiqueta secundaria: **B2B SERVICE**.
- Colores:
  - Acento (azul suave): `#3F6FD8`
  - Texto sobre acento: `#FFFFFF`
  - Acento texto oscuro: `#274586`
  - Tinte de fondo: `#E7ECF5`
  - Suave: `#D8E1F2`
  - Brillante (sobre fondo oscuro): `#8CA9E8`
  - Negro: `#0F1110`
  - Fondo: `#FAFAF8`
  - Grises de texto: `#4C504D`, `#6A6E6B`; líneas: `#ECEDE9`, `#DADBD6`
- Tipografías (Google Fonts): **Inter Tight** (titulares, 600–700, tracking negativo), **Inter** (texto), **DM Mono** (códigos, importes, estados).
- Estilo: minimalista, serio y social a la vez; mucho blanco, un solo color de acento, esquinas redondeadas (tarjetas 20–32 px, botones y etiquetas en forma de cápsula), sombras suaves, sin degradados ni emojis.
- Referencias de estilo: Attio, Mercury, Stripe, Qonto, Webflow.

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
