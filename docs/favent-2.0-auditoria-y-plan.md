# Favent 2.0: auditoría y plan de implementación

> Documento interno, no se publica (`docs/` está excluido en `_config.yml`).
> Base: el documento maestro completo «Favent 2.0: Product evolution, Connect Spot & Favent Catalog», adaptado a lo que Favent ya tiene y a las decisiones tomadas con Rodrigo. **Si el documento maestro y una decisión chocan, manda la decisión** (ver 2).

---

## 0. Idea principal

**Favent no cambia: crece.** El núcleo sigue siendo el canal de ventas profesional entre empresas: acuerdo de comisión, reserva con señal, canje por QR y liberación automática.

Favent Catalog y Connect Spot son **una capa aparte, sobre el mismo motor** (servicios publicados, Agenda, señal, QR y comisiones), que lleva más clientes a las mismas empresas y ayuda a la expansión. Una sola infraestructura y una sola base de datos, con tres interfaces.

### Reglas decididas
1. **El huésped solo ve precios totales. Nada de comisiones. Pero la comisión de lo que reserva va para el hotel.**
2. **A Catalog solo se entra desde un Connect Spot.** No hay acceso público ni registro libre.
3. **Los Connect Spots los da de alta Favent** en su software. Ningún establecimiento se apunta solo.
4. **QR por hotel o por habitación** (o casa, punto…), a elección. Se generan solos.
5. **La atribución se mantiene:** si el huésped vuelve más tarde desde fuera, la comisión sigue siendo de ese hotel. **Si hay dos spots, cuenta el último.**
6. **Sin perfiles de cliente.** Igual que Favent: le llega un enlace, reserva pagando una parte (la señal) y el resto en persona.
7. **Qué ve el huésped lo elige el Administrador del hotel:** «Solo colaboradores» (comisión pactada entre las dos empresas; en la práctica suele marcarla el hotel) o «Todo libre» (la comisión que fijó quien presta el servicio en su ficha).
8. **Favent es el marketplace y garantiza el cobro** a las dos partes, sobre todo a quien recomienda.
9. **Ingresos de Favent:** un precio por cada QR necesario más una tarifa mensual. Los pagan sobre todo los hoteles; quien presta el servicio también puede pedir QR para referenciar a sus clientes. Más adelante, unos pequeños **gastos de gestión** al cliente (cubren la pasarela de pago y la protección del pago), siempre dentro del precio total desde la primera pantalla.
10. La web pública (www.favent.app) **no menciona** Catalog ni Connect Spot hasta el lanzamiento.

---

## 1. Auditoría del proyecto actual (sección 12, puntos 1–7 del documento maestro)

### 1.1 Qué hay
| Pregunta | Respuesta |
|---|---|
| Frontend | Solo este repositorio: la **web pública** de presentación y lista de espera (`index.html`, ~4000 líneas, HTML/CSS/JS en línea, sin build), en GitHub Pages con dominio `www.favent.app`. |
| Backend | **No existe.** GitHub Pages no admite servidor. |
| Base de datos | **No existe.** |
| Autenticación | **No existe.** La «pantalla de entrada» del panel es una animación de ejemplo. |
| Integraciones | Formulario de acceso con Web3Forms (alternativas: FormSubmit y un `mailto:` a info@favent.es). Nada más. |
| Pagos | **No existen.** Stripe Connect está previsto, no integrado. |
| Estructura | `index.html`, `img/`, `CLAUDE.md`, `DESIGN.md`, `CNAME`, `_config.yml`, `robots.txt`, `sitemap.xml`, `docs/`. |

**Conclusión:** la «Favent Platform» que el documento pide conservar existe hoy como **especificación funcional muy detallada**, dibujada en los paneles de ejemplo de la web y descrita en `CLAUDE.md` y `DESIGN.md`. **No hay código de producto que romper ni base de datos que duplicar.** La beta se construye desde cero en el **repositorio de la app**, como ya prevé `CLAUDE.md` (PWA en Next.js + Supabase + Stripe Connect, en `app.favent.app`).

### 1.2 Qué se reutiliza (como especificación)
Los paneles de ejemplo ya fijan reglas de negocio que la beta debe respetar tal cual:
- **Servicios:** nombre del barco/recurso + servicio; máximo 2 publicados a la vez; comisión 1–50 % por servicio; señal «Solo la comisión» o «50 % del total».
- **Agenda:** calendario profesional (Día/Semana/Mes), un color por producto; reservas propias (Teléfono, Web propia, En persona, Otra agencia) y de Favent; sin solapes en el mismo producto.
- **Reserva y canje:** código (formato tipo `FV-7K2Q`), QR, estados (señal pagada / pago pendiente / ya canjeada), «A cobrar en la oficina», confirmación de canje que libera la comisión.
- **Colaboradores:** las dos empresas aceptan; «Pasar reserva» solo a colaboradores; filtro «Solo colaboradores».
- **Mensajes:** propuesta de acuerdo, aceptar o proponer cambios.
- **Informes:** ventas por canal, vía Favent frente a propias, comisiones pagadas.
- **Roles:** Usuario / Administrador; gestión de equipos.
- **Diseño:** `DESIGN.md` (tipografías, colores, las «pantallas encendidas» claras, que son la base natural de la app y de Catalog).

### 1.3 Riesgos de arquitectura
1. **Pagos retenidos:** el modelo «la comisión se libera al canjear el QR» exige retener fondos. Hay que hacerlo **con las capacidades reales** de la pasarela (ver 7), no con un falso escrow.
2. **Atribución manipulable:** si el spot solo viaja en la URL, se puede cambiar a mano. Debe registrarse y validarse en el backend (ver 6).
3. **Dos fuentes de verdad de la disponibilidad:** Catalog, la Agenda y las reservas propias tienen que leer y escribir **la misma** tabla de disponibilidad y reservas, con bloqueo frente a reservas dobles.
4. **Fugas de información:** el cliente no debe ver comisiones ni siquiera en la respuesta de la API, no solo en pantalla. Hacen falta permisos por fila en la base de datos (Supabase RLS) y vistas separadas para Catalog.
5. **Instantánea económica:** cambiar una comisión o un precio no debe alterar reservas ya hechas.

---

## 2. Documento maestro frente a decisiones: qué manda

| Documento maestro | Decisión | Qué se hace |
|---|---|---|
| «Catálogo público», navegable por cualquiera | Solo se entra desde un Connect Spot | Sin código de spot válido, `catalog.favent.app` muestra solo una pantalla de entrada. `noindex`. Dentro, se navega sin registro, como pide el documento |
| «Cada establecimiento debe poder registrarse como Connect Spot» | Los da de alta Favent | Alta solo desde el panel de Favent (Super Admin). El spot luego edita su perfil y su landing |
| Registro de cliente opcional; «Mis reservas» con cuenta o enlace seguro | Sin perfiles de cliente | Solo **enlace seguro** de seguimiento (por email/SMS). Los datos del cliente se guardan en la reserva, no en una cuenta |
| Booking flow con «Pago» del total (ejemplo 600 €) | Se paga una parte (señal) y el resto en persona | El paso de pago cobra la señal elegida por quien presta el servicio (+ gastos de gestión cuando se activen); el resumen muestra «Pagas ahora» y «Pagas en el lugar» |
| Favent cobra «comisión configurada según el acuerdo» | Precio por QR + tarifa mensual (+ gastos de gestión al cliente más adelante) | El motor de pagos admite un reparto para Favent en cada operación, pero en la beta va a 0; los ingresos de Favent se facturan aparte (suscripción) |
| Intermediary y Connect Spot como roles distintos | El spot es quien recomienda, con un punto físico | Connect Spot es un **tipo** de quien recomienda; una empresa puede ser las dos cosas |
| URL `catalog.favent.app/cs/hotel-123` y también `/hotel-a` | QR por hotel o por habitación | Una sola forma: `catalog.favent.app/cs/<slug>`; por habitación, `catalog.favent.app/cs/<slug>/<habitación>` |
| «Tema claro» | `DESIGN.md`: «dark & white», con interfaces claras | La app y Catalog usan la paleta clara de las «pantallas encendidas» (`screen-*`) y la tipografía de Favent; la web pública sigue igual |
| Categorías en inglés | Categorías actuales: Náutica, Traslados, Ciclismo, Servicios privados | Categorías configurables en el backend, en dos niveles (ver 9.2) |
| Vocabulario: proveedor, intermediario, comisionista | La web pública no lo usa | Válido en documentos internos y en el código; en pantallas, «quien recomienda» / «quien presta el servicio» |

---

## 3. Arquitectura propuesta

```
                     ┌──────────────── Supabase (una sola base de datos) ────────────────┐
                     │  Postgres + RLS · Auth · Storage (fotos, QR) · Edge Functions        │
                     └───────────────▲──────────────────▲──────────────────▲──────────────┘
                                     │                  │                  │
   www.favent.app            app.favent.app        catalog.favent.app    Webhooks Stripe
   (este repo, estático)     Platform B2B          Catalog B2C           (pagos, transfers)
   presentación y            + panel Connect Spot  solo con código
   lista de espera           + panel Favent admin  de spot
                             └──────── un solo repositorio Next.js (app) ────────┘
```

- **Un repositorio de app** (Next.js) con dos superficies: `app.` (empresas, spots y Favent) y `catalog.` (clientes), que comparten modelos, motor de reservas y motor de pagos.
- **Una base de datos.** Catalog lee los servicios a través de **vistas públicas** sin columnas de comisión.
- Los pagos solo cambian de estado con los **webhooks de la pasarela**, nunca porque lo diga el navegador.
- Este repositorio (www) **no** se toca para la beta.

---

## 4. Equivalencias: documento maestro ↔ Favent hoy

| Documento maestro | En Favent | Notas |
|---|---|---|
| Favent Platform | Favent (los paneles de ejemplo) | Nombre interno |
| Service provider / Proveedor | Quien ofrece / presta el servicio | |
| Intermediary | Quien recomienda | |
| Connect Spot | Quien recomienda con punto físico | Lo da de alta Favent |
| Activity | Servicio publicado | Máximo 2 a la vez por empresa |
| Availability | Agenda | |
| Relaciones comerciales | Colaboradores + acuerdo en Mensajes | |
| Service validation | Escanear QR / canje | |
| Customer | El cliente de la reserva | Sin cuenta |
| Business Owner / Staff | Administrador / Usuario (+ Equipos) | |

---

## 5. Modelo de datos (beta)

Entidades del documento maestro, agrupadas y ajustadas a Favent. `*` = imprescindible en P0.

| Grupo | Tablas | Claves |
|---|---|---|
| Identidad | `users`*, `businesses`*, `business_members`* (rol Administrador/Usuario) | Una empresa puede tener varios papeles: `business_roles` (presta servicio, recomienda, spot) |
| Red | `collaborations`* (solicitud, aceptada por las dos), `agreements`* (comisión pactada entre dos empresas, con vigencia) | El acuerdo pactado manda sobre la comisión de la ficha |
| Spots | `connect_spots`* (empresa, código `CS-001`, slug, modo «Solo colaboradores»/«Todo libre», landing), `spot_access_points`* (hotel o habitación/casa/punto, QR, URL, campaña) | Se crean solo desde el panel de Favent |
| Catálogo | `services`* (= activities: recurso + servicio, precio, duración, capacidad, incluye/no incluye, cancelación, seguridad, señal, comisión, publicado), `service_images`*, `categories`* (dos niveles, configurables) | Límite de 2 publicados por empresa, en base de datos |
| Agenda | `bookings`* (todas: Favent, Catalog, propias), `booking_participants` | Restricción de no solape por servicio y franja |
| Atribución | `attribution_sessions`*, `attribution_events`* (escaneo, visita, inicio de reserva, pago) | Ver 6 |
| Dinero | `transactions`*, `transaction_allocations`* (quién recibe cuánto), `payouts`*, `refunds`* | Ver 7 |
| Validación | `qr_validations`* (reserva, quién valida, cuándo, resultado) | Un canje por reserva |
| Otros | `customers` (solo datos de contacto por reserva), `reviews` (P1), `notifications` (P1), `audit_logs`* | |

**Instantánea económica:** cada reserva guarda en el momento de crearla el precio, la señal elegida, la comisión aplicada, el origen del acuerdo (ficha o pactado), el spot y los gastos de gestión. Nada de eso se recalcula después.

---

## 6. Sistema de atribución (Partner Attribution)

1. El huésped escanea el QR → `catalog.favent.app/cs/<slug>[/<habitación>]`.
2. El servidor valida el código, crea o actualiza una **sesión de atribución** (`attribution_sessions`) y la guarda en una cookie propia y firmada (el navegador no puede cambiar el spot). Registra el evento `scan`.
3. La navegación y la reserva usan esa sesión, no parámetros de la URL.
4. Al pagar, el **servidor** copia el spot (y el punto de acceso) a la reserva. La reserva queda atribuida para siempre.
5. **Vuelve más tarde desde fuera:** la cookie sigue ahí, o vuelve a abrir el enlace guardado → mismo spot.
6. **Abre el enlace de otro spot:** la sesión pasa al nuevo spot. Regla de la beta: **último punto de contacto válido**. El historial completo queda en `attribution_events` para auditoría y para cambiar la regla en el futuro.
7. **Duplicados:** una reserva por pago (clave de idempotencia); eventos de escaneo repetidos en poco tiempo se agrupan.
8. **Privacidad:** cookie técnica necesaria para la atribución, explicada en la política de privacidad; sin seguimiento publicitario.

---

## 7. Motor de pagos (uno para B2B y B2C)

### 7.1 Cómo encaja la señal de Favent
| Señal elegida | El cliente paga online | Al validar el QR | En el lugar |
|---|---|---|---|
| Solo la comisión | Comisión (+ gastos de gestión) | Comisión → hotel / quien recomendó | Resto del precio |
| 50 % del total | 50 % (+ gastos de gestión) | Comisión → hotel; resto del 50 % → quien presta el servicio | El otro 50 % |

El cliente solo ve «Pagas ahora» y «Pagas en el lugar».

### 7.2 Estados
- Pago: `pendiente` → `autorizado/cobrado` (solo con webhook) → `reembolsado` / `fallido`.
- Liquidación de cada reparto: `retenido` → `en_liquidación` → `liquidado` (solo con confirmación de la pasarela) / `pendiente_manual` / `fallido`.
- Reserva: `confirmada` → `canjeada` / `cancelada` / `no_show`.
- **Nada se marca como pagado o liquidado sin confirmación de la pasarela.** Si una transferencia no se puede ejecutar, queda `pendiente_manual` y aparece en el panel de Favent.

### 7.3 Retener fondos de verdad (investigación pendiente, antes de programar pagos)
- **Stripe Connect** (cargos y transferencias separados): el dinero entra en la cuenta de Favent y se transfiere al canjear. Los fondos no se pueden retener indefinidamente: hay que confirmar con Stripe los plazos máximos para España y cómo afectan las reservas hechas con mucha antelación.
- **Mangopay:** entidad de dinero electrónico pensada para marketplaces, con monederos por usuario. Encaja con «retener hasta el canje»; hay que comparar costes, alta de empresas (KYC) y plazos.
- **Otras:** Adyen for Platforms y similares.
- **Entregable de esta investigación:** una tabla comparativa con plazos de retención, costes, KYC, reembolsos y validación por el abogado. Se decide la pasarela antes del módulo M5.

### 7.4 Pendiente de decidir
- Qué pasa con la señal en un **no-show** y en cada tipo de **cancelación**.
- Si la reserva se hace con mucha antelación y la retención no da para tanto, ¿se cobra más tarde o se transfiere antes?

---

## 8. Roles y permisos

| Rol (documento) | En Favent | Puede |
|---|---|---|
| Super Admin | Equipo Favent | Todo; alta de spots y QR; liquidaciones manuales; auditoría |
| Business Owner | Administrador de la empresa | Su empresa, sus usuarios, acuerdos, modo del spot |
| Business Staff | Usuario de la empresa | Lo que le dé el Administrador (p. ej. Agenda y escanear QR) |
| Service Provider | Empresa que presta el servicio | Sus servicios, su Agenda, sus reservas, validar QR |
| Intermediary | Empresa que recomienda | Recomendar, sus reservas, sus comisiones |
| Connect Spot | Empresa que recomienda con punto físico | Su panel de spot: QR, reservas atribuidas, ganancias, perfil |
| Customer | Cliente sin cuenta | Su reserva, mediante enlace seguro |

Control en el **backend**: políticas RLS de Supabase por empresa y por papel, más comprobación en cada endpoint. Las vistas de Catalog no contienen columnas de comisión, acuerdos ni repartos.

---

## 9. Favent Catalog

### 9.1 Pantallas (mobile-first)
- **Entrada:** sin código de spot válido, «Accede desde el QR de tu alojamiento».
- **Home:** hero con foto (del spot si tiene landing), buscador, fecha, categorías, destacados, populares, empresas recomendadas, descubrir, ayuda. «Discover more. Experience better.»
- **Explore:** buscador; filtros por categoría, ubicación, precio, fecha y duración; orden por relevancia, precio y popularidad.
- **Ficha:** fotos, nombre, descripción, quién presta el servicio, que Favent actúa como intermediario, ubicación, **precio total**, duración, capacidad, disponibilidad, incluye/no incluye, condiciones, cancelación, seguridad, «Reservar».
- **Reserva:** actividad → fecha → horario → personas → datos del cliente → resumen («Precio total», «Pagas ahora», «Pagas en el lugar», gastos de gestión cuando existan) → aceptar condiciones → pago → confirmación con código y QR.
- **Mi reserva:** desde el enlace seguro: fecha y hora, actividad, quién presta el servicio, código, QR, estado, contacto, condiciones y cancelación.
- **Nunca** aparece la palabra «comisión» en Catalog, ni en emails, recibos o QR del cliente.

### 9.2 Categorías (configurables, dos niveles)
| Favent | Catalog |
|---|---|
| Náutica | Boat experiences · Water sports · Diving and snorkeling |
| Ciclismo | Outdoor activities · Adventure |
| Traslados | Excursions |
| Servicios privados | Gastronomy · Private experiences |
| Otros | Other local services |

### 9.3 Qué servicios se muestran
Los publicados (máximo 2 por empresa), filtrados por el modo del spot: «Solo colaboradores» o «Todo libre».

---

## 10. Connect Spot

- **Tipos:** hoteles, hostales, apartamentos turísticos, restaurantes, beach clubs, comercios, agencias, oficinas de turismo, transporte…
- **Alta:** solo Favent. Crea el spot (`CS-001`…), lo vincula a la empresa, elige hotel o habitaciones y genera QR y URL.
- **Material:** QR y URL personalizados; plantillas de tarjeta, flyer, cartel de recepción, expositor y pegatina con identidad Connect Spot (P0: QR descargable en PNG/PDF; el resto, P1).
- **Landing** (`/cs/<slug>`): nombre, logotipo, portada, descripción, destacados y acceso al catálogo (P1 según el documento; en P0, cabecera simple con el nombre del spot).
- **Panel del spot** (en `app.favent.app`):
  - Resumen: escaneos, visitas, reservas, volumen bruto, comisiones, liquidaciones pendientes.
  - Mi QR: ver, descargar, copiar enlace, ver landing.
  - Reservas: atribuidas, estado, fecha, actividad, importe, liquidación.
  - Rendimiento (P1): conversión, ticket medio, por periodo.
  - Ganancias: generadas, pendientes, liquidadas, ajustes.
  - Perfil: datos, logo, fotos, contacto, landing y modo «Solo colaboradores» / «Todo libre».

---

## 11. Plan por módulos (beta)

Cada módulo deja la beta funcionando y se prueba antes de pasar al siguiente. Todo en el **repositorio de la app**.

| # | Módulo | Prioridad | Contenido | Pruebas clave |
|---|---|---|---|---|
| M0 | Base | P0 | Repo Next.js, Supabase (entornos dev/prod), autenticación de empresas, `businesses`, `business_members`, roles, RLS, `audit_logs` | Un usuario no ve datos de otra empresa |
| M1 | Servicios y Agenda | P0 | `services`, imágenes, categorías, límite de 2 publicados, `bookings` con no solape, reservas propias | Dos reservas a la vez en el mismo barco → rechazo |
| M2 | Red | P0 | Colaboradores (aceptan las dos), acuerdos de comisión | Acuerdo pactado manda sobre la ficha |
| M3 | Connect Spot (alta) | P0 | Panel Favent: alta de spot, puntos de acceso, QR/URL, modo del spot | Solo Super Admin crea spots |
| M4 | Catalog + atribución | P0 | Entrada con código, home, explore básico, ficha, sesión y eventos de atribución, vistas públicas sin comisión | La API de Catalog no devuelve comisiones; cambiar la URL no cambia el spot; último spot gana |
| M5 | Reserva y pago | P0 | Flujo de reserva, instantánea económica, pago de la señal con la pasarela elegida (tras 7.3), webhooks, idempotencia, enlace seguro, email de confirmación con QR | Pago duplicado → una sola reserva; sin webhook no hay «pagado» |
| M6 | Validación y liquidación | P0 | Escanear QR, `qr_validations`, repartos, transferencias, `pendiente_manual`, reembolsos | Un QR solo se canjea una vez; liquidado solo con confirmación |
| M7 | Panel del spot | P0 | Resumen, Mi QR, Reservas, Ganancias, Perfil | Un spot no ve a otro |
| M8 | Siguiente fase | P1 | Buscador avanzado, filtros completos, landings, conversión, valoraciones verificadas, notificaciones, favoritos, material imprimible | |
| — | Futuro | P2 | Recomendaciones, fidelización, premium, patrocinados, app nativa, nuevas verticales, internacional (Varsovia: BLIK/PLN) | |

Para cada módulo, el PR incluye: componentes, endpoints, modelos, validaciones, permisos, estados, manejo de errores y pruebas. Sin datos ficticios en producción, sin botones sin función y sin confirmaciones simuladas.

**Objetivo de la beta:** un huésped entra desde el QR, descubre un servicio, lo reserva y paga la señal, y recibe la confirmación. Favent sabe qué hotel lo originó, quien presta el servicio valida el QR y el reparto queda registrado para liquidar.

---

## 12. Piloto y métricas
- Mallorca, **5–10 Connect Spots** y suficientes servicios para un catálogo atractivo. No crecer hasta ver tráfico y reservas reales.
- Métricas: spots activos, escaneos, visitas, reservas, conversión, ticket medio, volumen bruto, comisiones, cancelaciones y retención de spots.

---

## 13. Este repositorio (www.favent.app)
- **Ahora:** sin cambios. Corregir `DESIGN.md` → *Known Gaps* (el formulario y el email ya existen) y el token `ink-2`.
- **Al lanzar:** una sección después de «Para quién es» y el perfil «Tengo un establecimiento» en la lista de espera; actualizar `CLAUDE.md` y `DESIGN.md`.

---

## 14. Qué hacer con la parte legal (antes de lanzar Catalog, no ahora)

Hoy Favent solo vende a empresas. Con Catalog, un turista paga desde su móvil y eso trae obligaciones nuevas. **Antes de lanzar Catalog**, que un abogado o una asesoría que conozca plataformas online revise esta lista:

| Tema | Qué significa | Qué hay que tener |
|---|---|---|
| Información antes de pagar | Quién presta el servicio, quién intermedia, precio total, cuánto ahora y cuánto después, cancelación | Ficha y resumen de pago con esos datos |
| Cancelación y desistimiento | En ocio con fecha concreta normalmente no hay 14 días de desistimiento, pero hay que confirmarlo | Política de cancelación por servicio, visible antes de pagar |
| Gastos de gestión | Cualquier cargo obligatorio va en el precio total desde el principio | Incluido y desglosado antes de pagar; nombre validado por el abogado |
| Datos personales (RGPD) | Nombre, email o teléfono del huésped y cookie de atribución | Privacidad, aviso legal y cookies en `catalog.favent.app` |
| Condiciones para empresas | Favent como marketplace (orden de servicios, cobros, incidencias) | Condiciones de uso para empresas y spots |
| Dinero de terceros | Favent retiene la señal hasta el canje | Pasarela con licencia (Stripe Connect o Mangopay) |
| Hacienda | Las plataformas informan de lo que ganan los vendedores (DAC7) | Lo gestiona la asesoría |
| La palabra «seguro» | Puede confundirse con un producto de seguros | «Garantía de cobro» o «Pago protegido» |

Se suma a lo ya pendiente para la web: aviso legal, privacidad y cookies.

---

## 15. Pendientes
1. Importes del precio por QR y de la tarifa mensual.
2. Elegir la pasarela de pago tras la investigación de 7.3.
3. Reglas de la señal en no-show y cancelaciones.
4. Crear el repositorio de la app y los entornos de Supabase y Stripe/Mangopay.
5. Revisión legal (sección 14).
