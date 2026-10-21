# Especificación: Solicitud de vacaciones

> **Para quién:** cualquier persona que haya hecho el ejercicio 01; no hace falta programar · **Tiempo de lectura:** ~12 min · **Nivel:** 🟢 básico

Esta es la especificación completa de «Solicitud de vacaciones» que pide el [ejercicio 01](../../01-tu-primera-especificacion-sin-codigo.md), escrita con la [plantilla de especificación](../../plantillas/especificacion.md) y sin una línea de código. Sigue el mismo orden de secciones que la plantilla y los ocho pasos del ejercicio, para que puedas comparar la tuya sección por sección. Cubre los pasos 1 (especificar) y 2 (aclarar) del flujo de SDD (*Spec-Driven Development*, desarrollo guiado por especificaciones): dice **qué** queremos y **por qué**; el **cómo** no aparece.

> [!NOTE]
> Es un ejemplo, no la única respuesta correcta: si la tuya pasa la lista de verificación, es igual de válida aunque tome otras decisiones. Tres de las nuestras son discutibles y podrías haberlas resuelto de otra forma: 1) el solapamiento con vacaciones del equipo avisa pero no bloquea (podrías haberlo prohibido, o limitado a un número de personas fuera a la vez); 2) hay una antelación mínima de 5 días laborables (podrías no poner ninguna y dejar que Marta lo valore, o pedir 15); 3) los días no gastados no pasan al año siguiente de forma automática (es habitual permitir arrastrar unos pocos hasta marzo, y entonces el saldo necesitaría un dato más).

**Qué vas a encontrar**

- [Resumen](#resumen)
- [Historias de usuario y escenarios](#historias-de-usuario-y-escenarios-obligatorio)
- [Aclaraciones](#aclaraciones)
- [Requisitos](#requisitos-obligatorio)
- [Criterios de éxito](#criterios-de-éxito-obligatorio)
- [Supuestos](#supuestos)
- [Fuera de alcance](#fuera-de-alcance)
- [Revisión con la lista de verificación](#revisión-con-la-lista-de-verificación)

**Carpeta/rama:** `001-solicitud-vacaciones` · **Creada:** 2026-10-20 · **Estado:** Borrador (aclaraciones resueltas y lista de verificación pasada el 2026-10-20) · **Petición original:** «Queremos dejar de pedir las vacaciones por correo y saber siempre cuántos días nos quedan.»

## Resumen

Hoy, para pedir vacaciones, Luis escribe un correo a Marta, su manager; Marta contesta cuando puede, a veces por el pasillo, y Jorge, de RRHH, se entera por una copia del correo (o no se entera) y lleva el saldo de días de cada persona en una hoja de cálculo. Eso provoca peticiones que se pierden, personas que no saben cuántos días les quedan y semanas en las que medio equipo está fuera sin que Marta lo haya visto venir. Queremos que cualquier persona pida sus días en un par de minutos y sepa al momento cuántos le quedan, que su manager decida con un motivo cuando rechace y vea quién de su equipo está fuera, y que a Jorge le llegue cada solicitud aprobada sin que nadie la copie a mano.

Quién la va a usar:

- Empleado (Luis): quiere pedir días sin perseguir a nadie y saber en todo momento cuántos le quedan.
- Manager (Marta): quiere decidir rápido, con un motivo si rechaza, y ver quién de su equipo está fuera cada semana.
- RRHH (Jorge): quiere que cada solicitud aprobada le llegue sola, con los días ya descontados, y ver el saldo de toda la empresa sin cuadrar hojas de cálculo.

## Historias de usuario y escenarios *(obligatorio)*

### Historia de usuario 1 - Pedir días de vacaciones (Prioridad: P1)

Luis quiere tomarse la semana del 9 al 13 de noviembre de 2026. Indica la fecha de inicio y la de fin, ve que la petición consume 5 días laborables y que le quedarían 7, y la envía. Marta recibe un aviso con las fechas y los días, y Luis no tiene que preguntar a nadie si el correo ha llegado.

**Por qué esta prioridad:** es el problema que motivó el encargo: las peticiones se pierden y nadie sabe cuántos días le quedan. Con solo esta historia, cada solicitud queda registrada con sus fechas y su saldo, aunque Marta la apruebe todavía de palabra.

**Prueba independiente:** Luis pide cinco días y se comprueba que la solicitud aparece como «pendiente», que el saldo previsto es el correcto y que Marta ha recibido el aviso. No hacen falta las historias 2 y 3.

**Criterios de aceptación:**

1. **Dado** que Luis tiene 12 días disponibles, **cuando** pide del lunes 9 al viernes 13 de noviembre de 2026 (5 días laborables), **entonces** la solicitud queda en estado «pendiente», Luis ve que le quedarían 7 días y Marta recibe un aviso con las fechas y los días.
2. **Dado** que Luis tiene 2 días disponibles, **cuando** pide 5, **entonces** el sistema rechaza la solicitud e indica que solo le quedan 2 días.
3. **Dado** que hoy es martes 20 de octubre de 2026, **cuando** Luis pide del 13 al 16 de octubre, **entonces** el sistema rechaza la solicitud e indica que la fecha de inicio ya ha pasado.
4. **Dado** que hoy es martes 20 de octubre de 2026, **cuando** Luis pide a partir del jueves 22, **entonces** el sistema rechaza la solicitud e indica que la primera fecha de inicio posible es el martes 27 de octubre (el quinto día laborable después del envío).

### Historia de usuario 2 - Aprobar o rechazar una solicitud (Prioridad: P2)

Marta abre su lista de solicitudes pendientes, ve la de Luis con las fechas, los días que consume y quién más de su equipo estará fuera esos días, y decide. Si aprueba, los días se descuentan y Jorge lo sabe sin que nadie le escriba; si rechaza, tiene que dar un motivo, y Luis lo recibe junto con la decisión.

**Por qué esta prioridad:** sin esto el proceso funciona a medias: las solicitudes quedan registradas, pero la respuesta sigue llegando por el pasillo y Jorge sigue enterándose por copia. Es la segunda mejora, no la primera.

**Prueba independiente:** se parte de una solicitud pendiente (aunque se haya creado a mano), Marta la aprueba y se comprueba que cambia de estado, que el saldo baja y que Luis y Jorge reciben la decisión; después rechaza otra y se comprueba que no puede hacerlo sin motivo.

**Criterios de aceptación:**

1. **Dado** que Marta tiene en su lista de pendientes la solicitud de Luis del 9 al 13 de noviembre, **cuando** la aprueba, **entonces** la solicitud pasa a «aprobada» con la fecha de la decisión, el saldo de Luis queda en 7 días disponibles, Luis recibe la respuesta y la solicitud queda registrada para Jorge.
2. **Dado** que Marta rechaza esa solicitud con el motivo «ya hay dos personas del equipo fuera esa semana», **cuando** confirma, **entonces** la solicitud pasa a «rechazada», Luis recibe la respuesta con el motivo y sus 12 días vuelven a estar disponibles.
3. **Dado** que Marta intenta rechazar la solicitud sin escribir un motivo, **cuando** confirma, **entonces** el sistema se lo impide y le pide el motivo.
4. **Dado** que Carmen, del equipo de Luis, ya tiene aprobadas esas mismas fechas, **cuando** Marta abre la solicitud de Luis, **entonces** ve el aviso de que Carmen estará fuera del 9 al 13 de noviembre y puede aprobar o rechazar igualmente.

### Historia de usuario 3 - Ver el saldo y las solicitudes (Prioridad: P3)

Luis quiere saber cuántos días le quedan y en qué estado está lo que ha pedido sin buscar entre correos: ve su saldo (totales, consumidos, pendientes de decidir y disponibles) y sus solicitudes con su estado, y si le cambian los planes cancela una aprobada antes de que empiece y recupera los días. Jorge ve las solicitudes aprobadas de toda la empresa y el saldo de cada persona, que es lo que hoy cuadra a mano en su hoja de cálculo.

**Por qué esta prioridad:** da visibilidad y elimina la hoja de cálculo de Jorge, pero el proceso ya funciona sin ello: Luis ve su saldo al pedir (historia 1) y Jorge recibe cada aprobación (historia 2).

**Prueba independiente:** con varias solicitudes de distintas personas y en distintos estados, se comprueba que Luis ve solo las suyas con el saldo correcto, que puede cancelar una aprobada y que Jorge ve las aprobadas de toda la empresa.

**Criterios de aceptación:**

1. **Dado** que Luis tiene 22 días de vacaciones en 2026, ya disfrutó 10 en agosto, tiene aprobada la semana del 9 al 13 de noviembre y pendientes el 21 y el 22 de diciembre, **cuando** consulta su saldo, **entonces** ve 22 días totales, 15 consumidos, 2 pendientes de decidir y 5 disponibles, y sus solicitudes con su estado.
2. **Dado** que Luis tiene aprobada la semana del 9 al 13 de noviembre, **cuando** la cancela el lunes 2 de noviembre, **entonces** la solicitud pasa a «cancelada», sus 5 días vuelven al saldo y Marta y Jorge reciben el aviso.
3. **Dado** que Jorge tiene rol de RRHH, **cuando** consulta el mes de noviembre, **entonces** ve todas las solicitudes aprobadas de la empresa con persona, equipo, fechas y días, y el saldo de cada persona.
4. **Dado** que Luis no tiene rol de RRHH, **cuando** consulta las solicitudes, **entonces** ve solo las suyas y no las del resto de la empresa.

### Casos límite

- ¿Qué pasa si Luis pide más días de los que tiene? → Se rechaza en el momento y se le indica cuántos le quedan (RF-004). Los días de solicitudes pendientes de decidir ya no cuentan como disponibles, así que no puede pedir dos veces el mismo saldo.
- ¿Qué pasa si las fechas se solapan con vacaciones ya aprobadas de otra persona del mismo equipo? → La solicitud se admite, pero Luis ve al pedir quién de su equipo estará fuera esas fechas y Marta ve el mismo aviso al decidir (RF-007). Bloquearla sería decidir por Marta.
- ¿Qué pasa si la fecha de inicio ya ha pasado? → Se rechaza y se indica que la fecha ya ha pasado (RF-005). Si la fecha de fin es anterior a la de inicio, se rechaza igualmente y se indica que el fin no puede ser anterior al inicio.
- ¿Qué pasa si las fechas incluyen un festivo o un fin de semana? → No consumen días (RF-002): del lunes 7 al viernes 11 de diciembre de 2026 salen 4 días, porque el martes 8 es festivo; un fin de semana suelto consume 0 días.
- ¿Qué pasa si la manager está de vacaciones y no puede aprobar? → **Dado** que Marta tiene vacaciones aprobadas del 16 al 20 de noviembre (lo sabe el propio sistema, por su solicitud) y ha dejado como sustituto a Pablo, otro manager del departamento, **cuando** Luis envía una solicitud el martes 17, **entonces** la solicitud llega a Pablo, que decide como lo haría Marta (RF-014). Si Marta no hubiera dejado a nadie, llegaría a Jorge.
- ¿Qué pasa si una solicitud cruza el cambio de año? → Cada día se descuenta del saldo del año en que cae (RF-011): del 28 al 31 de diciembre de 2026 salen del saldo de 2026, y del 4 al 8 de enero de 2027 (el 1 y el 6 son festivos) del de 2027. Por eso Jorge carga el saldo del año siguiente antes del 1 de diciembre (ver Supuestos).
- ¿Qué pasa si Luis quiere cancelar una solicitud ya aprobada? → Puede hasta el día anterior al inicio: la solicitud pasa a «cancelada», los días vuelven a su saldo y Marta y Jorge reciben el aviso (RF-012). Una vez empezadas las vacaciones, lo gestiona RRHH fuera del sistema (ver Fuera de alcance).
- ¿Qué pasa si una persona no tiene manager asignado? → No debería ocurrir: es un supuesto, porque Jorge asigna manager a cada persona al cargar su saldo. Si ocurre, la solicitud llega a Jorge como sustituto por defecto, igual que cuando Marta está fuera sin dejar a nadie (RF-014), y Jorge corrige la asignación.

## Aclaraciones

### Sesión 2026-10-20

Dudas que surgieron al escribir el borrador y respuestas de Jorge (RRHH), que es quien conoce la política de vacaciones:

- P: ¿Los días se cuentan en laborables o en naturales? → R: En laborables: no cuentan sábados, domingos ni festivos del calendario de la empresa.
- P: ¿Quién aprueba si la manager está de vacaciones? → R: La persona que la manager haya dejado como sustituta antes de irse; si no ha dejado a nadie, RRHH.
- P: ¿Se puede cancelar una solicitud ya aprobada y se devuelven los días? → R: Sí, hasta el día anterior al inicio, y los días vuelven al saldo; una vez empezada, lo gestiona RRHH fuera del sistema.
- P: ¿Hay una antelación mínima para pedir? → R: Sí: 5 días laborables. Las vacaciones pueden empezar, como pronto, el quinto día laborable después del envío.
- P: ¿Los días que no se gastan pasan al año siguiente? → R: No de forma automática: el saldo de cada año lo carga RRHH y, si decide arrastrar días a alguien, los suma a mano en el saldo nuevo.

Cambios aplicados en el texto a raíz de la sesión (una respuesta que no cambia nada no era una duda):

- Respuesta 1: nuevo RF-002; «días laborables» en RF-003, en el criterio 1 de la historia 1, en el caso límite del festivo y en la entidad Solicitud.
- Respuesta 2: nuevo RF-014, caso límite «la manager está de vacaciones» y persona sustituta en la entidad Persona.
- Respuesta 3: nuevo RF-012, criterio 2 de la historia 3, caso límite «cancelar una aprobada», estado «cancelada» en Solicitud y una línea en Fuera de alcance.
- Respuesta 4: nuevo RF-006 y criterio 4 de la historia 1.
- Respuesta 5: Supuestos (RRHH carga el saldo cada año), Fuera de alcance (arrastre automático) y caso límite «cruce de año».

### Dudas pendientes

- Ninguna: las cinco dudas del paso 7 se respondieron en la sesión y el texto ya refleja cada respuesta. Si al revisar aparece otra, apúntala aquí y márcala junto al requisito afectado como explica el paso 7 del ejercicio.

## Requisitos *(obligatorio)*

### Requisitos funcionales

Redactados en EARS (*Easy Approach to Requirements Syntax*), una forma sencilla y estructurada de redactar requisitos: cada uno es una sola frase comprobable con el verbo «deberá». Son catorce, más de los seis que pide el ejercicio, porque cada respuesta de la sesión de aclaraciones añadió uno; con seis bien escritos el ejercicio está cumplido.

- **RF-001**: El sistema deberá mostrar a cada persona su saldo de días de vacaciones del año en curso: días totales, consumidos, pendientes de decidir y disponibles.
- **RF-002**: El sistema deberá contar los días de cada solicitud en días laborables, sin sábados, domingos ni festivos del calendario de la empresa.
- **RF-003**: CUANDO una persona envía una solicitud, el sistema deberá registrarla en estado «pendiente» y avisar a su manager con las fechas y los días laborables que consume.
- **RF-004**: SI una persona pide más días de los que tiene disponibles, ENTONCES el sistema deberá rechazar la solicitud e indicar cuántos días le quedan.
- **RF-005**: SI la fecha de inicio es anterior a hoy, ENTONCES el sistema deberá rechazar la solicitud e indicar que esa fecha ya ha pasado.
- **RF-006**: SI la fecha de inicio es anterior al quinto día laborable posterior al envío, ENTONCES el sistema deberá rechazar la solicitud e indicar la primera fecha de inicio posible.
- **RF-007**: SI las fechas pedidas coinciden con vacaciones ya aprobadas de otra persona del mismo equipo, ENTONCES el sistema deberá avisar de quién estará fuera y en qué fechas, a la persona solicitante y a su manager, sin impedir la solicitud.
- **RF-008**: MIENTRAS una solicitud esté pendiente de respuesta, el sistema deberá mostrarla en la lista de pendientes de su manager.
- **RF-009**: CUANDO la manager aprueba o rechaza una solicitud, el sistema deberá registrar la decisión, con quién la tomó y cuándo, y comunicársela a la persona solicitante junto con el motivo si es un rechazo.
- **RF-010**: SI la manager intenta rechazar una solicitud sin indicar un motivo, ENTONCES el sistema deberá impedirlo y pedir el motivo.
- **RF-011**: CUANDO una solicitud queda aprobada, el sistema deberá descontar cada día del saldo del año al que pertenece y dejar la solicitud registrada para RRHH.
- **RF-012**: CUANDO la persona solicitante cancela una solicitud aprobada antes de su fecha de inicio, el sistema deberá marcarla como «cancelada», devolver sus días al saldo y avisar a su manager y a RRHH.
- **RF-013**: DONDE la persona tenga rol de RRHH, el sistema deberá permitir ver las solicitudes aprobadas de toda la empresa y el saldo de cada persona.
- **RF-014**: MIENTRAS la manager esté de vacaciones, CUANDO llegue una solicitud de su equipo, el sistema deberá enviarla a la persona que la sustituye.

Un apunte sobre la regla «un requisito, una sola cosa»: RF-003, RF-009, RF-011 y RF-012 tienen dos o tres efectos (registrar y avisar) para un mismo suceso; van juntos porque ocurren siempre a la vez y se comprueban en un solo criterio, igual que en la [especificación de ReservaSalas](../03-reserva-salas/spec.md). Dónde se comprueba cada uno: RF-001 a RF-006 en los criterios de la historia 1; RF-007 a RF-011 en los de la historia 2; RF-012 y RF-013 en los de la historia 3; RF-014 en el caso límite de la manager de vacaciones.

| Patrón EARS | Requisitos |
|---|---|
| Ubicuo («El sistema deberá…») | RF-001, RF-002 |
| Por evento (CUANDO…) | RF-003, RF-009, RF-011, RF-012 |
| Por estado (MIENTRAS…) | RF-008 |
| Comportamiento no deseado (SI…, ENTONCES…) | RF-004, RF-005, RF-006, RF-007, RF-010 |
| Opcional (DONDE…) | RF-013 |
| Complejo (MIENTRAS…, CUANDO…) | RF-014 |

### Entidades clave

- **Solicitud**: persona solicitante, fecha de inicio, fecha de fin, días laborables que consume, estado (pendiente, aprobada, rechazada o cancelada), motivo de rechazo (obligatorio solo al rechazar), quién decidió y cuándo.
- **Persona**: nombre, correo corporativo, equipo, manager, rol (empleado, manager o RRHH; con cualquier rol se pueden pedir vacaciones) y, opcionalmente, la persona sustituta a la que llegan las solicitudes de su equipo mientras está de vacaciones.
- **Saldo**: persona, año, días totales, días consumidos y días pendientes de decidir; los días disponibles son los totales menos los consumidos y los pendientes.

## Criterios de éxito *(obligatorio)*

### Resultados medibles

- **CE-001**: Pedir vacaciones, desde que se abre la solicitud hasta que se envía, lleva menos de 2 minutos.
- **CE-002**: El 100 % de las solicitudes aprobadas quedan registradas para RRHH sin que nadie las copie a mano.
- **CE-003**: Cero solicitudes aprobadas con saldo negativo en todo el año.

Cómo se medirán: CE-001 cronometrando a 10 personas de distintos equipos la primera vez que piden; CE-002 y CE-003 comparando al final de cada mes el registro de Jorge con las solicitudes aprobadas y el saldo de cada persona.

## Supuestos

- Todas las personas tienen manager asignado, y Jorge lo revisa cada vez que carga un saldo.
- RRHH carga el saldo de días de cada persona antes de que empiece cada año (antes del 1 de diciembre del anterior, para las solicitudes que cruzan el año) e incluye en él los días que decida arrastrar.
- Hay un único calendario de festivos para toda la empresa, que mantiene RRHH.
- Todas las personas tienen correo corporativo, por el que reciben los avisos.
- Las solicitudes de cada persona solo las ven ella, su manager (o quien la sustituya) y RRHH. El aviso de solapamiento de RF-007 muestra solo el nombre y las fechas de quien estará fuera: ni su saldo ni el resto de sus solicitudes.
- El volumen es pequeño: unas 200 personas y unas pocas solicitudes al día.

## Fuera de alcance

- Bajas médicas, permisos retribuidos y cualquier ausencia que no sean vacaciones.
- Nómina: ni el pago de días no disfrutados ni ningún cálculo económico.
- Festivos distintos por sede: hay un único calendario para toda la empresa.
- Arrastre automático de días al año siguiente (lo hace RRHH a mano al cargar el saldo).
- Cancelar o modificar una solicitud una vez empezadas las vacaciones.

## Revisión con la lista de verificación

Pasada el 2026-10-20 con la [plantilla de lista de verificación](../../plantillas/lista-de-verificacion.md), como pide el paso 8 del ejercicio: cumple CHK001 a CHK019. Tres notas para quien la repita:

- CHK010 y CHK012 se adaptaron a vacaciones: los casos límite que se buscan son «más días de los disponibles, solapamiento con el equipo y fecha pasada», y los supuestos «todas las personas tienen manager y RRHH carga el saldo cada año».
- CHK019 habla de la constitución, que aquí no existe; se usó para comprobar tres cosas y se marcó porque las tres se cumplen: ningún requisito contradice a otro (por ejemplo, RF-007 avisa del solapamiento pero no impide la solicitud que RF-003 registra); las entidades solo guardan los datos imprescindibles de cada persona; y las ausencias ajenas solo las ve quien las necesita: la manager (o quien la sustituya) y RRHH, enteras, y la persona solicitante, solo el nombre y las fechas del aviso de RF-007 (ver Supuestos).
- La categoría propia (CHK020 a CHK022) se cambió por tres preguntas sobre vacaciones: ¿está dicho qué ve Luis cuando se rechaza (RF-009)?, ¿está dicho qué pasa con el saldo al cancelar (RF-012)?, ¿está dicho quién decide si Marta no está (RF-014)? Las tres cumplen.

## En tres frases

1. La especificación de «Solicitud de vacaciones» dice qué quieren Luis, Marta y Jorge y por qué, sin una palabra de tecnología: tres historias priorizadas con criterios Dado / Cuando / Entonces, ocho casos límite, catorce requisitos EARS, tres criterios de éxito con cifra y cinco aclaraciones que han cambiado el texto.
2. Cada decisión discutible (laborables, avisar sin bloquear, antelación mínima, sin arrastre automático) está escrita, para que se pueda discutir y cambiar sin adivinar.
3. Pasa los puntos CHK001 a CHK019 de la lista de verificación; si la tuya también los pasa, está lista aunque no se parezca a esta.

## Siguiente paso

Vuelve al [ejercicio 01](../../01-tu-primera-especificacion-sin-codigo.md) para comparar tu especificación con esta, sección por sección, y continúa con el [Ejercicio 02: practicar requisitos EARS](../../02-practicar-requisitos-ears.md).

---

⬅️ [Ejercicio 01](../../01-tu-primera-especificacion-sin-codigo.md) · 🏠 [Índice de soluciones](../README.md)
