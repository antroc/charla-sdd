# Plantilla: lista de aclaraciones

> [!TIP]
> Copia este fichero junto a tu especificación, renómbralo `aclaraciones.md` y rellena los corchetes a medida que surjan preguntas y se respondan. Borra este aviso al terminar.
>
> Con Spec Kit no existe un fichero aparte: el comando `/speckit.clarify` hace hasta 5 preguntas, de una en una, y apunta las respuestas en la sección «Clarifications» de `spec.md`. Esta plantilla sirve para trabajar sin herramientas, para preparar las respuestas antes de la sesión con el asistente de IA o para revisar lo que este anote.
>
> Cada respuesta tiene que acabar reflejada en la especificación (requisito, historia o caso límite). Una aclaración que no cambia nada en la especificación no era una aclaración.

<!--
  Qué es este documento: el registro de las dudas que aparecen al leer la especificación y de las decisiones que las resuelven.
  Para quién: pregunta quien construye (o el asistente de IA); responde quien encarga el proyecto. Lo consulta cualquiera que quiera saber «¿por qué se decidió esto?».
  Consejo: preguntas que se respondan con una opción corta o con un sí/no. «¿Qué te parece el diseño?» no es una pregunta de aclaración.
-->

**Especificación:** [`specs/001-reserva-salas/spec.md`] · **Responde:** [Ana, responsable de Oficina] · **Pregunta:** [Luis, con el asistente de IA] · **Estado:** [4 de 5 respondidas]

## Preguntas y respuestas
<!--
  Qué se escribe: una fila por pregunta. La respuesta, corta y decidida. En «Impacto» di qué parte de la especificación cambia (qué requisito, historia o sección) o escribe «Fuera de alcance». Mientras una pregunta esté sin responder, deja la respuesta como «[...]» y «Pendiente» en la columna de quién y cuándo.
  Para quién: la tabla la rellena quien responde; la columna de impacto la completa quien luego edita la especificación.
  Consejo: máximo 5 preguntas por sesión, por orden de impacto e incertidumbre: primero alcance, roles y datos; después experiencia de uso; por último los detalles.
-->

| Nº | Pregunta | Respuesta | Quién y cuándo | Impacto en la especificación |
|---|---|---|---|---|
| 1 | [¿Se pueden hacer reservas recurrentes (por ejemplo, todos los lunes a las 9)?] | [No en la primera versión.] | [Ana, AAAA-MM-DD] | [Añadir a «Fuera de alcance».] |
| 2 | [¿Quién puede cancelar una reserva ajena?] | [Solo administración.] | [Ana, AAAA-MM-DD] | [Nuevo requisito RF-010 con el patrón EARS «SI…, ENTONCES…»; retocar la historia 2.] |
| 3 | [¿Hay que avisar por correo?] | [Sí, un correo de confirmación.] | [Ana, AAAA-MM-DD] | [Resolver el marcador de RF-011.] |
| 4 | [¿Con cuánta antelación como máximo se puede reservar?] | [...] | [Pendiente] | [Previsto: nuevo límite en RF-006 (patrón EARS «SI…, ENTONCES…») y un caso límite.] |
| 5 | [¿Qué pasa si nadie aparece en la sala reservada?] | [Fuera de alcance: no se controla la asistencia.] | [Ana, AAAA-MM-DD] | [Añadir a «Fuera de alcance».] |

## Dudas abiertas
<!--
  Qué se escribe: preguntas que todavía nadie ha respondido. Mientras estén aquí, en la especificación aparecen como [NECESITA ACLARACIÓN: pregunta concreta].
  Para quién: para quien encarga el proyecto, que es quien tiene que contestarlas antes de que se escriba el plan técnico.
  Consejo: si una duda es de tecnología («¿usamos una base de datos u otra?»), no va aquí: va al plan técnico.
-->

- [NECESITA ACLARACIÓN: ¿con cuánta antelación como máximo se puede reservar?] → afecta a [RF-006 y casos límite].
- [NECESITA ACLARACIÓN: …] → afecta a [...].

## Cambios aplicados a la especificación
<!--
  Qué se escribe: una casilla por cada edición que las respuestas obligan a hacer en spec.md. Se marca cuando el cambio está hecho.
  Para quién: para quien edita la especificación (sin herramientas, una persona; con Spec Kit, el asistente lo hace y tú lo compruebas).
  Consejo: no dejes la respuesta solo en esta tabla. Si no está en la especificación, para el asistente de IA no existe.
-->

- [x] [«Reservas recurrentes» añadido a «Fuera de alcance».]
- [x] [RF-010 redactado: «SI una persona sin permisos de administración intenta cancelar una reserva ajena, ENTONCES el sistema deberá rechazar la operación e indicar quién puede hacerlo.» Nuevo criterio de aceptación en la historia 2.]
- [x] [Marcador de RF-011 sustituido por la respuesta: «enviar un correo de confirmación a la persona responsable».]
- [x] [«Control de asistencia» añadido a «Fuera de alcance».]
- [ ] [...]

## Cómo lo anota Spec Kit
<!--
  Qué se escribe: nada que rellenar. Es el formato que el asistente añade a spec.md, para que lo reconozcas y lo revises.
  Para quién: para quien use Spec Kit y quiera comprobar que las respuestas quedaron bien registradas.
  Consejo: compara esta lista con la tabla de arriba; si falta una respuesta en spec.md, vuelve a pedírsela al asistente.
  Borra esta sección cuando el documento esté listo.
-->

Spec Kit escribe los títulos en inglés y cada respuesta en una línea; en el ejemplo resuelto de este repositorio los verás traducidos como «Aclaraciones», «Sesión» y «P: … → R: …».

```markdown
## Clarifications

### Session 2026-10-07

- Q: ¿Se pueden hacer reservas recurrentes? → A: No en la primera versión.
- Q: ¿Quién puede cancelar una reserva ajena? → A: Solo administración.
- Q: ¿Hay que avisar por correo? → A: Sí, un correo de confirmación.
```

<!-- Volver al índice de plantillas: abre README.md en esta misma carpeta (ejercicios/plantillas/README.md). -->
