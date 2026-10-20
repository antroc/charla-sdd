# Especificación: ReservaSalas

> [!NOTE]
> Este fichero es la **especificación** (`spec.md`): describe qué tiene que hacer ReservaSalas y por qué, en lenguaje natural y sin decidir tecnología. Es el paso 1 del flujo SDD (*Spec-Driven Development*, desarrollo guiado por especificaciones) y se genera con `/speckit.specify` a partir de la descripción de Ana; la sección «Aclaraciones» la añade después `/speckit.clarify` (paso 2). En un proyecto real vive en `specs/001-reserva-salas/spec.md`.

**Carpeta/rama:** `specs/001-reserva-salas/` · **Creada:** 2026-10-06 · **Estado:** lista para planificar (aclaraciones resueltas el 2026-10-07)

**Petición original (descripción de Ana):**

> Quiero una aplicación interna para reservar las 12 salas de reuniones de la empresa, repartidas en 3 plantas. Hoy nos apuntamos en una hoja de cálculo compartida y pasa de todo: dos equipos en la misma sala, salas reservadas que se quedan vacías y reservas de las que nadie sabe quién es el responsable. Cualquier empleado tiene que poder ver qué salas están libres en una franja, reservar una, cancelar o cambiar su reserva, y ver sus reservas y las de hoy en cada sala. El horario de oficina es de 08:00 a 20:00 y no queremos reservas de más de 4 horas. Administración tiene que poder marcar una sala en mantenimiento.

**Qué vas a encontrar**

- [Historias de usuario y escenarios](#historias-de-usuario-y-escenarios-user-scenarios--testing)
- [Aclaraciones](#aclaraciones-clarifications)
- [Requisitos](#requisitos-requirements)
- [Criterios de éxito](#criterios-de-éxito-success-criteria)
- [Supuestos](#supuestos-assumptions)
- [Fuera de alcance](#fuera-de-alcance-out-of-scope)

## Historias de usuario y escenarios (User Scenarios & Testing)

Cada criterio de aceptación se escribe en tres partes: **Dado** una situación de partida, **cuando** ocurre algo, **entonces** el sistema responde de una forma concreta. Así cualquiera puede comprobar si se cumple sin saber programar.

### Historia de usuario 1 — Reservar una sala (Prioridad: P1)

Marta quiere reunir a su equipo el jueves de 10:00 a 11:00. Entra en ReservaSalas, indica la fecha y la franja, ve qué salas están libres (con su planta y su aforo), elige una y confirma. A partir de ese momento la sala es suya en esa franja y nadie más puede reservarla.

**Por qué esta prioridad:** es el motivo de la aplicación. Sin esto no hay producto; con solo esto ya se evitan los choques de la hoja de cálculo.

**Prueba independiente:** se puede probar por completo creando una reserva desde cero y comprobando que la sala deja de aparecer como libre en esa franja. Aporta valor por sí sola, aunque no existan las historias 2 y 3.

**Criterios de aceptación:**

1. **Dado** que la sala Mediterráneo está libre el jueves de 10:00 a 11:00, **cuando** Marta indica esa fecha y esa franja, **entonces** Mediterráneo aparece en la lista de salas libres con su planta (1.ª) y su aforo (8 personas).
2. **Dado** que Marta ha elegido Mediterráneo para el jueves de 10:00 a 11:00, **cuando** confirma la reserva, **entonces** el sistema la guarda y muestra «Reserva confirmada: Mediterráneo, jueves 22 de octubre, de 10:00 a 11:00», con Marta como responsable.
3. **Dado** que Mediterráneo ya está reservada el jueves de 10:30 a 11:30, **cuando** Marta intenta reservarla de 10:00 a 11:00, **entonces** el sistema rechaza la reserva e indica que la sala está ocupada de 10:30 a 11:30.
4. **Dado** que Marta pide una franja de 09:00 a 14:00 (5 horas), **cuando** intenta confirmar, **entonces** el sistema rechaza la reserva e indica que el máximo son 4 horas.
5. **Dado** que la sala Ártico está en mantenimiento, **cuando** Marta consulta la disponibilidad, **entonces** Ártico aparece marcada como «en mantenimiento» y no se puede elegir.
6. **Dado** que Marta pide una franja de 19:30 a 20:30, **cuando** intenta confirmar, **entonces** el sistema rechaza la reserva e indica que el horario de reservas es de 08:00 a 20:00.
7. **Dado** que Marta ha confirmado una reserva, **cuando** el sistema la guarda, **entonces** Marta recibe un correo con la sala, la fecha y la franja.

---

### Historia de usuario 2 — Cancelar o modificar mi reserva (Prioridad: P2)

A Marta se le cae la reunión del jueves. Entra en ReservaSalas, localiza su reserva y la cancela; la sala vuelve a estar libre para los demás. Otro día la reunión se mueve una hora: Marta cambia la franja sin tener que cancelar y volver a reservar.

**Por qué esta prioridad:** es una de las causas de las salas vacías con reserva: la gente no cancela porque es incómodo. Sin esto la aplicación funciona, pero el problema de las salas vacías sigue ahí.

**Prueba independiente:** se puede probar creando una reserva, cancelándola y comprobando que la franja vuelve a aparecer libre; y modificándola y comprobando que la franja antigua se libera y la nueva queda ocupada.

**Criterios de aceptación:**

1. **Dado** que Marta tiene una reserva en Cantábrico el viernes de 12:00 a 13:00, **cuando** la cancela, **entonces** el sistema la marca como cancelada, muestra un mensaje de confirmación y Cantábrico vuelve a aparecer libre en esa franja.
2. **Dado** que Marta tiene una reserva de 12:00 a 13:00, **cuando** la cambia a 13:00-14:00 y esa franja está libre, **entonces** el sistema guarda el cambio y libera la franja de 12:00 a 13:00.
3. **Dado** que Marta cambia su reserva a una franja que ya está ocupada, **cuando** confirma, **entonces** el sistema rechaza el cambio, indica qué franja está ocupada y mantiene la reserva original intacta.
4. **Dado** que Luis ve una reserva de Marta, **cuando** intenta cancelarla, **entonces** el sistema se lo impide e indica que solo la persona responsable o administración pueden hacerlo.
5. **Dado** que Ana tiene permisos de administración, **cuando** cancela una reserva de Marta, **entonces** el sistema la cancela y la reserva queda identificada como «cancelada por administración».

---

### Historia de usuario 3 — Ver mis reservas y las de hoy en cada sala (Prioridad: P3)

Jorge quiere saber qué tiene reservado esta semana sin buscar entre correos. Entra en «Mis reservas» y ve la lista ordenada por fecha. Además, cualquier persona puede ver, para cada sala, quién la tiene reservada hoy y a qué hora, para saber si la sala que ve vacía está libre de verdad.

**Por qué esta prioridad:** da visibilidad y refuerza la transparencia, pero la aplicación ya es útil sin ello.

**Prueba independiente:** se puede probar creando varias reservas de distintas personas y comprobando que cada una ve solo las suyas en «Mis reservas» y que la vista de hoy muestra las de todas las personas, con su nombre.

**Criterios de aceptación:**

1. **Dado** que Jorge tiene dos reservas futuras y una pasada, **cuando** abre «Mis reservas», **entonces** ve las dos futuras ordenadas por fecha y no ve la pasada.
2. **Dado** que hoy hay tres reservas en Atlántico, **cuando** cualquier persona consulta la vista de hoy, **entonces** ve las tres con hora de inicio, hora de fin y nombre de la persona responsable.
3. **Dado** que Jorge no tiene ninguna reserva, **cuando** abre «Mis reservas», **entonces** ve el mensaje «No tienes reservas» y un enlace para reservar.
4. **Dado** que Jorge canceló ayer una reserva para mañana, **cuando** abre «Mis reservas», **entonces** esa reserva no aparece y la franja figura libre en la disponibilidad.

---

### Casos límite (Edge Cases)

- **Solapamiento parcial:** una franja de 10:00 a 11:00 choca con otra de 10:30 a 11:30 en la misma sala, aunque no coincidan por completo. Dos reservas consecutivas (10:00-11:00 y 11:00-12:00) no chocan.
- **Fuera del horario de oficina:** una reserva de 07:30 a 08:30 o de 19:30 a 20:30 se rechaza; el horario es de 08:00 a 20:00.
- **Sala en mantenimiento:** no admite reservas nuevas; las reservas ya existentes se mantienen y administración avisa a las personas afectadas (fuera de la aplicación).
- **Marcar una sala en mantenimiento:** **Dado** que Ana tiene permisos de administración, **cuando** marca la sala Ártico en mantenimiento, **entonces** Ártico deja de aparecer como disponible y sus reservas existentes se mantienen. Quien no tiene permisos de administración no ve esa opción.
- **Más de 4 horas:** una reserva de 09:00 a 14:00 se rechaza aunque la sala esté libre.
- **«Para ya mismo» con la sala ocupada:** si son las 10:10 y alguien pide Mediterráneo de 10:00 a 11:00 pero está reservada, el sistema rechaza la petición e indica hasta qué hora está ocupada. Reservar una franja que ya ha empezado está permitido mientras la hora de fin sea futura.
- **Antelación excesiva:** una reserva para dentro de 45 días se rechaza (máximo 30 días; ver Aclaraciones).
- **Fin anterior al inicio:** una franja de 11:00 a 10:00 se rechaza con un mensaje claro.
- **Dos personas a la vez:** si dos personas confirman la misma sala y la misma franja en el mismo segundo, solo una reserva se guarda; la otra recibe el rechazo por solapamiento.

## Aclaraciones (Clarifications)

### Sesión 2026-10-07

- P: ¿Se pueden hacer reservas recurrentes (por ejemplo, todos los lunes)? → R: No en la primera versión.
- P: ¿Quién puede cancelar una reserva ajena? → R: Solo administración.
- P: ¿Hay que avisar por correo? → R: Sí: un correo al confirmar, al modificar y al cancelar, para que sirva de comprobante.
- P: ¿Con cuánta antelación máxima se puede reservar? → R: 30 días.
- P: ¿Qué pasa si nadie aparece a la reserva? → R: Fuera de alcance: no se controla la asistencia.

## Requisitos (Requirements)

### Requisitos funcionales (Functional Requirements)

Redactados en EARS (*Easy Approach to Requirements Syntax*), una forma sencilla y estructurada de redactar requisitos: cada uno es una sola frase comprobable con el verbo «deberá».

- **RF-001**: El sistema deberá mostrar la lista de salas con su planta y aforo.
- **RF-002**: CUANDO una persona indica una fecha y una franja horaria, el sistema deberá mostrar qué salas están libres en esa franja.
- **RF-003**: CUANDO una persona confirma una reserva, el sistema deberá guardarla y mostrar un mensaje de confirmación con sala, fecha y hora.
- **RF-004**: El sistema deberá mostrar, junto a cada reserva, el nombre de la persona responsable.
- **RF-005**: SI la franja solicitada se solapa con otra reserva de la misma sala, ENTONCES el sistema deberá rechazar la reserva e indicar qué franja está ocupada.
- **RF-006**: SI la franja solicitada queda fuera del horario de oficina (08:00-20:00), dura más de 4 horas, termina en el pasado o empieza más de 30 días después de hoy, ENTONCES el sistema deberá rechazar la reserva e indicar qué límite se incumple.
- **RF-007**: MIENTRAS una sala esté marcada en mantenimiento, el sistema deberá impedir nuevas reservas en ella.
- **RF-008**: CUANDO la persona responsable de una reserva la cancela o la modifica, el sistema deberá aplicar el cambio, liberar la franja anterior y mostrar un mensaje de confirmación.
- **RF-009**: DONDE la persona tenga permisos de administración, el sistema deberá permitir marcar una sala en mantenimiento.
- **RF-010**: SI una persona sin permisos de administración intenta cancelar o modificar una reserva de la que no es responsable, ENTONCES el sistema deberá rechazar la operación e indicar quién puede hacerlo.
- **RF-011**: CUANDO una reserva se confirma, se modifica o se cancela, el sistema deberá enviar un correo a la persona responsable con la sala, la fecha, la franja y el tipo de cambio.
- **RF-012**: El sistema deberá permitir a cada persona ver sus reservas futuras ordenadas por fecha y, para cada sala, las reservas del día en curso con el nombre de su responsable.

Dos apuntes sobre la regla «un requisito, una sola cosa»: RF-006 agrupa cuatro límites en un solo SI porque la respuesta del sistema es la misma para todos (rechazar e indicar el límite); cada límite se comprueba por separado en los casos límite y en las pruebas, y si la respuesta fuera distinta para alguno sería un requisito aparte. RF-012 reúne dos vistas de la misma información (las reservas activas: las mías y las de hoy) en un solo requisito ubicuo. Que administración pueda cancelar o modificar una reserva ajena queda recogido en RF-010, en el criterio 5 de la historia 2 y en la aclaración 2.

Patrones EARS usados, para quien quiera comprobarlos:

| Patrón | Requisitos |
|---|---|
| Ubicuo («El sistema deberá…») | RF-001, RF-004, RF-012 |
| Por evento (CUANDO…) | RF-002, RF-003, RF-008, RF-011 |
| Por estado (MIENTRAS…) | RF-007 |
| Comportamiento no deseado (SI…, ENTONCES…) | RF-005, RF-006, RF-010 |
| Opcional (DONDE…) | RF-009 |

Qué requisitos necesita cada historia de usuario (HU); sirve para comprobar después que el plan y las tareas no se dejan ninguno:

| Historia | Requisitos |
|---|---|
| HU1 — Reservar una sala | RF-001, RF-002, RF-003, RF-004, RF-005, RF-006, RF-007, RF-011 |
| HU2 — Cancelar o modificar mi reserva | RF-008, RF-010, RF-011 |
| HU3 — Ver mis reservas y las de hoy | RF-004, RF-012 |
| Administración (sin historia propia) | RF-009 |

### Entidades clave (Key Entities)

Las «cosas» de las que la aplicación guarda información y qué datos tiene cada una:

- **Sala**: una de las 12 salas de reuniones. Tiene nombre único (Mediterráneo, Cantábrico, Atlántico, Egeo, Báltico, Adriático, Jónico, Tirreno, Caribe, Índico, Ártico, Mar del Norte), planta (1, 2 o 3), aforo (número de personas) y estado (disponible o en mantenimiento).
- **Reserva**: el uso de una sala por una persona en una franja. Tiene sala, persona responsable, inicio, fin, motivo (opcional, texto corto), estado (activa o cancelada) y quién la canceló o la modificó por última vez. Una reserva pertenece exactamente a una sala y a una persona.
- **Persona**: cualquier empleado. Tiene nombre, correo corporativo (que la identifica) y rol (empleado o administración). No se guarda ningún otro dato.

## Criterios de éxito (Success Criteria)

### Resultados medibles (Measurable Outcomes)

- **CE-001**: Reservar una sala, desde que se abre la aplicación hasta que aparece la confirmación, lleva menos de 1 minuto.
- **CE-002**: Cero reservas solapadas: en ningún momento existen dos reservas activas de la misma sala con franjas que se crucen.
- **CE-003**: El 90 % de las personas completan una reserva sin ayuda la primera vez que usan la aplicación.
- **CE-004**: El listado de disponibilidad se muestra en menos de 2 segundos.

Cómo se medirán: CE-001 y CE-003 con una prueba con 10 personas de distintos equipos antes de la puesta en marcha; CE-002 con pruebas automáticas y una comprobación semanal de los datos; CE-004 cronometrado con las 12 salas y un mes de reservas cargadas.

## Supuestos (Assumptions)

- Todas las personas usuarias tienen correo corporativo y entran con el acceso corporativo existente; la aplicación no gestiona contraseñas.
- No hace falta integrarse con el calendario corporativo en la primera versión.
- Las 12 salas y sus datos los proporciona Ana y cambian muy pocas veces al año. Planta 1: Mediterráneo, Cantábrico, Atlántico y Egeo; planta 2: Báltico, Adriático, Jónico y Tirreno; planta 3: Caribe, Índico, Ártico y Mar del Norte. Aforo: 8 personas en Mediterráneo, 12 en Báltico, 4 en Ártico y 6 en las demás.
- Las reservas se hacen en la hora local de la oficina; no hay sedes en otras zonas horarias.
- El volumen es pequeño: unas 200 personas y unas decenas de reservas al día.
- Hay un servidor de correo corporativo disponible para enviar los avisos.

## Fuera de alcance (Out of Scope)

- Reservas recurrentes.
- Control de asistencia o liberación automática de salas vacías.
- Integración con el calendario corporativo o con las pantallas de las salas.
- Reserva de equipamiento (proyectores, catering) o de puestos de trabajo.
- Aplicación móvil nativa: fuera de alcance; basta con que se pueda usar desde el móvil.

---

⬅️ [Anterior: Constitución](constitution.md) · 🏠 [Índice de la solución](README.md) · ➡️ [Siguiente: Aclaraciones](aclaraciones.md)
