# Plantilla: especificación

> [!TIP]
> Copia este fichero, renómbralo `spec.md` (en Spec Kit vive en `specs/001-nombre-corto/spec.md`), rellena los corchetes y borra este aviso; el título pasa a ser `# Especificación: <nombre de la funcionalidad>`.
>
> Con Spec Kit, `/speckit.specify` genera su equivalente a partir de tu descripción en lenguaje natural. Usa esta plantilla para trabajar sin herramientas o para revisar lo que el asistente de IA haya generado.
>
> Regla de oro: aquí se escribe QUÉ queremos y POR QUÉ. Nada de tecnología: si aparece «base de datos», «API» (la conexión entre dos programas) o el nombre de un lenguaje de programación, eso va al plan técnico.

<!--
  Qué es: el contrato entre quien pide el software y quien lo construye. Es la fuente de verdad: si el código no hace lo que dice aquí, se corrige el código (o se corrige esto y se regenera).
  Para quién: la escribe quien pide (negocio, RRHH, un manager) con ayuda de quien construye; la lee todo el mundo, incluido el asistente de IA.
  Consejo: escríbela para la persona menos técnica del equipo. Si ella la entiende, el asistente también.
-->

**Carpeta/rama:** `[001-reserva-salas]` · **Creada:** [AAAA-MM-DD] · **Estado:** Borrador · **Petición original:** «[Queremos una pequeña aplicación interna para reservar las salas de reuniones y dejar de usar la hoja de cálculo compartida.]»

## Resumen
<!-- Qué se escribe: el problema de hoy y lo que queremos conseguir, en 3-5 frases y sin tecnología. Para quién: cualquiera que abra el fichero por primera vez. Consejo: si no puedes explicar el problema sin decir «la app», todavía no sabes cuál es el problema. (Sección nuestra; en Spec Kit el resumen va en la petición original.) -->

[Hoy las 12 salas, repartidas en 3 plantas, se reservan apuntándose en una hoja de cálculo. Hay choques (dos equipos en la misma sala), salas reservadas que se quedan vacías y reservas «fantasma» de las que nadie sabe el dueño. Queremos que cualquier empleado vea qué salas están libres, reserve una en menos de un minuto y que toda reserva tenga un responsable visible.]

## Historias de usuario y escenarios *(obligatorio)*
<!-- Qué se escribe: lo que cada tipo de persona quiere conseguir, ordenado por importancia: P1 es lo imprescindible, P2 y P3 lo que viene después. Para quién: las escribe quien pide el software; las revisa quien lo construye. Consejo: cada historia tiene que poder construirse y probarse *sola*. Si solo hiciéramos la P1, ¿ya serviría para algo? Si no, no es una P1. -->

### Historia de usuario 1 - [Reservar una sala] (Prioridad: P1)
<!-- Describe el recorrido en lenguaje llano: quién es la persona, qué hace, qué consigue. Nada de pantallas ni botones. -->

[Marta, manager de un equipo, quiere ver qué salas están libres el jueves de 10:00 a 11:00, elegir una y confirmar la reserva sin preguntar a nadie.]

**Por qué esta prioridad:** [Sin esto no hay producto: es el problema que motivó el encargo.]

**Prueba independiente:** [Se puede probar por sí sola: entrar, elegir la franja, reservar la sala Mediterráneo y comprobar que aparece ocupada.]

**Criterios de aceptación:**
<!-- Formato Dado / Cuando / Entonces. Cada criterio es una situación concreta que alguien puede comprobar con un sí o un no. Al menos un caso que sale bien y otro que sale mal. -->

1. **Dado** [que la sala Mediterráneo está libre el jueves de 10:00 a 11:00], **cuando** [Marta la selecciona y confirma], **entonces** [la reserva queda guardada y ve un mensaje con sala, fecha y hora].
2. **Dado** [que la sala Cantábrico ya está reservada de 10:00 a 11:00], **cuando** [Marta intenta reservarla en esa franja], **entonces** [el sistema rechaza la reserva y le indica qué franja está ocupada].

### Historia de usuario 2 - [Cancelar o modificar mi reserva] (Prioridad: P2)
<!-- Misma estructura. Pregúntate si esta historia puede probarse sin que exista la P3. -->

[Luis ya no necesita la sala que reservó para el viernes y quiere cancelarla (o cambiarla de hora) para que otro equipo pueda usarla.]

**Por qué esta prioridad:** [Sin esto, las reservas que ya no hacen falta siguen bloqueando salas: el problema de las salas vacías.]

**Prueba independiente:** [...]

**Criterios de aceptación:**

1. **Dado** [que Luis tiene una reserva el viernes], **cuando** [la cancela], **entonces** [la sala vuelve a aparecer libre en esa franja].
2. **Dado** [que Luis intenta cancelar una reserva de Marta], **cuando** [confirma la cancelación], **entonces** [el sistema se lo impide e indica que solo la persona responsable o administración pueden hacerlo].

### Historia de usuario 3 - [Ver mis reservas y las de hoy en cada sala] (Prioridad: P3)
<!-- Misma estructura que las anteriores: recorrido, por qué, prueba independiente y criterios. Las historias P3 son las primeras que se recortan si falta tiempo; que no duela dejarlas fuera. -->

[...]

**Por qué esta prioridad:** [...]

**Prueba independiente:** [...]

**Criterios de aceptación:**

1. **Dado** [...], **cuando** [...], **entonces** [...].

### Casos límite
<!-- Qué se escribe: las situaciones raras o incómodas, como preguntas «¿qué pasa si…?»; son las que más errores producen cuando nadie las piensa. Un caso por línea. Para quién: las propone quien conoce los casos reales (negocio) y las completa quien construye. Consejo: piensa en extremos: cero, demasiado, al mismo tiempo, fuera de horario, sin permisos. -->

- [¿Qué pasa si la franja pedida se solapa solo en parte con otra (10:00-11:00 frente a 10:30-11:30)?]
- [¿Qué pasa si alguien pide una reserva fuera del horario de oficina (08:00-20:00)?]
- [¿Qué pasa si la sala está en mantenimiento?]
- [¿Qué pasa con una reserva de más de 4 horas?]
- [¿Qué pasa si alguien quiere una sala «para ya mismo» y está ocupada?]
- [¿Qué pasa si dos personas intentan reservar la misma sala en la misma franja a la vez?]

## Aclaraciones
<!-- Qué se escribe: las preguntas que surgieron al revisar y la respuesta decidida; con Spec Kit, /speckit.clarify añade esta sección por su cuenta justo después de las historias de usuario (por eso va aquí), y el registro completo con fecha e impacto va en lista-de-aclaraciones.md. Para quién: responde quien encarga el proyecto; cada respuesta tiene que reflejarse también en la sección afectada (requisito, historia o caso límite). Consejo: ninguna especificación pasa al plan con dudas pendientes de alcance o de datos. -->

### Sesión [AAAA-MM-DD]
<!-- Una línea por pregunta respondida, en este formato. -->

- P: [¿Se pueden hacer reservas recurrentes?] → R: [No en la primera versión.]
- P: [¿Quién puede cancelar una reserva ajena?] → R: [Solo administración.]
- P: [¿Hay que avisar por correo?] → R: [Sí, un correo de confirmación.]
- P: [¿Qué pasa si nadie aparece en la sala reservada?] → R: [Fuera de alcance: no se controla la asistencia.]

### Dudas pendientes
<!-- Lo que todavía nadie ha respondido. Mientras estén aquí, aparecen en el texto como [NECESITA ACLARACIÓN: …]. -->

- [¿Con cuánta antelación como máximo se puede reservar?] → afecta a [RF-006 y casos límite].

## Requisitos *(obligatorio)*
<!--
  Qué se escribe: la lista numerada de cosas que el sistema tiene que hacer: una por frase, cada una comprobable.
  Para quién: las escribe negocio con ayuda de quien construye; son el contrato que luego se convierte en pruebas.
  Consejo: usa EARS (*Easy Approach to Requirements Syntax*), «una forma sencilla y estructurada de redactar requisitos». Cinco plantillas de frase:
    1. Ubicuo (siempre se cumple):        «El sistema deberá [respuesta].»
    2. Por evento (algo ocurre):          «CUANDO [disparador], el sistema deberá [respuesta].»
    3. Por estado (dura un tiempo):       «MIENTRAS [estado], el sistema deberá [respuesta].»
    4. Comportamiento no deseado:         «SI [condición], ENTONCES el sistema deberá [respuesta].»
    5. Opcional (solo en algunos casos):  «DONDE [característica o perfil], el sistema deberá [respuesta].»
  Se pueden combinar («MIENTRAS…, CUANDO…, el sistema deberá…»). Palabras clave en mayúsculas y siempre el verbo «deberá».
-->

### Requisitos funcionales
<!-- Un requisito = una frase = una cosa comprobable. Sin adjetivos vagos («rápido», «intuitivo») y sin tecnología. Numera RF-001, RF-002… Lo que no sepas, márcalo [NECESITA ACLARACIÓN: pregunta concreta] (máximo 3). -->

*Recuerda las cinco plantillas EARS (*Easy Approach to Requirements Syntax*, una forma sencilla y estructurada de redactar requisitos): «El sistema deberá…» · «CUANDO…, el sistema deberá…» · «MIENTRAS…, el sistema deberá…» · «SI…, ENTONCES el sistema deberá…» · «DONDE…, el sistema deberá…».*

- **RF-001**: El sistema deberá [mostrar la lista de salas con su planta y aforo].
- **RF-002**: El sistema deberá [...].
- **RF-003**: CUANDO [una persona confirma una reserva], el sistema deberá [guardarla y mostrar un mensaje de confirmación con sala, fecha y hora].
- **RF-004**: CUANDO [...], el sistema deberá [...].
- **RF-005**: SI [la franja solicitada se solapa con otra reserva de la misma sala], ENTONCES el sistema deberá [rechazar la reserva e indicar qué franja está ocupada].
- **RF-006**: SI [la franja solicitada queda fuera del horario de oficina (08:00-20:00) o dura más de 4 horas], ENTONCES el sistema deberá [rechazar la reserva e indicar qué límite se incumple] [NECESITA ACLARACIÓN: ¿con cuánta antelación como máximo se puede reservar?].
- **RF-007**: MIENTRAS [una sala esté marcada en mantenimiento], el sistema deberá [impedir nuevas reservas en ella].
- **RF-008**: MIENTRAS [...], el sistema deberá [...].
- **RF-009**: DONDE [la persona tenga permisos de administración], el sistema deberá [permitir marcar una sala en mantenimiento].
- **RF-010**: SI [una persona sin permisos de administración intenta cancelar una reserva ajena], ENTONCES el sistema deberá [rechazar la operación e indicar quién puede hacerlo].
- **RF-011**: CUANDO [se confirma una reserva], el sistema deberá [enviar un correo de confirmación a la persona responsable].

### Entidades clave
<!-- Las «cosas» de las que habla el sistema y qué datos tiene cada una, sin decidir cómo se guardan. Solo si la funcionalidad maneja datos. -->

- **Sala**: [nombre, planta, aforo, estado (disponible o en mantenimiento)].
- **Reserva**: [sala, persona responsable, inicio, fin, motivo opcional].
- **Persona**: [nombre, correo corporativo, rol (empleado o administración)].

## Criterios de éxito *(obligatorio)*
<!-- Qué se escribe: cómo sabremos que ha funcionado, con números y sin tecnología; se miran meses después para decidir si mereció la pena. Para quién: los fija negocio; son lo que un manager puede comprobar sin leer una línea de código. Consejo: tiempo, porcentaje, cantidad o tasa. «Que sea rápido» no es un criterio; «en menos de 2 segundos» sí. -->

### Resultados medibles
<!-- Numera CE-001, CE-002… Cada uno comprobable sin saber cómo está construido el sistema. -->

- **CE-001**: [Reservar una sala lleva menos de 1 minuto desde que se abre la aplicación.]
- **CE-002**: [Cero reservas solapadas en la misma sala.]
- **CE-003**: [El 90 % de las personas completan una reserva sin ayuda la primera vez.]
- **CE-004**: [El listado de disponibilidad se muestra en menos de 2 segundos.]

## Supuestos
<!-- Lo que damos por sentado porque nadie lo ha dicho pero es razonable. Escribirlo evita sorpresas: si alguien no está de acuerdo, lo verá aquí. -->

- [Todas las personas usuarias tienen correo corporativo.]
- [No hace falta integrarse con el calendario corporativo en la primera versión.]

## Fuera de alcance
<!-- Lo que *no* vamos a hacer, dicho en voz alta. Es la sección que más discusiones ahorra. (Sección nuestra; no está en la plantilla oficial de Spec Kit.) -->

- [Reservas recurrentes (todos los lunes a las 9).]
- [Control de asistencia: no se comprueba si alguien aparece.]

<!-- Volver al índice de plantillas: abre README.md en esta misma carpeta (ejercicios/plantillas/README.md). -->
