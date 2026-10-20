# Aclaraciones de ReservaSalas

> [!NOTE]
> Este fichero recoge la fase de **aclarar**, paso 2 del flujo SDD (*Spec-Driven Development*, desarrollo guiado por especificaciones): las preguntas que el asistente de IA hizo al leer la especificación y las respuestas de Ana. Se produce con `/speckit.clarify`. En Spec Kit no existe como fichero aparte: las respuestas se incorporan dentro de `spec.md`, en la sección «Aclaraciones (Clarifications)», y el asistente actualiza los requisitos afectados. Aquí lo mostramos por separado para que se vea el proceso.

## Cómo fue la sesión

Luis ejecutó `/speckit.clarify` el 2026-10-07 con la especificación recién generada. El asistente revisó la especificación buscando huecos (alcance, roles, datos, casos límite, avisos) y fue haciendo **una pregunta cada vez**, con una respuesta recomendada y opciones cortas. Ana respondió en una reunión de 15 minutos. Cinco preguntas es el máximo que hace Spec Kit por sesión.

## Preguntas y respuestas

| # | Pregunta del asistente | Respuesta de Ana | Impacto en la especificación |
|---|---|---|---|
| 1 | ¿Se pueden hacer reservas recurrentes (por ejemplo, todos los lunes de 09:00 a 10:00)? | No en la primera versión. | Añadido a «Fuera de alcance». No hace falta guardar en cada reserva ningún dato sobre repeticiones. |
| 2 | ¿Quién puede cancelar una reserva ajena? | Solo administración. | Nuevo RF-010 y criterios 4 y 5 de la historia 2. Se precisa qué puede hacer el rol de administración, que ya existía por RF-009. |
| 3 | ¿Hay que avisar por correo cuando se hace una reserva? | Sí: un correo al confirmar, al modificar y al cancelar, para que sirva de comprobante. | Nuevo RF-011 (correo a la persona responsable al confirmar, modificar o cancelar, con el tipo de cambio) y criterio de aceptación 7 de la historia 1. Nuevo supuesto: existe un servidor de correo corporativo. |
| 4 | ¿Con cuánta antelación máxima se puede reservar? | 30 días. | Límite añadido a RF-006 y nuevo caso límite «Antelación excesiva». |
| 5 | ¿Qué pasa si nadie aparece a la reserva? ¿Se libera la sala? | Fuera de alcance: no se controla la asistencia. | Añadido a «Fuera de alcance». Evita construir confirmaciones de llegada, sensores o liberación automática. |

## Lo que el asistente no preguntó (y por qué)

- **Horario de oficina y duración máxima:** ya venían en la descripción de Ana (08:00-20:00, máximo 4 horas).
- **Qué datos guardar de cada persona:** lo fija la constitución (principio 4, datos mínimos), así que no hacía falta preguntar.
- **Tecnología:** la fase de aclarar evita las preguntas de tecnología salvo que bloqueen el funcionamiento; eso se decide en el plan técnico.

## Cómo quedó en spec.md

El asistente añadió esta sección justo después de los escenarios de usuario y actualizó los requisitos indicados en la tabla:

```markdown
## Aclaraciones (Clarifications)

### Sesión 2026-10-07

- P: ¿Se pueden hacer reservas recurrentes (por ejemplo, todos los lunes)? → R: No en la primera versión.
- P: ¿Quién puede cancelar una reserva ajena? → R: Solo administración.
- P: ¿Hay que avisar por correo? → R: Sí: un correo al confirmar, al modificar y al cancelar, para que sirva de comprobante.
- P: ¿Con cuánta antelación máxima se puede reservar? → R: 30 días.
- P: ¿Qué pasa si nadie aparece a la reserva? → R: Fuera de alcance: no se controla la asistencia.
```

Después de incorporar las respuestas, el asistente volvió a pasar la lista de verificación de calidad (ver [checklist.md](checklist.md)): se pasó de 20 a 23 comprobaciones superadas, de un total de 23.

Sobre la numeración: los dos requisitos nuevos (RF-010, permisos, y RF-011, correo) se colocaron junto a los de las historias 1 y 2, y el requisito de la historia 3, que hasta entonces era el RF-010, pasó a ser el RF-012. Se renumeró antes de aprobar la especificación, cuando todavía no lo citaba ningún plan ni ninguna tarea. Una vez aprobada, los identificadores ya no cambian: si algo desaparece se marca como retirado y lo nuevo toma el siguiente número libre.

> [!TIP]
> Si al responder descubres algo que cambia el alcance, no lo apuntes en un correo: vuelve a ejecutar `/speckit.clarify` o edita la especificación. La especificación es la fuente de verdad; el plan y las tareas salen de ella.

---

⬅️ [Anterior: Especificación](spec.md) · 🏠 [Índice de la solución](README.md) · ➡️ [Siguiente: Lista de verificación](checklist.md)
