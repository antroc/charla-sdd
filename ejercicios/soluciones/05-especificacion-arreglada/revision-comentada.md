# Revisión comentada del ejercicio 05

Este documento amplía la [solución del ejercicio 05](README.md). El objetivo normal del ejercicio es encontrar doce problemas relevantes, no reproducir una auditoría exhaustiva.

## Doce problemas que bastan para resolver el ejercicio

| N.º | Zona | Problema | Por qué bloquea | Corrección |
|---|---|---|---|---|
| 1 | Cabecera | «Creada: el viernes» | No identifica una fecha estable | Usar `AAAA-MM-DD` |
| 2 | Estado | Figura «lista para implementar» con dudas abiertas | Se salta aclaración, aprobación y planificación | Mantener «Borrador» hasta cerrar las dudas |
| 3 | Resumen | Incluye React, Node.js, PostgreSQL y nube | Mezcla el qué con el cómo | Trasladar la tecnología al plan |
| 4 | Alcance | Añade parking y catering «para más adelante» | Introduce funciones no solicitadas | Llevarlas a «Fuera de alcance» |
| 5 | Historias | Estadísticas aparece antes que reservar | La prioridad no responde al problema principal | Hacer «Reservar una sala» la P1 |
| 6 | Historias | Describe un botón verde y su posición | Fija una interfaz dentro de la spec | Describir «confirmar la reserva» |
| 7 | Casos límite | Dice que no hay ninguno destacable | Deja abiertas reglas esenciales | Añadir solapamientos, horarios, mantenimiento y permisos |
| 8 | Requisitos | «Rápido, intuitivo y fácil» | No se puede comprobar | Convertirlo en criterios de éxito con cifras |
| 9 | Requisitos | Un requisito reúne reservar y gestionar usuarios | Son capacidades y perfiles distintos | Separar y eliminar lo que no está en alcance |
| 10 | Requisitos | «Avisar si hay choque» | No dice si bloquea ni qué muestra | Rechazar el solapamiento e indicar la franja ocupada |
| 11 | Constitución | Permite reservas anónimas | Contradice la responsabilidad visible | Mostrar la persona responsable de cada reserva |
| 12 | Criterios | «La gente estará más contenta» | No tiene cifra ni método de medida | Sustituirlo por un indicador observable |

Una respuesta diferente también es válida si cubre al menos dos problemas de alcance, dos de requisitos, dos de criterios, dos choques con la constitución y cuatro problemas adicionales que cambien lo que se construiría.

## Requisitos corregidos

Una posible versión de los requisitos funcionales es:

```markdown
### Requisitos funcionales

- **RF-001**: El sistema deberá mostrar la lista de salas con su planta y aforo.
- **RF-002**: CUANDO una persona indica una fecha y una franja horaria, el sistema deberá mostrar qué salas están libres.
- **RF-003**: CUANDO una persona confirma una reserva, el sistema deberá guardarla y mostrar una confirmación con sala, fecha y hora.
- **RF-004**: El sistema deberá mostrar junto a cada reserva el nombre de la persona responsable.
- **RF-005**: SI la franja solicitada se solapa con otra reserva de la misma sala, ENTONCES el sistema deberá rechazarla e indicar qué franja está ocupada.
- **RF-006**: SI la franja queda fuera del horario, dura más del máximo, termina en el pasado o supera la antelación permitida, ENTONCES el sistema deberá rechazarla e indicar qué límite se incumple.
- **RF-007**: MIENTRAS una sala esté en mantenimiento, el sistema deberá impedir nuevas reservas en ella.
- **RF-008**: CUANDO la persona responsable cancela o modifica una reserva, el sistema deberá aplicar el cambio y liberar la franja anterior.
- **RF-009**: DONDE la persona tenga permisos de administración, el sistema deberá permitir marcar una sala en mantenimiento.
- **RF-010**: SI una persona sin permisos intenta modificar una reserva ajena, ENTONCES el sistema deberá rechazar la operación.
- **RF-011**: CUANDO una reserva se confirma, modifica o cancela, el sistema deberá enviar un aviso a su responsable.
- **RF-012**: El sistema deberá permitir a cada persona consultar sus reservas futuras.
```

Los límites concretos —por ejemplo, 08:00-20:00, cuatro horas y treinta días— deben proceder de quien encarga el sistema. Si todavía no están confirmados, se señalan como aclaraciones o supuestos provisionales.

## Criterios de éxito corregidos

```markdown
### Resultados medibles

- **CE-001**: Completar una reserva lleva menos de 1 minuto.
- **CE-002**: Existen cero reservas activas solapadas para la misma sala.
- **CE-003**: Al menos el 90 % de las personas completa una reserva sin ayuda la primera vez.
- **CE-004**: La disponibilidad se muestra en menos de 2 segundos con el volumen previsto.
```

Las cifras son decisiones de negocio. Pueden ser otras, pero deben quedar justificadas y acompañadas de una forma de medida.

## Aclaraciones que faltaban

Una sesión razonable podría cerrar estas preguntas:

- ¿Quién puede marcar una sala en mantenimiento?
- ¿Quién puede modificar una reserva ajena?
- ¿Cuál es el horario permitido?
- ¿Cuál es la duración máxima?
- ¿Con cuánta antelación se puede reservar?
- ¿Son obligatorios los avisos?
- ¿Se permiten reservas recurrentes?

Cada respuesta debe modificar una historia, un requisito, un caso límite o el alcance. Guardar la respuesta sin cambiar el texto no resuelve la ambigüedad.

## Resto de la especificación

| Sección | Qué debe cambiar |
|---|---|
| Resumen | Explicar los problemas actuales sin tecnología |
| Historias | P1 reservar; P2 cancelar o modificar; P3 consultar reservas |
| Criterios de aceptación | Usar Dado/Cuando/Entonces con casos felices y errores |
| Casos límite | Solapamientos, mantenimiento, pasado, límites y permisos |
| Entidades | Guardar solo sala, reserva y datos mínimos de persona/rol |
| Supuestos | Acceso corporativo, correo existente y volumen previsto |
| Fuera de alcance | Recurrentes, asistencia, calendario, catering, parking y equipamiento |

## Lista de verificación

La revisión no termina cuando los requisitos quedan bien. La especificación completa debe comprobar:

- ausencia de tecnología en el comportamiento;
- prioridades y pruebas independientes;
- requisitos numerados y comprobables;
- criterios con cifras;
- aclaraciones resueltas;
- alcance explícito;
- coherencia con la constitución;
- trazabilidad entre historias y requisitos.

Si solo se han reescrito los requisitos y criterios, las casillas referentes a historias, casos límite o alcance deben quedar abiertas con una nota. No se marcan como correctas por intuición.

## Qué no es necesario hacer

No hace falta encontrar todas las erratas, discutir el estilo o coincidir con la numeración exacta de la solución. El ejercicio se considera resuelto cuando detectas los defectos que podrían provocar una aplicación distinta, insegura, contradictoria o imposible de comprobar.

---

⬅️ [Portada de la solución](README.md) · 🏠 [Índice de soluciones](../README.md)
