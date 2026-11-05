# Favent 2.0: auditoría del proyecto y plan de implementación

> Documento interno, no se publica (`docs/` está excluido en `_config.yml`).
> Base: el documento maestro «Favent 2.0: Product evolution, Connect Spot & Favent Catalog». **Llegó cortado** en la lista de categorías de Favent Catalog («Other loca…»). Falta todo lo que va detrás: el resto de Catalog, Connect Spot completo y las peticiones finales. Este plan se ajustará cuando llegue.
> Prioridad acordada: **opción B primero**. La web pública presenta el ecosistema, en cambios pequeños y sin reconstruir lo que ya funciona.

---

## 1. Auditoría: qué hay hoy

### 1.1 Repositorio
| Elemento | Estado |
|---|---|
| `index.html` | 4043 líneas, CSS y JS en línea, sin build. Única página. |
| `DESIGN.md` | Fuente de verdad visual, muy detallada (501 líneas). |
| `CLAUDE.md` | Reglas de producto, tono, honestidad y accesibilidad. |
| `CNAME` | `www.favent.app`. **No tocar.** |
| `_config.yml` | Excluye `CLAUDE.md`, `DESIGN.md` y carpetas internas de la publicación. |
| `img/` | Logos, iconos, imagen social y fotos de ejemplo (náutica, traslados, ciclismo, privados, flota, perfiles). |
| `robots.txt`, `sitemap.xml` | Una sola URL (`/`). |
| Alojamiento | GitHub Pages, rama `main`. Cada push a `main` se publica. |

### 1.2 Estructura de `index.html` (orden actual)
| # | Sección | Fondo | Qué hace |
|---|---|---|---|
| 1 | `nav.topnav` | oscuro | Logo, «Solicitar acceso», selector ES/EN |
| 2 | `header.intro` | oscuro | Titular «Cada cliente que envías, cobrado.», rejilla animada, formulario `#acceso` |
| 3 | `#producto` | oscuro | Panel animado: login → categorías → mapa → chat → reserva |
| 4 | `#idea` | claro | Frase que se revela con el scroll |
| 5 | `#como` | claro | Recorrido en 4 pasos (Acuerdo, Reserva y señal, Canje, Liberación) |
| 6 | `#hoteles` | oscuro | «Para quién es»: 3 tarjetas (Si recomiendas / Si ofreces servicios / Entre colegas) |
| 7 | `#app` | claro | Panel interactivo doble: «Si recomiendas» y «Si ofreces servicios», con Agenda, Servicios, QR, Colaboradores, Informes… |
| 8 | `#mapa` | — | **Oculta**, pero su código la reutiliza el panel interactivo (`fxMap()`). No borrar. |
| 9 | `#confianza` | oscuro | Ficha de fiabilidad y revisión de empresas en el piloto |
| 10 | `#equipos` | claro | Gestión de equipos |
| 11 | `#acceso-final-sec` | oscuro | «Únete al piloto en Mallorca» + formulario |
| 12 | `footer` | oscuro | Palabra gigante, contacto; enlaces legales ocultos |
| — | Sección de logos de socios | — | Oculta (marcador) |

Script: diccionario `EN` (línea ~1454) para todo el texto; formulario con Web3Forms (clave en `WEB3FORMS_KEY`) y FormSubmit como alternativa; el campo `perfil` sale de `a[data-perfil]` (`recomienda` / `ofrece`).

### 1.3 Lo que funciona y **no hay que reconstruir**
- Rejilla del inicio, entrada del titular, botón de pausa y `prefers-reduced-motion`.
- Panel animado `#producto` (`#hx-pre`, recorrido automático).
- Panel interactivo `#app`: Agenda completa (Día/Semana/Mes, arrastrar, pantalla completa, Google Calendar de ejemplo), Servicios con comisión y señal, Escanear QR, Colaboradores, Informes, Mensajes.
- Mapa SVG propio con `proj()` y atribución © OpenStreetMap.
- Recorrido `#como` (`routeLayout`).
- Formulario de acceso (Web3Forms → FormSubmit → `mailto:`).
- Traducción ES/EN.

Todo lo nuevo se **añade** al lado; no se reescribe nada de esto.

### 1.4 Incoherencias encontradas (código ↔ documentación)
1. `DESIGN.md` → *Known Gaps* dice que no hay email de contacto y que `FORM_ENDPOINT` está vacío. **Ya no es cierto**: el pie tiene info@favent.es y el formulario envía por Web3Forms. Hay que corregir `DESIGN.md`.
2. `DESIGN.md` → *Footer* usa `{colors.ink-2}`, un token que no existe en su lista de colores (en CSS es la variable `--ink-2` = ink-muted). Es un detalle menor.
3. La alternancia oscuro/claro ya tiene dos pares seguidos (`#idea` y `#como`, ambos claros; `#producto` tras el inicio, ambos oscuros). Cualquier sección nueva creará otro par. Ver 3.2.

### 1.5 Choques entre el documento maestro y las reglas actuales
| Documento maestro | Regla actual | Hay que decidir |
|---|---|---|
| Habla de «proveedores», «intermediarios», «consumidores» | `CLAUDE.md`: no usar «proveedores», «comisionistas», «prescriptores» en la web | Uso interno sí; en la web, ¿se mantiene «quien recomienda / quien ofrece el servicio»? (recomendado: sí) |
| Lema de Catalog «Discover more. Experience better.» (inglés) | Idioma principal de la web: español | ¿Se deja en inglés como lema de submarca o se traduce? (p. ej. «Descubre más. Vívelo mejor.») |
| Catalog B2C, para el consumidor final | Toda la web habla a empresas («B2B SERVICE») | En www.favent.app, Catalog se presenta **a las empresas** («tus servicios también llegan al cliente final»), no al turista |
| Categorías en inglés (Boat experiences, Water sports…) | Categorías actuales del mapa: Náutica, Traslados, Ciclismo, Servicios privados | ¿Se amplían las categorías del panel de ejemplo o solo cambian en Catalog? |
| Connect Spot: establecimientos físicos que captan clientes | Ya existe el perfil «Si recomiendas clientes: hoteles, conserjerías, agencias» | **Clave:** ¿Connect Spot es una evolución de quien recomienda (el hotel pasa a ser «spot»), o un tercer papel distinto? Falta esa parte del documento |
| Ecosistema con 3 componentes | `CLAUDE.md` describe solo la web B2B | Actualizar `CLAUDE.md` y `DESIGN.md` en el mismo cambio que la web |

### 1.6 Límites técnicos
- **GitHub Pages admite un solo dominio por repositorio.** `catalog.favent.app` necesitará otro repositorio (o la app futura). Desde este se puede, como mucho, enlazarlo o presentarlo en `www.favent.app/catalog.html`.
- Sin backend: Catalog con reservas y pagos reales y Favent Platform van en el repositorio de la app (Next.js + Supabase + Stripe Connect), como ya prevé `CLAUDE.md`.
- Honestidad: Catalog y Connect Spot aún no existen. En la web deben aparecer como **«Próximamente»** o «En preparación», sin cifras, socios ni establecimientos inventados.

---

## 2. Alcance de la opción B (en este repositorio)

**Sí:** contar en la web pública que Favent es un ecosistema con tres caras (Platform, Catalog y Connect Spot), dejar que cada tipo de participante se apunte a la lista de espera con su perfil y preparar el terreno para `catalog.favent.app`.

**No (va en otro repositorio):** la plataforma B2B real, el catálogo con buscador, fechas y reservas reales, pagos B2C, cuentas de consumidor y la gestión de establecimientos.

---

## 3. Plan por fases

Cada fase es **un commit (o PR) pequeño**, revisable y publicable por separado. No se pasa a la siguiente sin validar la anterior.

### Fase 0: Decisiones pendientes (sin código)
1. Recibir el resto del documento maestro (Catalog completo, Connect Spot y lo que siga).
2. Decidir los puntos de la tabla 1.5, sobre todo **qué es Connect Spot respecto a «Si recomiendas clientes»** y el idioma del lema.
3. Confirmar si `catalog.favent.app` tendrá su propio repositorio desde ya.

### Fase 1: Documentación (sin cambios visibles)
- `CLAUDE.md`: añadir «Ecosistema Favent 2.0» con los tres componentes, qué va en este repositorio y qué no, y el vocabulario permitido.
- `DESIGN.md`: corregir *Known Gaps* (formulario y email ya existen) y el token `ink-2`; reservar el componente nuevo (`eco-card`, ver fase 2) antes de construirlo.
- Riesgo: ninguno; no se publica nada visible.

### Fase 2: Sección «Un ecosistema» en `index.html`
- **Una sola sección nueva**, `#ecosistema`, justo después de `#hoteles` («Para quién es»), en oscuro. Continúa la explicación de los perfiles y no toca los paneles de ejemplo.
- Contenido: etiqueta + H2 (p. ej. «Una red, tres formas de entrar.») y tres `glass-card`:
  - **Favent Platform**: el canal de ventas entre empresas (lo que ya muestra la web). Estado: «Piloto en Mallorca».
  - **Favent Catalog**: tus servicios, también ante el cliente final. Estado: «Próximamente».
  - **Connect Spot**: establecimientos que acercan clientes a los servicios de la red. Estado: «Próximamente».
- Estados en `status-pill` (Geist Mono); sin fotos nuevas mientras no haya material real; sin cifras.
- Textos nuevos con su entrada en `EN`.
- Comprobar en 1280 px y 390 px, ES/EN y con movimiento reducido; sin scroll horizontal; contraste ≥ 4,5:1.
- Riesgo: bajo. Es HTML y CSS añadidos; no se toca el JS de `#app` ni de `#producto`.

### Fase 3: Perfil Connect Spot en la lista de espera
- Según la decisión de la fase 0: o un cuarto botón o tarjeta «Tengo un establecimiento» con `data-perfil="spot"`, o ampliar el texto de «Si recomiendas clientes».
- El formulario ya envía `perfil`; solo hay que añadir el valor. No se cambia el flujo de envío.
- Riesgo: bajo. Probar un envío real a info@favent.es.

### Fase 4: Página de presentación de Catalog
- `catalog.html` en la raíz, con el mismo estilo, que explica a las empresas qué será Catalog y deja el email (o lo hace `catalog.favent.app` desde su propio repositorio, según la fase 0).
- Como mucho, una pantalla encendida de ejemplo del catálogo (hero, buscador y categorías) marcada «Vista de ejemplo». No es el producto real.
- Añadir la URL a `sitemap.xml`.
- Riesgo: medio-bajo. Página nueva; la principal solo gana un enlace.

### Fase 5: Metadatos y cierre
- Revisar `og:description` y `<title>` si el mensaje principal cambia a «ecosistema» (de momento **no**: el lema y el foco B2B se mantienen).
- Actualizar `DESIGN.md` con lo construido.

### Fuera de este repositorio (para más adelante)
- **Favent Catalog** (`catalog.favent.app`): mobile-first, hero con foto, buscador, ubicación, fecha, categorías, destacados, populares, recomendados y ayuda. Sin datos de comisiones ni acuerdos para el consumidor. Comparte backend con Platform.
- **Favent Platform**: evolución de lo que hoy son los paneles de ejemplo, en la PWA.
- **Modelo de datos común**: cada operación identifica consumidor, quien presta el servicio, quien recomienda, establecimiento de origen y Favent; permisos para que nadie vea condiciones privadas de otros.
- Validar en legal: venta a consumidores (derecho de desistimiento, información precontractual), RGPD de consumidores y el papel de Favent como marketplace.

---

## 4. Siguiente paso propuesto
1. Me envías el resto del documento y respondes a la fase 0.
2. Hago la **fase 1** (solo documentación) y después la **fase 2** en un PR aparte para revisarla antes de publicar en `main`.
