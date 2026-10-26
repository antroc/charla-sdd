# Respuestas comentadas del ejercicio 02

Este documento desarrolla la solución del [ejercicio 02](../../02-practicar-requisitos-ears.md). La [portada de la solución](README.md) contiene el mínimo esperado y los criterios de corrección; aquí se muestran respuestas posibles y el razonamiento.

## Bloque A

### F01 · Mostrar salas

**Frase original:** «La app tiene que enseñar las salas.»

**Respuesta posible:** El sistema deberá mostrar la lista de salas con su planta y aforo.

**Patrón:** ubicuo.

La frase deja de hablar de una «app» y concreta qué datos hacen falta para elegir una sala. También sería válido usar un patrón por evento si el requisito dijera cuándo se muestra la lista, siempre que ese disparador sea una decisión real y no un detalle inventado.

### F02 · Avisar al pedir vacaciones

**Respuesta posible:** CUANDO una persona envía una solicitud de vacaciones, el sistema deberá registrarla como pendiente y avisar a su manager con las fechas solicitadas.

**Patrón:** por evento.

«Que se entere» no se puede probar. «Recibir un aviso con las fechas» sí.

### F03 · Cafetera sin agua

**Respuesta posible:** SI se solicita un café con el depósito de agua vacío, ENTONCES la cafetera deberá impedir la preparación e indicar que falta agua.

**Patrón:** comportamiento no deseado.

También puede defenderse un requisito por estado: «MIENTRAS el depósito esté vacío…». La diferencia es si quieres describir el intento concreto o la regla que se mantiene durante todo el estado.

### F04 · Torno y tarjeta

**Respuesta posible:** CUANDO una persona presenta una tarjeta válida, el torno deberá desbloquearse durante `[NECESITA ACLARACIÓN: ¿cuántos segundos?]`.

**Patrón:** por evento.

No se inventa la duración ni qué significa «válida». Esos datos se preguntan a Seguridad o se anotan como supuestos provisionales.

## Bloque B

### F05 · Sala en mantenimiento

**Respuesta posible:** MIENTRAS una sala esté marcada en mantenimiento, el sistema deberá impedir nuevas reservas en ella.

**Patrón:** por estado.

El mantenimiento dura un tiempo; no es solo un evento puntual.

### F06 · Permiso de RRHH

**Respuesta posible:** DONDE la persona tenga rol de RRHH, el sistema deberá permitir consultar las solicitudes aprobadas de toda la empresa.

**Patrón:** opcional.

La regla solo se aplica a un perfil. El sujeto sigue siendo el sistema.

### F07 · Cafetera calentando

**Respuesta posible:** MIENTRAS la cafetera esté calentando el agua, la cafetera deberá mantener visible el indicador «Calentando».

**Patrón:** por estado.

«Que se vea» se sustituye por una respuesta observable.

### F08 · Reserva solapada

**Respuesta posible:** SI la franja solicitada se solapa con otra reserva de la misma sala, ENTONCES el sistema deberá rechazar la reserva e indicar qué franja está ocupada.

**Patrón:** comportamiento no deseado.

Avisar sin bloquear no evita el problema. Si quien encarga el sistema quisiera permitir el solapamiento, la respuesta cambiaría, pero la decisión tendría que quedar escrita.

## Bloque C

### F09 · Reservas «razonables»

**Respuesta posible A:** SI una reserva dura más de 4 horas, ENTONCES el sistema deberá rechazarla e indicar el máximo permitido.

**Respuesta posible B:** SI una reserva queda fuera del horario de 08:00 a 20:00, ENTONCES el sistema deberá rechazarla e indicar el horario permitido.

Son dos reglas diferentes. Pueden reunirse en un requisito si la respuesta es exactamente la misma y la trazabilidad sigue siendo clara.

### F10 · Más días de los disponibles

**Respuesta posible:** SI una persona solicita más días de los que tiene disponibles, ENTONCES el sistema deberá rechazar la solicitud e indicar su saldo actual.

«Decirlo claramente» se concreta mostrando el dato que explica el rechazo.

### F11 · Acceso fuera de horario

**Respuesta posible:** MIENTRAS el edificio esté fuera del horario de apertura, CUANDO una persona presenta su tarjeta, el torno deberá desbloquearse solo si la tarjeta pertenece al personal de seguridad.

**Patrón:** complejo.

Falta aclarar el horario exacto y qué ocurre en fines de semana y festivos.

### F12 · Limpieza de la cafetera

La frase contiene dos asuntos:

- «fácil de limpiar» debe convertirse en un criterio medible, por ejemplo: «La limpieza completa lleva menos de `[NECESITA ACLARACIÓN: minutos]`»;
- «avise cuando toque» puede expresarse así: CUANDO la cafetera alcance `[NECESITA ACLARACIÓN: número de cafés o días]` desde la última limpieza, la cafetera deberá mostrar un aviso de limpieza.

## Clasificación R1-R4

| Requisito | Patrón | Motivo |
|---|---|---|
| R1 | Por evento | Empieza por CUANDO y describe una cancelación puntual |
| R2 | Ubicuo | No depende de evento, estado, error ni perfil |
| R3 | Opcional | Solo se aplica donde está activado el registro de visitas |
| R4 | Complejo | Combina un estado pendiente con el evento de cambiar fechas |

## Caza el error

### E1 · Tecnología dentro del requisito

**Fallo:** menciona una tabla y PostgreSQL.

**Corrección:** CUANDO una persona confirma una reserva, el sistema deberá guardarla y mostrar una confirmación con sala, fecha y hora.

La tecnología se decide en el plan técnico.

### E2 · Dos capacidades independientes

**Fallo:** reúne reservar salas y gestionar el mantenimiento.

**Corrección:** separar un requisito de reserva y otro, condicionado por permisos, para marcar mantenimiento.

### E3 · Adjetivos sin medida

**Fallo:** «rápido» y «fácil de usar» no se pueden comprobar.

**Corrección:** mantener como requisito el comportamiento de mostrar disponibilidad y crear criterios de éxito con cifras, por ejemplo tiempo de respuesta y porcentaje de personas que completan la reserva sin ayuda.

### E4 · Falta la condición

**Fallo:** «El sistema deberá rechazar la solicitud» obligaría a rechazar todas las solicitudes.

**Corrección:** SI una persona solicita más días de los disponibles, ENTONCES el sistema deberá rechazar la solicitud e indicar el saldo.

## Supuestos y aclaraciones

| Caso | Decisión correcta |
|---|---|
| Duración de apertura del torno | Preguntar o anotar un supuesto visible |
| Definición de tarjeta válida | Aclarar con Seguridad |
| Horario fuera de apertura | Preguntar por laborables, fines de semana y festivos |
| Frecuencia de limpieza | Dejar un marcador de aclaración |
| Tiempo considerado «fácil de limpiar» | Convertirlo en criterio medible y pedir la cifra |

## Conclusión

Las respuestas no tienen que coincidir palabra por palabra. Deben conservar la regla de negocio, elegir un patrón defendible y producir una respuesta observable. Cuando falte un dato, se pregunta o se anota como supuesto; no se inventa a escondidas.

---

⬅️ [Portada de la solución](README.md) · 🏠 [Índice de soluciones](../README.md)
