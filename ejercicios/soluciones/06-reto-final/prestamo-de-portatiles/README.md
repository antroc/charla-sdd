# Préstamo de portátiles: el ejemplo completo del reto final

> **Para quién:** cualquier persona que haya empezado el ejercicio 06 y quiera ver un ejemplo completo · **Tiempo de lectura:** ~12 min · **Nivel:** 🟡 intermedio

Esta carpeta contiene el **ejemplo completo de la idea 1 del reto**: los artefactos que produce una sesión bien hecha de SDD (*Spec-Driven Development*, desarrollo guiado por especificaciones) con GitHub Spec Kit (<https://github.com/github/spec-kit>) para una aplicación pequeña, el préstamo de portátiles y proyectores de Oficina. Es el [ejemplo 1 del ejercicio 06](../../../06-reto-final-tu-propio-proyecto.md#solución-o-ejemplo-resuelto) con todos sus ficheros, en el estado en que los dejó Luis tras dos tardes de trabajo con Ana, justo antes del cambio que ella pidió al final. Ese cambio se cuenta con sus diferencias en el último apartado de «Lo que pasó por el camino», igual que los [pasos 7 a 10 de ReservaSalas](../../03-reserva-salas-pasos-7-a-10.md) cuentan el suyo.

> [!IMPORTANT]
> Es **un** ejemplo, no «la única respuesta correcta», y tiene fallos que su autor reconoce en la [autoevaluación](autoevaluacion.md): saca 17 de 20. Si tu proyecto es el mismo y te sale distinto, no pasa nada: lo que se compara es el método, no la letra. Ábrelo después de haber escrito tu propia petición y tu primera especificación, no antes.

**Qué vas a encontrar**

- [Qué contiene](#qué-contiene)
- [El recorrido de Luis, en dos tardes](#el-recorrido-de-luis-en-dos-tardes)
- [Lo que pasó por el camino](#lo-que-pasó-por-el-camino)
  - [Las cuatro aclaraciones de Ana y lo que cambió cada una](#las-cuatro-aclaraciones-de-ana-y-lo-que-cambió-cada-una)
  - [La constitución frenó una propuesta](#la-constitución-frenó-una-propuesta)
  - [El análisis encontró una incidencia HIGH](#el-análisis-encontró-una-incidencia-high)
  - [El cambio de Ana: de diez a cinco días laborables](#el-cambio-de-ana-de-diez-a-cinco-días-laborables)
- [La entrega](#la-entrega)
- [Qué mirar al compararlo con tu proyecto](#qué-mirar-al-compararlo-con-tu-proyecto)
- [En tres frases](#en-tres-frases)
- [Siguiente paso](#siguiente-paso)

## Qué contiene

| Fichero | Qué es | Paso del flujo | Comando de Spec Kit que lo produce |
|---|---|---|---|
| [peticion.md](peticion.md) | La petición de Ana, escrita por Luis, con las dos frases que ella cambió | Paso 1 del ejercicio 06, antes del flujo | Ninguno: se escribe a mano |
| [constitution.md](constitution.md) | Constitución: los cuatro principios del proyecto | 0. Constitución | `/speckit.constitution` |
| [spec.md](spec.md) | Especificación: tres historias, seis casos límite, nueve requisitos en EARS (una forma sencilla y estructurada de redactar requisitos), cuatro criterios de éxito y las cuatro aclaraciones de Ana | 1. Especificar y 2. Aclarar | `/speckit.specify` y después `/speckit.clarify` |
| [plan.md](plan.md) | Plan técnico: tecnología, comprobación contra la constitución, decisiones y alternativas, modelo de datos, páginas, estructura, arranque y registro de complejidad | 3. Planificar | `/speckit.plan` (con `research.md`, `data-model.md` y `quickstart.md` resumidos dentro) |
| [tasks.md](tasks.md) | 31 tareas por fases e historias, con las pruebas antes que el código | 4. Trocear en tareas | `/speckit.tasks` |
| [autoevaluacion.md](autoevaluacion.md) | La rúbrica puntuada (17 de 20), tres cosas que haría distinto y la lista de entrega | Paso 11 del ejercicio 06 | Ninguno: se escribe a mano |

No incluimos el código: lo genera el asistente a partir de estos ficheros (`/speckit.implement`) y cada asistente lo escribe distinto. Tampoco la lista de verificación de la especificación (`checklists/requirements.md`): la de [ReservaSalas](../../03-reserva-salas/checklist.md) es un buen modelo de cómo queda.

## El recorrido de Luis, en dos tardes

| Cuándo | Qué hizo | Ficheros |
|---|---|---|
| Martes 3 de noviembre de 2026, por la tarde | Escribió la petición con lo que le contó Ana (ella tardó diez minutos en leerla y cambió dos frases), dictó la constitución, especificó sin tecnología y aclaró con ella por escrito: cuatro preguntas | `peticion.md`, `constitution.md`, `spec.md` |
| Jueves 5 de noviembre de 2026, por la tarde | Planificó con la tecnología del ejercicio 03, troceó en tareas, analizó (una incidencia HIGH, corregida antes de implementar), implementó en dos rondas, enseñó el producto mínimo a Ana ese mismo día y obtuvo «Converged» en la segunda pasada de `/speckit.converge`; después aplicó el cambio que Ana pidió, se autoevaluó y abrió la *pull request* | `plan.md`, `tasks.md`, `autoevaluacion.md` |

## Lo que pasó por el camino

### Las cuatro aclaraciones de Ana y lo que cambió cada una

Una aclaración que no cambia nada en la especificación no ha servido. Aquí cada respuesta dejó huella:

| Pregunta | Respuesta de Ana | Qué cambió en la especificación |
|---|---|---|
| ¿Cuántos días puede durar un préstamo como máximo? | Diez días laborables | El límite de RF-005, el criterio 4 de la historia 1 y el caso límite «Límite de días y fechas pasadas» |
| ¿Se puede prorrogar un préstamo? | Una sola vez, sin pasar del máximo | RF-008, la parte de prórroga de RF-005 y el caso límite «Prórroga rechazada» |
| ¿Hay que guardar para qué se pide el equipo? | No | La entidad Préstamo no tiene motivo, el principio 2 lo confirma y «Fuera de alcance» lo recoge |
| ¿Hay que avisar antes de la devolución? | Sí: un correo el día laborable anterior | RF-009, CE-004 y la única desviación del plan |

### La constitución frenó una propuesta

En la primera versión del plan, el asistente propuso guardar el departamento de cada persona para poder contar los préstamos por departamento. La comprobación contra la constitución lo frenó: el principio 2 prohíbe guardar departamentos y ningún requisito lo necesita. La alternativa descartada quedó anotada en la tabla «Decisiones y alternativas» de [plan.md](plan.md), con el principio que la impide. Es lo que sostiene el 4 en «fidelidad a la constitución»: la constitución no solo se describió, se usó.

### El análisis encontró una incidencia HIGH

El primer `/speckit.analyze`, con 28 tareas, dijo esto (extracto):

```markdown
## Informe de análisis de la especificación (Specification Analysis Report)

| ID | Categoría (Category) | Gravedad (Severity) | Dónde (Location(s)) | Resumen (Summary) | Recomendación (Recommendation) |
|----|----------------------|---------------------|---------------------|-------------------|--------------------------------|
| C1 | Cobertura (Coverage Gaps) | HIGH | `spec.md`, RF-009 y CE-004; `tasks.md` | El correo de aviso del día laborable anterior a la devolución no tiene ninguna tarea | Añadir una tarea de pruebas, otra que envíe el correo y otra que programe su ejecución diaria |

**Métricas (Metrics):**

- Requisitos totales (Total Requirements): 9
- Tareas totales (Total Tasks): 28
- Cobertura (Coverage %): 89 % (8 de 9 requisitos con al menos una tarea)
- Incidencias críticas (Critical Issues Count): 0 (por gravedad: CRITICAL 0 · HIGH 1 · MEDIUM 0 · LOW 0)
```

Con una incidencia HIGH no se pasa a implementar. Luis pidió al asistente que añadiera lo que faltaba (T021, T024 y T025, y el aviso programado dentro de T031) y volvió a lanzar el análisis: sin incidencias CRITICAL ni HIGH y con cobertura del 100 % (9 de 9 requisitos, 31 tareas). Corregir `tasks.md` antes de implementar es barato; encontrarse con que nadie envía el correo cuando la aplicación ya está construida, no.

### El cambio de Ana: de diez a cinco días laborables

Con la aplicación funcionando, Ana decidió bajar el máximo de diez a cinco días laborables, para que los equipos no estén tanto tiempo fuera. Se hizo en el orden de siempre: Ana lo pidió, Luis lo escribió en la especificación y Ana releyó el texto nuevo y lo aprobó; después vinieron el plan, `/speckit.converge` y `/speckit.implement`. Estas son las tres piezas, con los números de línea de los ficheros de esta carpeta.

**1. La especificación cambia primero.** `git diff -U1` solo muestra cambios en `spec.md` (hemos quitado la línea `index` y el texto que Git añade tras cada `@@`):

```diff
diff --git a/specs/001-prestamo-portatiles/spec.md b/specs/001-prestamo-portatiles/spec.md
--- a/specs/001-prestamo-portatiles/spec.md
+++ b/specs/001-prestamo-portatiles/spec.md
@@ -37,3 +37,3 @@
 3. **Dado** que Luis tiene PORT-03 del lunes 16 al miércoles 18, **cuando** Marta pide PORT-03 del martes 17 al jueves 19, **entonces** el sistema rechaza la petición e indica que Luis lo tiene hasta el miércoles 18 y que queda libre desde el jueves 19.
-4. **Dado** que Marta pide un portátil del lunes 16 al lunes 30 de noviembre (once días laborables), **cuando** intenta confirmar, **entonces** el sistema rechaza la petición e indica que el máximo son diez días laborables.
+4. **Dado** que Marta pide un portátil del lunes 16 al lunes 23 de noviembre (seis días laborables), **cuando** intenta confirmar, **entonces** el sistema rechaza la petición e indica que el máximo son cinco días laborables.
 5. **Dado** que Marta pide un portátil que empieza el sábado 21 de noviembre, **cuando** intenta confirmar, **entonces** el sistema rechaza la petición e indica que los préstamos empiezan y terminan en día laborable, de lunes a viernes.
@@ -80,3 +80,3 @@
 - **Solapamiento por un solo día:** un préstamo de PORT-03 del lunes 16 al miércoles 18 choca con otro del miércoles 18 al viernes 20, aunque solo coincidan en un día. Dos préstamos consecutivos (hasta el miércoles 18 y desde el jueves 19) no chocan. Si dos personas confirman el mismo equipo y las mismas fechas en el mismo segundo, solo se guarda una petición; la otra recibe el rechazo por solapamiento.
-- **Límite de días y fechas pasadas:** de lunes 16 a viernes 27 de noviembre (diez días laborables) se acepta; hasta el lunes 30 (once) se rechaza (máximo diez; ver Aclaraciones). Empezar hoy se permite; empezar antes de hoy, no.
+- **Límite de días y fechas pasadas:** de lunes 16 a viernes 20 de noviembre (cinco días laborables) se acepta; hasta el lunes 23 (seis) se rechaza (máximo cinco; ver Aclaraciones). Empezar hoy se permite; empezar antes de hoy, no.
 - **Fin de semana:** una petición que empieza el sábado 21 o termina el domingo 29 se rechaza: la recogida y la devolución son siempre en día laborable.
@@ -95,2 +95,6 @@

+### Sesión 2026-11-05
+
+- P: ¿Cuántos días puede durar un préstamo como máximo? → R: Cinco días laborables, para que los equipos no estén tanto tiempo fuera. Sustituye a la respuesta de la sesión 2026-11-03.
+
 ## Requisitos (Requirements)
@@ -105,3 +109,3 @@
 - **RF-004**: SI el equipo pedido ya está prestado o reservado en alguna de las fechas pedidas, ENTONCES el sistema deberá rechazar la petición e indicar quién lo tiene y cuándo queda libre.
-- **RF-005**: SI una petición de préstamo o de prórroga incumple un límite (empezar antes de hoy, empezar o terminar en fin de semana, superar diez días laborables en total, pedir una segunda prórroga o prorrogar un préstamo vencido), ENTONCES el sistema deberá rechazarla e indicar qué límite se incumple.
+- **RF-005**: SI una petición de préstamo o de prórroga incumple un límite (empezar antes de hoy, empezar o terminar en fin de semana, superar cinco días laborables en total, pedir una segunda prórroga o prorrogar un préstamo vencido), ENTONCES el sistema deberá rechazarla e indicar qué límite se incumple.
 - **RF-006**: DONDE la persona tenga rol de Oficina, el sistema deberá permitir marcar un préstamo reservado como entregado.
```

Son cuatro bloques de cambio: el criterio 4 de la historia 1, el caso límite, una sesión nueva de aclaraciones con la fecha de hoy y RF-005. La sesión del 2026-11-03 no se borra: es el historial de la decisión, y por eso el «diez» solo sobrevive en ella. Luis hizo *commit* de este paso antes de tocar nada más, para que el historial muestre que el cambio empezó por la especificación.

**2. El plan.** El modelo de datos y un mensaje de ejemplo también decían diez: son dos líneas de `plan.md` (la regla de `devolucion` y el texto del rechazo por límite), y `tasks.md` no se toca. Este es el recuento de las menciones al límite antiguo (`grep -ciE "diez días"`), antes y después:

| Fichero | Al empezar | Al terminar | Qué se hace con él |
|---|---|---|---|
| `spec.md` | 5 | 2 | Cambian el criterio 4, el caso límite y RF-005; las dos de la sesión del 2026-11-03 se quedan (historial) |
| `plan.md` | 2 | 0 | Cambian la regla de `devolucion` y el ejemplo del mensaje de rechazo |
| `tasks.md` | 1 | 1 | No se toca: T013 es lo que se hizo; la sustituirá T032 |

**3. Qué encuentra `/speckit.converge`.** Compara el código con la especificación, el plan y las tareas tal como están hoy y enseña esto antes de escribir nada:

```markdown
## Hallazgos de convergencia (Convergence Findings)

| ID | Tipo (Gap Type) | Gravedad (Severity) | Origen (Source) | Evidencia (Evidence) | Trabajo pendiente (Remaining Work) |
|----|-----------------|---------------------|-----------------|----------------------|------------------------------------|
| F1 | partial | HIGH | RF-005 | `tests/unitarias/test_reglas_prestamo.py` (T013) comprueba el límite de diez días laborables; ninguna prueba exige que seis días se rechacen | Actualizar las pruebas del límite a cinco días laborables |
| F2 | contradicts | HIGH | RF-005 | `src/prestamo/servicios/prestamos.py` (T017) y su mensaje en `src/prestamo/textos.py` (T008) aceptan préstamos de hasta diez días laborables; RF-005 ya dice cinco | Cambiar el límite y el mensaje de rechazo a cinco días laborables |

**Siguientes acciones (Next Actions):** he añadido 2 tareas en la fase `## Phase 7: Convergence` de `tasks.md` (T032 y T033). Ejecuta `/speckit.implement` para completarlas; un nuevo `/speckit.converge` encontrará menos hallazgos o ninguno.
```

Lo único que cambia en `tasks.md` es una fase nueva al final, con números a continuación de la última tarea (T031) y de la última fase (la 6). Spec Kit escribe el encabezado tal cual (`## Phase 7: Convergence`), aunque el resto del fichero esté en castellano:

```markdown
## Phase 7: Convergence

- [ ] T032 Actualizar las pruebas del límite en `tests/unitarias/test_reglas_prestamo.py`: un préstamo de cinco días laborables se acepta y otro de seis se rechaza indicando que el máximo son cinco, según RF-005 (partial)
- [ ] T033 Cambiar a cinco días laborables el límite de duración en `src/prestamo/servicios/prestamos.py` y en su mensaje de rechazo de `src/prestamo/textos.py`, según RF-005 (contradicts)
```

Luis lanzó `/speckit.implement solo la fase de convergencia`: las pruebas nuevas fallaron (rojo), el asistente cambió el límite y el mensaje, volvieron a pasar (verde) y `pytest` entero quedó en verde. Luis comprobó a mano que un préstamo de seis días se rechazaba con el mensaje nuevo y dio el cambio por bueno.

Aquí está el fallo que él mismo reconoce: no repitió `/speckit.converge`. Seguramente habría respondido «✅ Converged», pero es la comprobación que cubre a la vez la especificación, el plan y las tareas, y por no hacerla la coherencia se queda en un 3 y no llega al 4.

## La entrega

La *pull request* tenía 38 ficheros: la petición, la constitución, la carpeta de la especificación (con el plan, las tareas y las listas de verificación), el código y sus pruebas, los tres documentos de `docs/` y el `README.md`. Siguió el guion de cinco puntos del ejercicio como descripción, con enlaces directos a `spec.md`, `plan.md`, `tasks.md` y `docs/autoevaluacion.md`.

Hubo dos revisiones, como pide el ejercicio. Ana revisó la especificación en 20 minutos, contestó «¿es esto lo que pedí?» y pidió un cambio de texto. Un compañero con experiencia revisó la comprobación contra la constitución, el plan y las pruebas, y miró el historial para comprobar que el último cambio empezó por la especificación. Los comentarios de las dos revisiones son la primera lista de aclaraciones de la versión 2.

## Qué mirar al compararlo con tu proyecto

Pasa tu trabajo por estas preguntas, que son las de la [rúbrica](../../../06-reto-final-tu-propio-proyecto.md#rúbrica-de-autoevaluación) dichas de otra manera:

- **¿Tu P1 vale sola?** Aquí es «pedir un equipo para unas fechas y recogerlo»: con solo eso, ningún equipo sale sin una persona y una fecha, y el cuaderno deja de hacer falta para pedir y entregar. Lo demás es P2 y P3.
- **¿Tu principio propio prohíbe algo concreto?** El cuarto de Luis lo hace: «no existen préstamos abiertos». Sirvió para decidir cosas del plan (un préstamo vencido no desaparece de «Hoy») y de la especificación (sin responsable o sin fecha no se guarda).
- **¿Cada aclaración tuya cambió algo?** Compara con la tabla de arriba.
- **¿Usaste el análisis para corregir antes de implementar?** Aquí corrigió una incidencia HIGH.
- **¿Tu último cambio empezó por la especificación?** Aquí sí, y el historial lo demuestra.
- **¿Tu autoevaluación dice lo que falta?** La de Luis dice que dos requisitos no tienen criterio de aceptación, que no repitió `converge` y que nadie más ha seguido el `quickstart.md`.

## En tres frases

1. Este ejemplo recorre el flujo completo con una aplicación pequeña: petición, constitución, especificación con aclaraciones, plan, tareas, análisis, implementación, un cambio pedido desde la especificación y autoevaluación.
2. Lo que lo hace un buen resultado no es que no falle nada, sino que cada decisión está escrita en un fichero, el análisis se usó para corregir antes de implementar y el cambio empezó por la especificación.
3. Sus fallos (dos requisitos sin criterio de aceptación, un `converge` sin repetir, un `quickstart.md` sin probar por otra persona) están a la vista en la autoevaluación, que es lo que se espera de la tuya.

## Siguiente paso

Vuelve al [ejercicio 06](../../../06-reto-final-tu-propio-proyecto.md) y puntúa tu proyecto con la rúbrica, o abre el [índice de las soluciones del reto](../README.md) para ver los esqueletos del resto de ideas. Si quieres empezar por la primera pieza de este ejemplo, es la [petición](peticion.md).

---

⬅️ [Ejercicio 06](../../../06-reto-final-tu-propio-proyecto.md) · 🏠 [Índice del reto final](../README.md) · ➡️ [Siguiente: Petición](peticion.md)
