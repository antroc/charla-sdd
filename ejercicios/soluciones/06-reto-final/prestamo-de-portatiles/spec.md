# Especificación: PrestamoPortatiles

> [!NOTE]
> Este fichero es la **especificación** (`spec.md`): describe qué tiene que hacer PrestamoPortatiles y por qué, en lenguaje natural y sin decidir tecnología. Es el paso 1 del flujo SDD (*Spec-Driven Development*, desarrollo guiado por especificaciones) y se genera con `/speckit.specify` a partir de la [petición](peticion.md); la sección «Aclaraciones» la añade después `/speckit.clarify` (paso 2). En un proyecto real vive en `specs/001-prestamo-portatiles/spec.md`.

**Carpeta/rama:** `specs/001-prestamo-portatiles/` · **Creada:** 2026-11-03 · **Estado:** lista para planificar (aclaraciones resueltas el 2026-11-03)

**Petición original (la de Ana, tal como la dejó tras corregirla):**

> Oficina presta portátiles y proyectores a la gente de la empresa y lo apunta todo en un cuaderno: nunca sabemos quién tiene cada equipo ni cuándo lo va a devolver. Hay 10 portátiles y 4 proyectores, y cuando alguien pide uno que ya está fuera, no podemos decirle cuándo vuelve. Cualquier empleado tiene que poder pedir un equipo para unas fechas, y Oficina, que es quien lo entrega y lo recoge, tiene que poder anotar la entrega y la devolución. Quien tiene un equipo tiene que poder pedir más días si los necesita, y todo el mundo tiene que poder ver qué equipos hay libres hoy y quién tiene los que faltan. Los préstamos son de pocos días, y cada equipo prestado tiene que llevar siempre el nombre de una persona y una fecha de devolución. En la primera versión no entra comprar ni reparar equipos, ni llevar el inventario de la empresa.

**Qué vas a encontrar**

- [Historias de usuario y escenarios](#historias-de-usuario-y-escenarios-user-scenarios--testing)
- [Aclaraciones](#aclaraciones-clarifications)
- [Requisitos](#requisitos-requirements)
- [Criterios de éxito](#criterios-de-éxito-success-criteria)
- [Supuestos](#supuestos-assumptions)
- [Fuera de alcance](#fuera-de-alcance-out-of-scope)

## Historias de usuario y escenarios (User Scenarios & Testing)

Cada criterio de aceptación se escribe en tres partes: **Dado** una situación de partida, **cuando** ocurre algo, **entonces** el sistema responde de una forma concreta. Así cualquiera puede comprobar si se cumple sin saber programar.

### Historia de usuario 1 — Pedir un equipo para unas fechas y recogerlo (Prioridad: P1)

Marta necesita un proyector el miércoles 18 de noviembre para enseñar un informe a un cliente. Entra en PrestamoPortatiles, elige «Proyector», indica del miércoles 18 al jueves 19, ve qué proyectores están libres, elige uno y confirma. La aplicación le dice hasta qué día puede quedárselo. El miércoles pasa por Oficina, Ana le entrega el proyector y lo anota; desde ese momento el proyector figura a nombre de Marta.

**Por qué esta prioridad:** es el motivo de la aplicación. Con solo esto el cuaderno deja de hacer falta para pedir y entregar: ningún equipo sale sin una persona y una fecha de devolución, y quien pide uno que ya está fuera sabe quién lo tiene y hasta cuándo.

**Prueba independiente:** se puede probar por completo pidiendo un equipo desde cero, entregándolo y comprobando que figura prestado a nombre de la persona, con sus fechas, y que nadie más puede pedirlo para esos días. Aporta valor por sí sola, aunque no existan las historias 2 y 3.

**Criterios de aceptación:**

1. **Dado** que PORT-03 y PORT-07 están libres de lunes 16 a miércoles 18 de noviembre, **cuando** Marta elige «Portátil» e indica esas fechas, **entonces** ve PORT-03 y PORT-07 entre los equipos libres, cada uno con su código y su descripción.
2. **Dado** que Marta ha elegido PROY-02 del miércoles 18 al jueves 19 de noviembre, **cuando** confirma, **entonces** el sistema guarda el préstamo y muestra «Préstamo confirmado: PROY-02, del miércoles 18 al jueves 19 de noviembre. Devuélvelo como máximo el jueves 19», con Marta como responsable.
3. **Dado** que Luis tiene PORT-03 del lunes 16 al miércoles 18, **cuando** Marta pide PORT-03 del martes 17 al jueves 19, **entonces** el sistema rechaza la petición e indica que Luis lo tiene hasta el miércoles 18 y que queda libre desde el jueves 19.
4. **Dado** que Marta pide un portátil del lunes 16 al lunes 30 de noviembre (once días laborables), **cuando** intenta confirmar, **entonces** el sistema rechaza la petición e indica que el máximo son diez días laborables.
5. **Dado** que Marta pide un portátil que empieza el sábado 21 de noviembre, **cuando** intenta confirmar, **entonces** el sistema rechaza la petición e indica que los préstamos empiezan y terminan en día laborable, de lunes a viernes.
6. **Dado** que Marta tiene reservado PROY-02 desde el miércoles 18, **cuando** Ana, de Oficina, lo marca como entregado ese día, **entonces** el préstamo pasa a «entregado» y PROY-02 figura prestado a Marta con su fecha de devolución.
7. **Dado** que Marta no es de Oficina, **cuando** abre su préstamo reservado, **entonces** no ve la opción de marcarlo como entregado.

---

### Historia de usuario 2 — Devolver o prorrogar (Prioridad: P2)

El jueves 19, Marta devuelve el proyector en Oficina y Ana anota la devolución: el proyector vuelve a estar libre para los demás. Otro día, Jorge ve que no va a terminar su trabajo con el portátil y pide un día más: la aplicación le da la nueva fecha de devolución. La víspera de cada devolución, a la persona responsable le llega un correo que se lo recuerda.

**Por qué esta prioridad:** sin ella, la aplicación solo sabe cuándo debería volver cada equipo, no si ha vuelto, y quien necesita más días tiene que pedírselos a Oficina de palabra. La aplicación funciona sin esta historia (cada préstamo termina en su fecha), pero el cuaderno seguiría haciendo falta para saber qué equipos han vuelto de verdad.

**Prueba independiente:** se puede probar con un préstamo entregado: registrar su devolución y comprobar que el equipo vuelve a estar libre, y pedir una prórroga y comprobar que la fecha de devolución cambia.

**Criterios de aceptación:**

1. **Dado** que Marta tiene PROY-02 entregado hasta el jueves 19 de noviembre, **cuando** Ana registra la devolución ese jueves, **entonces** el préstamo se cierra y PROY-02 aparece libre.
2. **Dado** que Jorge ya ha prorrogado una vez su préstamo de PORT-05, **cuando** pide prorrogarlo otra vez, **entonces** el sistema rechaza la prórroga e indica que un préstamo solo se puede prorrogar una vez.
3. **Dado** que PORT-06 está reservado por Marta desde el lunes 23 de noviembre y Luis lo tiene hasta el miércoles 18, **cuando** Luis pide prorrogar su préstamo hasta el martes 24, **entonces** el sistema rechaza la prórroga e indica que PORT-06 solo está libre hasta el viernes 20.
4. **Dado** que el préstamo de Luis de PORT-04 venció el viernes 20 de noviembre y hoy es lunes 23 sin que se haya devuelto, **cuando** Luis pide prorrogarlo, **entonces** el sistema rechaza la prórroga e indica que tiene que devolver el equipo a Oficina.

---

### Historia de usuario 3 — Ver qué hay disponible hoy (Prioridad: P3)

Jorge necesita un proyector para esta tarde y no quiere bajar a Oficina para averiguar si queda alguno. Abre «Hoy» y ve los 14 equipos: los libres, y de los demás quién los tiene y cuándo los devuelve. Si ve que Luis tiene PROY-01 hasta mañana, sabe a quién pedírselo.

**Por qué esta prioridad:** da visibilidad y refuerza la transparencia (cualquiera sabe de quién es cada equipo), pero la aplicación ya es útil sin ello: al pedir un equipo ocupado, el rechazo ya dice quién lo tiene y hasta cuándo.

**Prueba independiente:** se puede probar creando varios préstamos de distintas personas y comprobando que la vista de hoy muestra cada equipo con su estado, su responsable y su fecha de devolución.

**Criterios de aceptación:**

1. **Dado** que hoy hay tres portátiles y un proyector prestados, **cuando** cualquier persona abre «Hoy», **entonces** ve los 14 equipos: diez libres y cuatro prestados, cada uno de estos con el nombre de su responsable y su fecha de devolución.
2. **Dado** que Luis tenía que devolver PORT-04 el viernes 20 de noviembre y hoy es lunes 23 sin que se haya devuelto, **cuando** cualquier persona abre «Hoy», **entonces** PORT-04 aparece como «vencido», con el nombre de Luis y la fecha del viernes 20.
3. **Dado** que PROY-01 se ha devuelto esta mañana, **cuando** cualquier persona abre «Hoy», **entonces** PROY-01 aparece libre y sin persona responsable.

---

### Casos límite (Edge Cases)

- **Solapamiento por un solo día:** un préstamo de PORT-03 del lunes 16 al miércoles 18 choca con otro del miércoles 18 al viernes 20, aunque solo coincidan en un día. Dos préstamos consecutivos (hasta el miércoles 18 y desde el jueves 19) no chocan. Si dos personas confirman el mismo equipo y las mismas fechas en el mismo segundo, solo se guarda una petición; la otra recibe el rechazo por solapamiento.
- **Límite de días y fechas pasadas:** de lunes 16 a viernes 27 de noviembre (diez días laborables) se acepta; hasta el lunes 30 (once) se rechaza (máximo diez; ver Aclaraciones). Empezar hoy se permite; empezar antes de hoy, no.
- **Fin de semana:** una petición que empieza el sábado 21 o termina el domingo 29 se rechaza: la recogida y la devolución son siempre en día laborable.
- **Prórroga rechazada:** se rechaza la segunda prórroga de un mismo préstamo, la de un préstamo que ya ha vencido y la que choca con el préstamo siguiente del mismo equipo; en este último caso, el mensaje dice hasta qué fecha está libre.
- **Equipo vencido:** si un equipo no se devuelve en su fecha, sigue figurando a nombre de la misma persona, con la etiqueta «vencido», hasta que Oficina registra la devolución. No se envía ningún aviso de retraso: Oficina lo ve en «Hoy» y lo reclama. La aplicación no lo bloquea: otra persona puede pedirlo para fechas posteriores, y Oficina decide qué hacer al entregarlo.
- **Nadie recoge el equipo:** si la persona no pasa por Oficina, el préstamo sigue reservado y el equipo ocupado hasta su fecha de devolución. Oficina puede cerrarlo con la opción de registrar la devolución, y el equipo vuelve a estar libre.

## Aclaraciones (Clarifications)

### Sesión 2026-11-03

- P: ¿Cuántos días puede durar un préstamo como máximo? → R: Diez días laborables.
- P: ¿Se puede prorrogar un préstamo? → R: Una sola vez, y sin pasar del máximo: la prórroga cuenta dentro de los diez días.
- P: ¿Hay que guardar para qué se pide el equipo? → R: No: no se guarda el motivo.
- P: ¿Hay que avisar antes de la devolución? → R: Sí: un correo a la persona responsable el día laborable anterior a la fecha de devolución (si cae en lunes, el viernes anterior).

## Requisitos (Requirements)

### Requisitos funcionales (Functional Requirements)

Redactados en EARS (*Easy Approach to Requirements Syntax*), una forma sencilla y estructurada de redactar requisitos: cada uno es una sola frase comprobable con el verbo «deberá».

- **RF-001**: El sistema deberá mostrar la lista de equipos con su código, su tipo y su estado de hoy (libre, prestado o vencido) y, en los prestados y vencidos, el nombre de la persona responsable y la fecha de devolución.
- **RF-002**: CUANDO una persona indica un tipo de equipo y unas fechas, el sistema deberá mostrar qué equipos de ese tipo están libres en ese periodo.
- **RF-003**: CUANDO una persona confirma un préstamo, el sistema deberá guardarlo a su nombre y mostrar un mensaje de confirmación con el equipo, las fechas y la fecha de devolución.
- **RF-004**: SI el equipo pedido ya está prestado o reservado en alguna de las fechas pedidas, ENTONCES el sistema deberá rechazar la petición e indicar quién lo tiene y cuándo queda libre.
- **RF-005**: SI una petición de préstamo o de prórroga incumple un límite (empezar antes de hoy, empezar o terminar en fin de semana, superar diez días laborables en total, pedir una segunda prórroga o prorrogar un préstamo vencido), ENTONCES el sistema deberá rechazarla e indicar qué límite se incumple.
- **RF-006**: DONDE la persona tenga rol de Oficina, el sistema deberá permitir marcar un préstamo reservado como entregado.
- **RF-007**: CUANDO Oficina registra la devolución de un equipo, el sistema deberá dejarlo libre y cerrar el préstamo.
- **RF-008**: CUANDO la persona responsable pide prorrogar su préstamo dentro de los límites, el sistema deberá alargar la fecha de devolución y mostrar la nueva fecha.
- **RF-009**: CUANDO llega el día laborable anterior a la fecha de devolución de un préstamo reservado o entregado, el sistema deberá enviar un correo a la persona responsable con el equipo y la fecha de devolución.

Dos apuntes sobre la regla «un requisito, una sola cosa»: RF-005 agrupa cinco límites en un solo SI porque la respuesta del sistema es la misma para todos (rechazar e indicar el límite); cada límite se comprueba por separado en los casos límite y en las pruebas, y si la respuesta fuera distinta para alguno sería un requisito aparte. RF-001 reúne en una sola lista el estado de cada equipo y, si está fuera, quién lo tiene y cuándo vuelve, porque son la misma información vista en una pantalla.

Patrones EARS usados, para quien quiera comprobarlos:

| Patrón | Requisitos |
|---|---|
| Ubicuo («El sistema deberá…») | RF-001 |
| Por evento (CUANDO…) | RF-002, RF-003, RF-007, RF-008, RF-009 |
| Comportamiento no deseado (SI…, ENTONCES…) | RF-004, RF-005 |
| Opcional (DONDE…) | RF-006 |

Este proyecto no necesita el patrón por estado (MIENTRAS…).

Qué requisitos necesita cada historia de usuario (HU); sirve para comprobar después que el plan y las tareas no se dejan ninguno:

| Historia | Requisitos |
|---|---|
| HU1 — Pedir un equipo y recogerlo | RF-002, RF-003, RF-004, RF-005, RF-006 |
| HU2 — Devolver o prorrogar | RF-004, RF-005, RF-007, RF-008, RF-009 |
| HU3 — Ver qué hay disponible hoy | RF-001 |

### Entidades clave (Key Entities)

Las «cosas» de las que la aplicación guarda información y qué datos tiene cada una:

- **Equipo**: uno de los 14 portátiles y proyectores. Tiene código único (PORT-01 a PORT-10 y PROY-01 a PROY-04), tipo (portátil o proyector) y una descripción corta. Si está libre, prestado o vencido no se guarda: se deduce de sus préstamos.
- **Préstamo**: el uso de un equipo por una persona entre dos fechas. Tiene equipo, persona responsable, fecha de inicio, fecha de devolución, estado (reservado, entregado o cerrado), si ya se prorrogó, si ya se envió el aviso de devolución, y quién lo entregó y quién registró la devolución. Un préstamo pertenece exactamente a un equipo y a una persona. No tiene motivo.
- **Persona**: cualquier empleado. Tiene nombre, correo corporativo (que la identifica) y rol (empleado u Oficina). No se guarda ningún otro dato.

## Criterios de éxito (Success Criteria)

### Resultados medibles (Measurable Outcomes)

- **CE-001**: Pedir un equipo, desde que se abre la aplicación hasta que aparece la confirmación, lleva menos de 2 minutos.
- **CE-002**: Cero préstamos solapados: en ningún momento existen dos préstamos sin cerrar del mismo equipo con fechas que se crucen.
- **CE-003**: Cero préstamos sin persona responsable o sin fecha de devolución.
- **CE-004**: El aviso llega, antes de las 09:00 del día laborable anterior a la fecha de devolución, al 100 % de los préstamos reservados o entregados que ya existen a las 08:00 de ese día.

Cómo se medirán: CE-001 con una prueba con 5 personas de distintos equipos antes de la puesta en marcha; CE-002 con pruebas automáticas y una comprobación semanal de los datos; CE-003 con una consulta semanal que cuenta los préstamos sin una de las dos cosas (tiene que dar 0); CE-004 con los registros de envío del servidor de correo durante el primer mes.

## Supuestos (Assumptions)

- Todas las personas usuarias tienen correo corporativo y entran con el acceso corporativo existente; la aplicación no gestiona contraseñas.
- Hay 14 equipos: 10 portátiles de 14 pulgadas con cargador (PORT-01 a PORT-10) y 4 proyectores con cable HDMI (PROY-01 a PROY-04). Los datos los proporciona Oficina y cambian muy pocas veces al año.
- Un día laborable es de lunes a viernes. La primera versión no conoce los festivos: Oficina los gestiona a mano.
- Un préstamo ocupa el equipo desde su fecha de inicio hasta su fecha de devolución, ambas incluidas, mientras no esté cerrado. Oficina entrega y recoge de lunes a viernes.
- Oficina es el único rol con permisos especiales (entregar equipos y registrar devoluciones); Ana fija qué personas lo tienen.
- No hay límite de antelación para pedir un equipo ni de equipos por persona. Si Ana quiere alguno, es un requisito nuevo.
- Hay un servidor de correo corporativo disponible para enviar los avisos.
- El volumen es pequeño: unas 200 personas y unas decenas de préstamos al mes.

## Fuera de alcance (Out of Scope)

- Cancelar o cambiar las fechas de un préstamo ya pedido: se cierra con la opción de registrar la devolución y se vuelve a pedir.
- Otros equipos (monitores, cámaras, cables sueltos) y accesorios: solo portátiles y proyectores.
- Compra, reparación, altas y bajas de equipos, e inventario de la empresa.
- Calendario de festivos.
- Avisos automáticos de retraso y reclamación de equipos vencidos: Oficina los ve en «Hoy» y los reclama a mano.
- Guardar el motivo del préstamo (decisión de Ana) y cualquier estadística por persona o por departamento.
- Integración con el calendario corporativo o con el inventario de IT.
- Aplicación móvil nativa: basta con que se pueda usar desde el móvil.

---

⬅️ [Anterior: Constitución](constitution.md) · 🏠 [Índice del ejemplo](README.md) · ➡️ [Siguiente: Plan técnico](plan.md)
