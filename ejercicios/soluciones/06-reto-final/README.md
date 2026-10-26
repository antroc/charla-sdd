# Soluciones del reto final

> **Para quién:** cualquier persona que haya empezado o terminado el ejercicio 06 · **Tiempo de lectura:** ~5 min · **Nivel:** 🟡 intermedio

El [ejercicio 06](../../06-reto-final-tu-propio-proyecto.md#solución-o-ejemplo-resuelto) te pide llevar un problema tuyo por todo el flujo de SDD (*Spec-Driven Development*, desarrollo guiado por especificaciones) y avisa de que no tiene una solución única, porque cada proyecto es distinto. Esta carpeta no lo contradice: reúne los materiales con los que sí puedes comparar tu trabajo cuando lo tengas hecho, o a medias.

> [!NOTE]
> Son ejemplos, no la única respuesta correcta. Un proyecto tuyo que pase la lista de entrega y puntúe bien en la rúbrica es igual de válido aunque recorte, decida y redacte de otra forma.


## Mínimo esperado

Un reto final válido puede ser pequeño: 1 P1 útil, 4-6 requisitos trazables, 2-3 criterios medibles, 3-5 aclaraciones, un plan breve, tasks pequeñas con dependencias visibles, código y pruebas para la P1 y un cambio funcional que empiece en la spec. Marca qué tasks pueden ejecutarse en paralelo cuando no dependan entre sí.

El préstamo de portátiles de esta carpeta es un **ejemplo ampliado**, no el tamaño objetivo del ejercicio.
## Qué hay en esta carpeta

| Material | Qué contiene | Idea |
|---|---|---|
| [Préstamo de portátiles](prestamo-de-portatiles/README.md) | El ejemplo completo: la petición, la constitución, la especificación, el plan, las tareas y la autoevaluación | 1 |
| [Otras ideas](otras-ideas.md) | Un esqueleto de partida para cada una de las otras seis ideas que el ejercicio plantea y no resuelve: petición, recorte, historias, un principio de constitución, cinco requisitos, tres aclaraciones, lo que queda fuera y el error típico | 2, 3, 5, 6, 7 y 8 |
| [Solicitud de vacaciones](../01-solicitud-de-vacaciones/especificacion.md) | La especificación completa del ejercicio 01, que el reto te pide llevar hasta el código | 4 |

## Por qué el reto no tiene una solución única

Un proyecto del reto se parece más a un encargo que a un problema de examen: no hay una respuesta que acertar, hay decisiones que tomar y dejar por escrito. Tres razones:

- **El problema y la persona que decide son tuyos.** Otra Ana contestaría de otra forma a las mismas aclaraciones y la especificación cambiaría con ellas; las dos versiones serían correctas.
- **El recorte es una decisión.** Dos P1 distintas para la misma idea pueden valer solas las dos. La tuya puede ser más pequeña o más grande que la de los ejemplos y estar igual de bien si cabe en uno o dos días con sus pruebas.
- **Quien juzga no es una clave de respuestas.** Lo juzgan la [lista de verificación de entrega](../../06-reto-final-tu-propio-proyecto.md#lista-de-verificación-de-entrega), la [rúbrica](../../06-reto-final-tu-propio-proyecto.md#rúbrica-de-autoevaluación) y la revisión de quien encargó el proyecto: ¿está cada decisión escrita? ¿se entiende sin abrir el código?

## Cómo usar estos materiales sin estropearte el ejercicio

1. **Haz tu proyecto primero.** Elige idea, escribe la petición y recorre los pasos sin abrir la solución de tu idea. Si no sabes cómo recortar, lee el recorte de otra idea, no el de la tuya.
2. **Compárate con las reglas, no con el ejemplo.** Pasa tu trabajo por la lista de entrega y puntúate con la rúbrica: ahí está lo que de verdad se evalúa.
3. **Después, abre la solución de tu idea** y compara pieza a pieza: ¿tu P1 vale sola?, ¿tu principio prohíbe algo concreto?, ¿cada aclaración tuya cambió algo en la especificación?
4. **Apunta las diferencias, no las copies.** Lo que descubras va a «Tres cosas que haría distinto» de tu `docs/autoevaluacion.md`; si algo del ejemplo te parece mejor, cámbialo en tu especificación y deja anotado por qué.

## Las ocho ideas y su solución

| # | Idea | Nivel | Su solución |
|---|---|---|---|
| 1 | Préstamo de portátiles y proyectores | 🟢 | [Ejemplo completo](prestamo-de-portatiles/README.md) |
| 2 | Buzón de sugerencias con votos | 🟢 | [Esqueleto](otras-ideas.md#buzón-de-sugerencias-con-votos) |
| 3 | Días en la oficina | 🟢 | [Esqueleto](otras-ideas.md#días-en-la-oficina) |
| 4 | Solicitud de vacaciones | 🟡 | [Especificación completa](../01-solicitud-de-vacaciones/especificacion.md) |
| 5 | Incidencias de oficina | 🟡 | [Esqueleto](otras-ideas.md#incidencias-de-oficina) |
| 6 | Inscripción a cursos internos | 🟡 | [Esqueleto](otras-ideas.md#inscripción-a-cursos-internos) |
| 7 | Turnos de guardia del equipo de soporte | 🔴 | [Esqueleto](otras-ideas.md#turnos-de-guardia-del-equipo-de-soporte) |
| 8 | Horas por proyecto con cierre mensual | 🔴 | [Esqueleto](otras-ideas.md#horas-por-proyecto-con-cierre-mensual) |

## Qué tienen en común

Todo lo que hay aquí, y los dos ejemplos que cuenta el ejercicio, comparten cinco rasgos. Son lo que conviene mirar de un buen resultado, más que el código:

- **Una P1 que vale sola.** Cada petición se recorta hasta una primera historia que, si fuera la única, ya resolvería el problema de hoy; lo recortado va a la P2, a la P3 o a «Fuera de alcance», con su razón.
- **Quien decide es distinto de quien construye.** Ana, Jorge o Marta responden a las aclaraciones y aprueban el texto; quien construye lo escribe. Si haces los dos papeles, la regla es escribir cada decisión antes de usarla: lo que no está escrito no existe.
- **Cada decisión, en un fichero.** El recorte en la petición, las respuestas en las aclaraciones de `spec.md`, las alternativas descartadas en `research.md`: nada vive solo en el chat del asistente de IA.
- **El análisis, para corregir antes de implementar.** Se ejecuta `/speckit.analyze` antes de escribir código y se repite hasta que sale sin incidencias CRITICAL ni HIGH y con cobertura del 100 % (cada requisito tiene al menos una tarea).
- **Un cambio que empieza por la especificación.** Quien encarga decide y pide el cambio, quien construye lo escribe en `spec.md` y quien encarga relee el texto nuevo y lo aprueba; después, `/speckit.converge` añade a `tasks.md` las tareas que faltan y `/speckit.implement` las ejecuta. Quien decide no necesita editar ficheros: basta con pedirlo por escrito y aprobar el texto nuevo. La idea 7 lo muestra con [el requisito antes y después](otras-ideas.md#el-cambio-que-llega-después).

## En tres frases

1. El reto no tiene una solución única, pero sí un ejemplo completo (el préstamo de portátiles), un esqueleto para cada idea que falta y la especificación de vacaciones del ejercicio 01.
2. Se usan después de hacer tu proyecto, para compararte con la lista de entrega, la rúbrica y la solución de tu idea, no para copiar.
3. Lo que tienen en común, y lo que conviene imitar, no es el código: es una P1 que vale sola, una persona que decide, cada decisión por escrito, un análisis antes de implementar y un cambio que empieza por la especificación.

## Siguiente paso

Vuelve al [ejercicio 06](../../06-reto-final-tu-propio-proyecto.md) y sigue por donde lo dejaste. Si aún no has elegido idea, empieza por la [tabla de las ocho](../../06-reto-final-tu-propio-proyecto.md#ocho-ideas-de-proyecto); si ya has terminado, abre la solución de tu idea en la tabla de arriba y compara.

---

⬅️ [Ejercicio 06](../../06-reto-final-tu-propio-proyecto.md) · 🏠 [Índice de soluciones](../README.md)
