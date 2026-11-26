# Favent — web pública (favent.app)

> **Diseño:** todo el diseño debe seguir [`DESIGN.md`](DESIGN.md), que es la fuente de verdad visual del proyecto.

## Qué es Favent
Favent es el canal de ventas profesional B2B entre empresas de servicios. Quien recomienda clientes y quien presta el servicio pactan una comisión; la reserva se paga por adelantado con una señal (vía Stripe), queda retenida y la comisión se libera automáticamente cuando se presta el servicio (canje por código QR).

- Mercado inicial: Mallorca (náutico: chárter privado, yates, veleros, lanchas; también traslados, ciclismo y servicios privados). Expansión prevista (decisión de Rodrigo, 25 nov 2026): resto de España, México y Argentina, hacia 2029. El test en Varsovia queda aplazado.
- Dos flujos: (1) quien recomienda → quien presta el servicio; (2) entre colegas: un proveedor lleno pasa la reserva (o parte) a otro y cobra comisión.
- Señal: la elige quien presta el servicio, en cada servicio. Al canjear el QR se liberan la comisión a quien recomendó y el resto de la señal a quien presta el servicio. (a) 50 % del total: el otro 50 % se cobra en la oficina. (b) 100 % del total: no queda nada por cobrar en la oficina. Ya no existe «Solo la comisión» (igual que en la app).
- Gastos de gestión (24 nov 2026): el cliente paga un 3,25 % de lo que se paga en la app (la señal), no del total. Ni quien presta el servicio ni quien recomienda pagan nada por reserva (antes, desde el 19 nov, 2 % el cliente y 2 % quien presta el servicio). Cancelación: si el cliente cancela con más de 72 horas se le devuelve la señal (antes eran 48 h y un 2,75 % solo para el cliente).
- Precios (24 nov 2026, Rodrigo): precio fundador, plan Pro todo 2027 por 99 € + IVA, solo 100 plazas: se mantiene si la solicitud llega antes del 15 de febrero de 2027 y Favent la acepta (aunque la acepte después); desde el 15 de febrero, Starter 29 €/mes y Pro 44,95 €/mes (+ IVA); Enterprise siempre a medida. Igual para quien ofrece servicios y quien recomienda.
- Servicios publicados: cada empresa puede registrar todos los servicios que quiera, pero publicar como máximo 2 a la vez; cada servicio publicado se presenta por separado (su propia etiqueta y ficha en el mapa).
- Cada servicio se nombra con el nombre del barco (o del recurso) y el servicio, p. ej. «Zafiro — Barco privado · 12 pax · bebida incluida». La disponibilidad no se fija en el servicio: se lleva en la Agenda, que es una agenda completa con todos los servicios dados de alta (publicados o no). Quien presta el servicio apunta ahí sus propias reservas (teléfono, web, en persona…) como en cualquier agenda; las reservas hechas con Favent se apuntan solas en su salida, con el cliente, las personas y quien la recomendó.
- La Agenda es uno de los productos centrales: debe verse como un calendario profesional (vistas Día, Semana y Mes; productos en columnas y días/horas hacia abajo; un color por producto). Las empresas de barcos suelen tener 5–6 productos.
- Colaboradores: dos empresas colaboran solo cuando ambas aceptan la solicitud. Quien ofrece servicios solo puede pasar reservas a sus colaboradores. Quien recomienda puede filtrar el mapa por «Solo colaboradores».
- Fundadores: Rodrigo (negocio) y un socio ingeniero (producto).

## Este repositorio
- Solo contiene la **web pública de presentación y lista de espera**. La app (PWA en Next.js + Supabase + Stripe Connect) irá en otro repositorio y en un subdominio (p. ej. app.favent.app). No construir la app aquí.
- Alojamiento: **GitHub Pages**, rama `main`, carpeta raíz. Cada push a `main` se publica en https://www.favent.app.
- **Publicar lo hace Claude (decisión de Rodrigo, 21 nov 2026):** en este repositorio, al terminar un cambio se junta en `main` sin pedírselo a Rodrigo (rama de trabajo → PR → juntarla), y se le dice qué se ha publicado. En la app (`favent-app`) no: ahí las PR las junta él.
- **No borrar ni modificar el archivo `CNAME`** (contiene `www.favent.app`).
- Páginas por público (24 nov 2026, para Google): `si-recomiendas.html` (quien recomienda: hoteles, alquiler vacacional, restaurantes, agencias y conserjerías; no solo «hoteles y agencias», decisión de Rodrigo) y `empresas-de-servicios.html` (quien ofrece servicios), en la raíz, con su versión en inglés (`refer-clients.html`, `service-businesses.html`) enlazada con `hreflang` (es, en y x-default = español) en la cabecera y en `sitemap.xml`, y un botón «EN / ES» en el menú. Cada una con su título, descripción, canónica y datos estructurados; enlazadas desde la portada y el pie (los enlaces con `data-href-en` cambian a la página en inglés al poner la web en EN), y en `sitemap.xml` (actualizar `lastmod` cuando cambien). Sus botones de «Solicitar acceso» llevan a `/?solicitar=1&perfil=…` (en inglés, con `&lang=en`), que abre el panel de la portada. Vídeos del recorrido de la app (de Rodrigo, 24 nov 2026): `img/app/tour-rec-es.mp4` en `si-recomiendas.html` (el lema del final se cambió a «Connecting businesses.») y `img/app/tour-ofr-es.mp4` en `empresas-de-servicios.html`; faltan las versiones en inglés. `hoteles-y-agencias.html` queda solo como redirección a `si-recomiendas.html` (no borrarla: puede haber enlaces).
- Botones de los planes (26 nov): «Empezar con Starter», «Empezar con Pro» y «Hablar con Favent»; abren el formulario con ese plan y ese tipo de empresa.
- Secciones antiguas (26 nov): se quitaron del código las que ya no se veían (socios, la idea, «Así se mueve una reserva», hoteles, confianza y equipos); su parte del script se queda protegida con comprobaciones. `#app` y `#mapa` siguen ocultas en el código porque el panel interactivo las usa: no borrarlas sin quitar antes esa dependencia.
- Web estática: un único `index.html` con CSS y JS en línea, sin build ni dependencias. Mantenerlo así salvo que se pida lo contrario. Si se añaden páginas (privacidad, aviso legal, cookies), crear archivos `.html` en la raíz con el mismo estilo.
- El mapa es un SVG propio: costa de Mallorca y Dragonera de OpenStreetMap (paquete `@geo-maps/earth-lands-100m`, ODbL; atribución «© OpenStreetMap» obligatoria en el mapa), con Serra de Tramuntana, carreteras principales esquemáticas, pueblos y bahías. Los pins se colocan por latitud/longitud con `proj()`. Sin librerías ni mosaicos externos.
- GitHub Pages no permite backend ni pagos: los formularios deben enviar a un servicio externo (Formspree, Supabase, etc.).

## Marca
**Todo el diseño de la web debe seguir [`DESIGN.md`](DESIGN.md)**: colores, tipografía, espaciado, elevación (lienzo, tarjetas y pantallas dibujadas), componentes, movimiento y comportamiento responsive. Antes de cambiar algo visual, léelo; si un cambio introduce o modifica un token o un componente, actualiza `DESIGN.md` en el mismo cambio. Si el código y `DESIGN.md` no coinciden, avisa y corrige uno de los dos.

Resumen (el detalle está en `DESIGN.md`):
- Nombre: siempre **favent** en minúscula en el logotipo, "Favent" en el texto. Etiqueta secundaria: **B2B SERVICE**.
- Logotipo: la palabra «favent.» en Michroma con punto rosa (`.logo` + `.logo-cur`). El monograma «fv» en negativo con el punto interior rosa (`img/logo-mark-neg.png`, del original `img/logo-mark.png`) es el icono: favicon (`img/favicon-32.png`, `favicon.ico`), iconos de app (`img/icon-192.png`, `img/icon-512.png`, `img/apple-touch-icon.png`) e imagen social (`img/og-image.png`). No va pegado a la palabra. Si cambian, regenerarlos y subir el `?v=N` de sus enlaces.
- Identidad D, «Favent depurado» (16 nov 2026): carbón `#0B0F17` solo en el inicio, la llamada final y el pie; el resto claro como la app (`#F6F6F3`, tarjetas blancas, texto `#1E2226`). El rosa señal `#FF4F9A` en toques (el punto del logotipo repetido al final de cada titular, etiquetas, línea de los pasos, marcas; en texto pequeño `#C2185B`), nunca en párrafos ni fondos. Sin «gratis durante el piloto» en la web (decisión de Rodrigo, 16 nov). Sin rejilla de puntos, grano, vidrio, relieves ni azul eléctrico. Las pantallas de la app se dibujan en HTML (`.mini`, `.phone`) y llevan «Vista de ejemplo».
- Tipografías: Funnel Display (titulares y texto), Geist Mono (etiquetas, códigos, importes, estados), Michroma (solo la palabra del logotipo).
- Identidad E, «Favent nocturno» (19 nov 2026, rama `oscuro-brillo`): toda la web en carbón, resplandor rosa y azul detrás del panel y de los bloques, menú flotante en píldora, cabeceras centradas y tarjetas en rejilla. Manda sobre la D en la web; detalle en `DESIGN.md`.
- Limpieza (25 nov 2026, Rodrigo: «más sencilla, sin cambiar el estilo»): el resplandor solo en el inicio y en la llamada final; tarjetas y planes lisos; menú sin «B2B SERVICE» y con el idioma solo en banderitas, sin «ES / EN» (Rodrigo); aviso de privacidad en una línea. Lo nuevo debe seguir esa línea: pocos elementos y nada flotando.
- Sin naranja, sin degradados de color visibles (salvo el resplandor de la identidad E), sin emojis, sin transición de día y noche.
- Botón principal: «Crear cuenta» → `https://app.favent.app/registro` (Favent revisa cada alta); «Entrar» → `https://app.favent.app/login`. El email de la llamada final sigue llegando a info@favent.es (Web3Forms).

## Textos y tono
- Idioma principal: **español**. Directo, profesional, cercano.
- Expresión clave: "canal de ventas profesional".
- **No usar** "comisionistas", "prescriptores" ni "proveedores" en la web. Usar: "quien recomienda", "quien ofrece / presta el servicio", "las dos empresas", "Si recomiendas", "Si ofreces servicios".
- Contacto por WhatsApp (24 nov 2026): al +34 633 952 154 («Consultar por WhatsApp»), con un mensaje ya escrito en el idioma de la web. Desde el 25 nov es un icono dentro del menú de arriba, no un botón flotante (Rodrigo: que nada flote sobre la página).
- No mencionar WhatsApp ni el efectivo como problema en el copy; hablar de "la forma profesional de gestionar tus comisiones".
- Ubicación en el copy: **Mallorca** (no Pollença/Alcúdia).
- Lema corto (desde el 23 nov 2026): "Connecting businesses." (en inglés también en la web en español; antes «Cada cliente que envías, cobrado.»).
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
1. Formulario de acceso a **info@favent.es** (se abre en un panel desde el botón de arriba; se envía primero a la app, `https://app.favent.app/api/solicitud`, que lo guarda, cuenta la plaza de fundador y lo manda por email; si la app no responde, por Web3Forms. Las plazas que quedan las da `https://app.favent.app/api/fundadores`: 100, contando desde 23. Desde el 26 nov, corto (Rodrigo): tipo, nombre comercial, contacto, teléfono, email y plan, más la fecha de envío para el precio fundador y la casilla de consentimiento; sector y municipio se envían como «Sin indicar» porque la app aún los exige, y el resto se pide al revisar el alta. Al enviar con precio fundador, el contador de plazas baja una al momento): con la clave de Web3Forms en `WEB3FORMS_KEY` se envía por Web3Forms (cuenta creada con info@favent.es); sin clave, por FormSubmit (`https://formsubmit.co/ajax/info@favent.es`, exige activar por correo). Si falla, el aviso abre un email ya escrito a info@favent.es. Email de contacto en el pie: info@favent.es. Al publicar la política de privacidad, mencionar FormSubmit como encargado del tratamiento.
1b. Dominio favent.es: redirigir (301) a https://www.favent.app desde el proveedor del dominio; GitHub Pages solo admite un dominio por repositorio y el `CNAME` se queda en www.favent.app.
2. Páginas legales: aviso legal, política de privacidad y cookies (RGPD/LSSI). Enlazarlas desde el pie.
3. Sustituir marcadores de logos y fotos cuando haya material real.
4. Versión en inglés de la web.
5. Metadatos para compartir (Open Graph, imagen social).

## Contexto legal y de negocio (no reflejar en la web sin validar)
- Marca: existe una marca española registrada "Faventy" (clase 42). Pendiente opinión de un agente de marcas antes de registrar "Favent".
- Pagos previstos: Stripe Connect (cargos y transferencias separados). Para México y Argentina habrá que revisar moneda, facturación y pasarela de cada país (confirmar si Stripe opera en Argentina). Polonia y BLIK, aplazados.
- Estructura prevista (25 nov 2026, Rodrigo): una SL española. Ya no una sp. z o.o. en Polonia.
