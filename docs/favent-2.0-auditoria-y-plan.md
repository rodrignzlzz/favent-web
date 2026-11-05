# Favent 2.0: adaptado a lo que ya tenemos

> Documento interno, no se publica (`docs/` está excluido en `_config.yml`).
> Base: el documento maestro «Favent 2.0: Product evolution, Connect Spot & Favent Catalog» (llegó cortado en la lista de categorías de Catalog). Aquí se traduce a los conceptos, nombres y reglas que Favent ya tiene.

## 0. Idea principal

**Favent no cambia: crece.** El núcleo sigue siendo el canal de ventas profesional entre empresas que ya está definido y mostrado en la web: acuerdo de comisión, reserva con señal, canje por QR y liberación automática.

Favent Catalog y Connect Spot son **una capa aparte que se introducirá más adelante**. No sustituyen nada: usan el mismo motor (servicios, Agenda, señal, QR, comisiones) para llevar más clientes a las mismas empresas. Su papel es dar sentido a la red y ayudar a la expansión del servicio.

Hasta que se lancen, **la web pública sigue igual** y no los menciona.

---

## 1. Equivalencias: documento maestro ↔ Favent hoy

| Documento maestro | En Favent ya existe como | Notas |
|---|---|---|
| Favent Platform (B2B) | **Favent**: el producto actual (lo que muestran los paneles de ejemplo) | No hace falta un nombre nuevo de cara afuera; «Platform» puede quedar como nombre interno |
| Proveedor | **Quien ofrece / presta el servicio** | En la web no se usa «proveedor» |
| Intermediario | **Quien recomienda** | Hoteles, conserjerías, agencias, profesionales |
| Relaciones comerciales | **Colaboradores** (las dos empresas aceptan) + **acuerdo de comisión** en Mensajes | |
| Derivación de clientes | **Recomendar** (flujo 1) y **pasar reserva entre colegas** (flujo 2) | |
| Gestión de disponibilidad | **Agenda** (Día/Semana/Mes, un color por producto, reservas propias y de Favent) | La disponibilidad no se fija en el servicio |
| Productos y servicios | **Servicios**: nombre del barco/recurso + servicio; máximo 2 publicados a la vez | |
| Configuración de comisiones | Comisión por servicio (1–50 %) en la tarjeta del servicio | |
| Señal / pago | **Señal** elegida por quien presta el servicio: «Solo la comisión» o «50 % del total» | Stripe Connect previsto |
| Validación por QR | **Escanear QR** y canje | |
| Estadísticas | **Informes** | |
| Usuarios y permisos | Usuario / Administrador (pantalla de entrada) y **Equipos** | |
| Consumidor | **El cliente** (hoy solo aparece como nombre en la reserva) | Con Catalog pasa a ser usuario directo |
| Establecimiento de origen | Nuevo: **Connect Spot** (ver 3) | |
| Favent | Favent | Su papel económico en cada operación **está por definir**; no se publica nada hasta decidirlo |

Conclusión: casi todo lo que pide la parte B2B del documento **ya está pensado y dibujado**. Lo nuevo es el cliente final como usuario (Catalog) y el establecimiento físico como origen (Connect Spot).

---

## 2. Favent Catalog: un canal de venta más para quien ofrece servicios

**Qué es:** el escaparate público, para el cliente final, de los servicios **publicados** en Favent. Dirección prevista: `catalog.favent.app`. Lema: «Discover more. Experience better.». Catalog se dirige a turistas y puede ir en inglés; en la web de Favent (en español) se presentaría como «Descubre más. Vívelo mejor.» o con el lema en inglés como nombre de submarca.

**Cómo encaja con lo que ya hay:**
- **Mismos servicios:** lo que una empresa publica (máximo 2 a la vez) aparece en el mapa B2B y en Catalog. No hay un alta aparte.
- **Misma Agenda:** una reserva de Catalog entra sola en la Agenda, como las de Favent, con origen **«Catalog»** (junto a Favent, Teléfono, Web propia, En persona y Otra agencia). En Informes, «Por canal» gana una fila.
- **Misma señal y mismo QR:** el cliente paga la señal elegida por quien presta el servicio, recibe su código QR y lo canjea al llegar. El resto se cobra en la oficina, igual que ahora.
- **Mismo recorrido de 4 pasos:** Acuerdo (ya pactado entre las empresas o con Favent) → Reserva y señal → Canje → Liberación.
- **Lo que el cliente no ve:** comisiones, acuerdos, colaboradores, liquidaciones ni reparto. Solo descubre, compara y reserva.

**Categorías:** las de Catalog cuelgan de las cuatro que ya existen, así no hay que rehacer el mapa:

| Favent (mapa) | Catalog |
|---|---|
| Náutica | Boat experiences · Water sports · Diving and snorkeling |
| Ciclismo | Outdoor activities · Adventure |
| Traslados | Excursions (si incluye transporte) |
| Servicios privados | Gastronomy · Private experiences |
| (nueva, más adelante) | Other local experiences |

**Home de Catalog** (según el documento): hero con foto, buscador, ubicación, fecha, categorías, destacados, populares, empresas recomendadas, descubrir y ayuda. Mobile-first y con el mismo sistema visual (`DESIGN.md`), en versión «pantalla clara».

**Por definir:** quién cobra comisión en una reserva hecha directamente en Catalog, sin quien recomienda (¿nadie, Favent, un spot?).

---

## 3. Connect Spot: quien recomienda, con un punto físico

**Qué es:** un establecimiento (hotel, conserjería, bar de playa, tienda, alquiler…) que se une a la red como **quien recomienda**, pero con presencia física: un código QR o un enlace propio que lleva al cliente a Catalog.

**Cómo encaja con lo que ya hay:**
- Es el mismo perfil «Si recomiendas clientes». No es un tercer papel; es una forma nueva de recomendar.
- Hoy quien recomienda reserva por el cliente desde el panel. Con Connect Spot, **el cliente también puede reservar solo** escaneando el QR del establecimiento, y la reserva queda **atribuida al spot**.
- La comisión sigue las mismas reglas: la pactan las dos empresas y se libera al canjear el QR de la reserva.
- Solo puede recomendar servicios de empresas con acuerdo (o colaboradoras, según se decida). Es la misma lógica que «Solo colaboradores».
- En la reserva y en la Agenda de quien presta el servicio aparece «Recomendada por: [spot]», como ya pasa con las reservas de Favent.

**Por qué ayuda a la expansión:** cada spot es un punto de captación que no necesita a nadie de la empresa delante. Abrir una zona nueva (p. ej. Varsovia) es sumar empresas que ofrecen servicios y spots que los muestran.

**Pendiente:** el resto del documento maestro sobre Connect Spot (llegó cortado). Si contradice algo de esta sección, se ajusta.

---

## 4. Cada operación, de punta a punta

| Papel | Quién | Ve |
|---|---|---|
| Cliente | Reserva en Catalog, en un spot o a través de quien recomienda | Servicio, precio, señal, su QR |
| Quien presta el servicio | La empresa del servicio | Su reserva, señal, lo que cobra en la oficina, comisión que paga |
| Quien recomienda / Connect Spot | Si la reserva viene de él | Su comisión y el estado de la reserva |
| Favent | Siempre | Lo necesario para operar y liquidar |

Nadie ve las condiciones privadas de otros participantes.

---

## 5. Auditoría breve de este repositorio

- `index.html` (una página, ~4000 líneas, sin build) presenta el producto B2B con paneles de ejemplo completos: Agenda, Servicios, QR, Colaboradores, Informes, mapa y recorrido. **Todo esto se mantiene.**
- Formulario de acceso operativo (Web3Forms → FormSubmit → email a info@favent.es), con el campo `perfil`.
- **Incoherencia que hay que corregir:** `DESIGN.md` → *Known Gaps* dice que no hay email de contacto y que el formulario no está conectado; las dos cosas ya existen. El *Footer* cita `{colors.ink-2}`, que no es un token de la lista.
- GitHub Pages admite un dominio por repositorio: `catalog.favent.app` irá en su propio repositorio o en la app, no aquí.

---

## 6. Hoja de ruta

| Etapa | Qué | Dónde |
|---|---|---|
| **Ahora** | Web pública B2B como está. Este documento como referencia. Corregir `DESIGN.md` (Known Gaps). | Este repositorio |
| **Producto** | App B2B (PWA): lo que hoy son paneles de ejemplo. Añadir el origen «Catalog» y el «spot» al modelo de datos desde el principio, aunque no se usen todavía. | Repositorio de la app |
| **Expansión 1: Catalog** | `catalog.favent.app` con los servicios publicados, reserva con señal y QR. | Repositorio propio / app |
| **Expansión 2: Connect Spot** | Alta de establecimientos, QR/enlace propio, reservas atribuidas. | App + Catalog |
| **Al lanzar** | Presentar Catalog y Connect Spot en www.favent.app: una sección después de «Para quién es» y un perfil «Tengo un establecimiento» en la lista de espera. Actualizar `CLAUDE.md` y `DESIGN.md`. | Este repositorio |

## 7. Decisiones abiertas
1. Comisión en reservas directas de Catalog (sin quien recomienda).
2. Si un spot puede recomendar cualquier servicio con acuerdo o solo los de colaboradores.
3. Papel económico de Favent en cada operación (no publicar nada hasta decidirlo).
4. Validación legal de la venta al consumidor final: desistimiento, información previa, RGPD y papel de marketplace.
