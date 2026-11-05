# Favent — web pública (favent.app)

> **Diseño:** todo el diseño debe seguir [`DESIGN.md`](DESIGN.md), que es la fuente de verdad visual del proyecto.

## Qué es Favent
Favent es el canal de ventas profesional B2B entre empresas de servicios. Quien recomienda clientes y quien presta el servicio pactan una comisión; la reserva se paga por adelantado con una señal (vía Stripe), queda retenida y la comisión se libera automáticamente cuando se presta el servicio (canje por código QR).

- Mercado inicial: Mallorca (náutico: chárter privado, yates, veleros, lanchas; también traslados, ciclismo y servicios privados). Test en Varsovia en estudio.
- Dos flujos: (1) quien recomienda → quien presta el servicio; (2) entre colegas: un proveedor lleno pasa la reserva (o parte) a otro y cobra comisión.
- Señal (en prueba): la elige quien presta el servicio, en cada servicio. (a) Solo la comisión: al canjear el QR se libera la comisión a quien recomendó y el resto se cobra en la oficina. (b) 50 % del total: al canjear el QR se liberan la comisión a quien recomendó y el resto de ese 50 % a quien presta el servicio; el otro 50 % se cobra en la oficina.
- Servicios publicados: cada empresa puede registrar todos los servicios que quiera, pero publicar como máximo 2 a la vez; cada servicio publicado se presenta por separado (su propia etiqueta y ficha en el mapa).
- Cada servicio se nombra con el nombre del barco (o del recurso) y el servicio, p. ej. «Zafiro — Barco privado · 12 pax · bebida incluida». La disponibilidad no se fija en el servicio: se lleva en la Agenda, que es una agenda completa con todos los servicios dados de alta (publicados o no). Quien presta el servicio apunta ahí sus propias reservas (teléfono, web, en persona…) como en cualquier agenda; las reservas hechas con Favent se apuntan solas en su salida, con el cliente, las personas y quien la recomendó.
- La Agenda es uno de los productos centrales: debe verse como un calendario profesional (vistas Día, Semana y Mes; productos en columnas y días/horas hacia abajo; un color por producto). Las empresas de barcos suelen tener 5–6 productos.
- Colaboradores: dos empresas colaboran solo cuando ambas aceptan la solicitud. Quien ofrece servicios solo puede pasar reservas a sus colaboradores. Quien recomienda puede filtrar el mapa por «Solo colaboradores».
- Fundadores: Rodrigo (negocio) y un socio ingeniero (producto).

## Este repositorio
- Solo contiene la **web pública de presentación y lista de espera**. La app (PWA en Next.js + Supabase + Stripe Connect) irá en otro repositorio y en un subdominio (p. ej. app.favent.app). No construir la app aquí.
- Alojamiento: **GitHub Pages**, rama `main`, carpeta raíz. Cada push a `main` se publica en https://www.favent.app.
- **No borrar ni modificar el archivo `CNAME`** (contiene `www.favent.app`).
- Web estática: un único `index.html` con CSS y JS en línea, sin build ni dependencias. Mantenerlo así salvo que se pida lo contrario. Si se añaden páginas (privacidad, aviso legal, cookies), crear archivos `.html` en la raíz con el mismo estilo.
- El mapa es un SVG propio: costa de Mallorca y Dragonera de OpenStreetMap (paquete `@geo-maps/earth-lands-100m`, ODbL; atribución «© OpenStreetMap» obligatoria en el mapa), con Serra de Tramuntana, carreteras principales esquemáticas, pueblos y bahías. Los pins se colocan por latitud/longitud con `proj()`. Sin librerías ni mosaicos externos.
- GitHub Pages no permite backend ni pagos: los formularios deben enviar a un servicio externo (Formspree, Supabase, etc.).

## Marca
**Todo el diseño de la web debe seguir [`DESIGN.md`](DESIGN.md)**: colores, tipografía, espaciado, elevación (vidrio, relieve, pantallas), componentes, movimiento y comportamiento responsive. Antes de cambiar algo visual, léelo; si un cambio introduce o modifica un token o un componente, actualiza `DESIGN.md` en el mismo cambio. Si el código y `DESIGN.md` no coinciden, avisa y corrige uno de los dos.

Resumen (el detalle está en `DESIGN.md`):
- Nombre: siempre **favent** en minúscula en el logotipo, "Favent" en el texto. Etiqueta secundaria: **B2B SERVICE**.
- Logotipo: la palabra «favent.» en Michroma con punto rosa (`.logo` + `.logo-cur`). El monograma «fv» en negativo con el punto interior rosa (`img/logo-mark-neg.png`, del original `img/logo-mark.png`) es el icono: favicon (`img/favicon-32.png`, `favicon.ico`), iconos de app (`img/icon-192.png`, `img/icon-512.png`, `img/apple-touch-icon.png`) e imagen social (`img/og-image.png`). No va pegado a la palabra. Si cambian, regenerarlos y subir el `?v=N` de sus enlaces.
- Tema «dark & white»: secciones oscuras (`#0B0F17`, texto `#E9EEF6`) y claras (`.light`, `#F6F6F3`) alternas; rosa señal `#FF4F9A` (marca y progreso) y azul eléctrico `#4DA8FF` / `#7CC4FF` (energía y énfasis). Las interfaces de ejemplo son «pantallas encendidas» claras.
- Tipografías: Funnel Display (titulares y texto), Geist Mono (etiquetas, códigos, importes, estados), Michroma (solo la palabra del logotipo).
- Sin naranja, sin degradados de color visibles, sin emojis, sin transición de día y noche.

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
1. Formulario de acceso a **info@favent.es**: con la clave de Web3Forms en `WEB3FORMS_KEY` se envía por Web3Forms (cuenta creada con info@favent.es); sin clave, por FormSubmit (`https://formsubmit.co/ajax/info@favent.es`, exige activar por correo). Si falla, el aviso abre un email ya escrito a info@favent.es. Email de contacto en el pie: info@favent.es. Al publicar la política de privacidad, mencionar FormSubmit como encargado del tratamiento.
1b. Dominio favent.es: redirigir (301) a https://www.favent.app desde el proveedor del dominio; GitHub Pages solo admite un dominio por repositorio y el `CNAME` se queda en www.favent.app.
2. Páginas legales: aviso legal, política de privacidad y cookies (RGPD/LSSI). Enlazarlas desde el pie.
3. Sustituir marcadores de logos y fotos cuando haya material real.
4. Versión en inglés (y quizá polaco) de la web.
5. Metadatos para compartir (Open Graph, imagen social).

## Favent 2.0: expansión futura (no reflejar en la web todavía)
- Favent Catalog (`catalog.favent.app`, escaparate para el cliente final; p. ej. el huésped desde su habitación) y Connect Spot (establecimientos físicos, como hoteles, que recomiendan) son una capa aparte que se introducirá más adelante, sobre el mismo motor: servicios publicados, Agenda, señal, QR y comisiones. No cambian el núcleo B2B.
- Regla clave: el cliente final solo ve precios totales, nunca comisiones; aun así, la comisión de lo que reserva desde un hotel va para ese hotel.
- A Catalog solo se entra desde un Connect Spot (sin acceso público). Los spots los da de alta Favent en su software. La atribución va en el enlace: si el huésped entra más tarde desde fuera, la comisión sigue siendo de ese hotel; si abre el enlace de otro spot, cuenta el último. QR por hotel o por habitación. Sin perfiles de cliente: le llega un enlace, reserva pagando una parte y el resto en persona, igual que en Favent. El Administrador del hotel elige qué ve el huésped: «Solo colaboradores» (comisión pactada entre las dos empresas) o «Todo libre» (comisión que fija quien presta el servicio).
- Favent hace de marketplace y garantía de cobro para las dos partes (sobre todo para quien recomienda). Ingresos: un precio por cada QR necesario (habitación, casa…) más una tarifa mensual, que pagan sobre todo los hoteles (quien presta el servicio también puede pedir QR para referenciar a sus clientes, aunque puede hacerlo desde la app); importes por definir, no publicar cifras. Más adelante, el cliente pagará unos pequeños «gastos de gestión» (cubren Stripe/Mangopay y la protección del pago), siempre incluidos en el precio total desde la primera pantalla y nunca llamados «comisión» ni «seguro».
- Detalle y equivalencias con lo que ya existe: [`docs/favent-2.0-auditoria-y-plan.md`](docs/favent-2.0-auditoria-y-plan.md).
- No mencionarlos en `index.html` hasta que se decida lanzarlos. Catalog no se construye en este repositorio.

## Contexto legal y de negocio (no reflejar en la web sin validar)
- Marca: existe una marca española registrada "Faventy" (clase 42). Pendiente opinión de un agente de marcas antes de registrar "Favent".
- Pagos previstos: Stripe Connect (cargos y transferencias separados). En Polonia, BLIK (solo PLN).
- Estructura prevista: sp. z o.o. en Polonia, venta principal en España.
