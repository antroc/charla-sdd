# ReservaSalas: los pasos 7 a 10 por dentro

> **Para quién:** cualquier persona que haya hecho el ejercicio 03 · **Tiempo de lectura:** ~15 min · **Nivel:** 🟡 intermedio

La [solución canónica del ejercicio 03](03-reserva-salas/README.md) guarda los seis ficheros que produce el flujo de SDD (*Spec-Driven Development*, desarrollo guiado por especificaciones): constitución, especificación, aclaraciones, lista de verificación, plan técnico y lista de tareas. Pero el [ejercicio 03](../03-reserva-salas-paso-a-paso.md) describe tres salidas más que allí no tienen ejemplo: el informe de `/speckit.analyze` (paso 7), el cambio de antelación de 30 a 60 días (paso 9) y la reflexión (paso 10).

Este fichero las cuenta desde fuera y no toca el ejemplo canónico: allí la antelación máxima sigue siendo de 30 días. Todo lo que verás está sacado de esos ficheros con `grep` y `git diff`, así que puedes comprobarlo. Los números de tarea (T001…) son los de [tasks.md](03-reserva-salas/tasks.md).

> [!NOTE]
> Es un ejemplo, no la única respuesta correcta. Cada asistente de IA redacta sus informes a su manera: fíjate en la estructura, no en la letra. Aquí los informes van en castellano, con los encabezados originales entre paréntesis; en tu pantalla pueden salir en inglés.

**Qué vas a encontrar**

- [Paso 7: el informe de /speckit.analyze](#paso-7-el-informe-de-speckitanalyze)
  - [Cómo leerlo](#cómo-leerlo)
  - [Cómo comprobarlo](#cómo-comprobarlo)
- [Paso 9: el cambio de 30 a 60 días, por dentro](#paso-9-el-cambio-de-30-a-60-días-por-dentro)
  - [1. La especificación cambia primero](#1-la-especificación-cambia-primero)
  - [2. El plan y la lista de verificación](#2-el-plan-y-la-lista-de-verificación)
  - [3. Qué encuentra converge](#3-qué-encuentra-converge)
  - [4. Las tareas nuevas](#4-las-tareas-nuevas)
  - [5. Implementar la convergencia](#5-implementar-la-convergencia)
  - [6. Tres comprobaciones a mano](#6-tres-comprobaciones-a-mano)
- [Paso 10: una reflexión de ejemplo](#paso-10-una-reflexión-de-ejemplo)
- [En tres frases](#en-tres-frases)
- [Siguiente paso](#siguiente-paso)

## Paso 7: el informe de /speckit.analyze

Luis lanza `/speckit.analyze` el 2026-10-09, justo después de generar las tareas. El comando es de solo lectura: cruza `spec.md`, `plan.md`, `tasks.md` y la constitución, y deja su informe en el chat sin crear ningún fichero. Con los ficheros del ejemplo canónico, el informe sería este:

```markdown
## Informe de análisis de la especificación (Specification Analysis Report)

| ID | Categoría (Category) | Gravedad (Severity) | Dónde (Location) | Resumen (Summary) | Recomendación (Recommendation) |
|----|----------------------|---------------------|------------------|-------------------|--------------------------------|
| U1 | Subespecificación (Underspecification) | MEDIUM | `spec.md`, «Casos límite»; `tasks.md`, Fase 3 (T014) | El caso límite «Para ya mismo» dice que una franja que ya ha empezado se acepta si termina en el futuro. T014 prueba el rechazo de «fin en el pasado», pero ninguna tarea prueba el caso que se acepta | Añadir esa prueba a T014 |
| C1 | Cobertura (Coverage Gaps) | LOW | `tasks.md`, Fases 3 a 5 | T022, T030, T031 y T035 a T038 (implementación) no citan ningún requisito y T023 cita un rango. RF-012, por ejemplo, solo lo cita una tarea de pruebas (T033) | Citar en cada tarea el requisito que implementa |
| A1 | Ambigüedad (Ambiguity) | LOW | `plan.md`, «Arranque rápido» | `git clone <url-del-repositorio-interno> reserva-salas` deja un marcador sin resolver: la URL depende de cada equipo | Aceptable por ahora; poner la URL real al crear `README.md` (T005) |

**Tabla de cobertura (Coverage Summary Table):**

| Requisito (Requirement Key) | ¿Tiene tarea? (Has Task?) | Tareas (Task IDs) | Notas (Notes) |
|---|---|---|---|
| RF-001 | Sí | pruebas T015 · código T018, T023* | |
| RF-002 | Sí | pruebas T015 · código T018, T023* | |
| RF-003 | Sí | pruebas T016 · código T020, T023* | |
| RF-004 | Sí | pruebas T016, T033 · código T023* | T038 muestra el responsable y no lo cita |
| RF-005 | Sí | pruebas T013, T016 · código T020, T023* | |
| RF-006 | Sí | pruebas T014, T016 · código T019, T023* | |
| RF-007 | Sí | pruebas T015, T016 · código T018, T020, T023* | |
| RF-008 | Sí | pruebas T026 · código T029 | T030 y T031 lo implementan sin citarlo |
| RF-009 | Sí | pruebas T040 · código T041 | Administración, sin historia propia |
| RF-010 | Sí | pruebas T025, T026 · código T028 | |
| RF-011 | Sí | pruebas T017, T027 · código T021, T029 | |
| RF-012 | Sí | pruebas T033 | T035 a T038 lo implementan sin citarlo |

\* T023 cita el rango «RF-001 a RF-007» y cuenta para los siete. Criterios de éxito con trabajo que construir: CE-002 (T013, T020, T042) y CE-004 (T043); CE-001 y CE-003 los mide una persona (T044, tarea manual).

**Alineación con la constitución (Constitution Alignment Issues):** ninguna incidencia. Los cinco principios se cumplen.

| Principio | Qué lo respalda | Estado |
|---|---|---|
| 1. Sencillez primero | Una sola desviación, la API JSON, justificada en `plan.md` («Registro de complejidad»); la implementan T022, T030, T036 y T041 | Cumple |
| 2. Accesible y en castellano | T009 y T024 (mensajes en `textos.py`), T012 (plantilla base accesible) y T045 (revisión con lector de pantalla, manual) | Cumple |
| 3. Pruebas antes de dar algo por hecho | Pruebas antes que código en cada historia: T013-T017 antes de T018-T023, T025-T027 antes de T028-T031, T033-T034 antes de T035-T038, y T040 antes de T041 | Cumple |
| 4. Datos mínimos | T006 crea `persona` con lo que dice el plan (nombre, correo y rol) y ninguna tarea guarda otros datos personales | Cumple |
| 5. Transparencia | T026 y T029 guardan quién cancela y quién modifica; T016 y T038 muestran el responsable | Cumple |

**Tareas sin requisito (Unmapped Tasks):** 18 tareas no citan ningún RF ni llevan marca de historia: T001 a T012 (Fases 1 y 2, la infraestructura que sostiene a las tres historias) y T042 a T047 (Fase 6: verifican CE-001 a CE-004 y el principio 2, revisan la constitución y completan el `README.md`). Ninguna es una funcionalidad que nadie haya pedido.

**Métricas (Metrics):**

- Requisitos totales (Total Requirements): 12
- Tareas totales (Total Tasks): 47
- Cobertura (Coverage %): 100 % (12 de 12 requisitos con al menos una tarea)
- Ambigüedades (Ambiguity Count): 1
- Duplicidades (Duplication Count): 0
- Incidencias críticas (Critical Issues Count): 0 (por gravedad: CRITICAL 0 · HIGH 0 · MEDIUM 1 · LOW 2)

**Siguientes acciones (Next Actions):**

- No hay incidencias CRITICAL ni HIGH y la cobertura es del 100 %: puedes pasar a `/speckit.implement`.
- Si prefieres cerrar antes las tres incidencias, las recomendaciones de la primera tabla bastan.
- ¿Quieres que proponga correcciones concretas para las 3 incidencias? No aplicaré nada sin que lo apruebes.
```

### Cómo leerlo

- **Primero, las métricas.** Las incidencias CRITICAL tienen que ser 0 y la cobertura, 100 %: es el umbral del paso 7. Si falla alguna, no pases a implementar.
- **Después, la tabla de incidencias, de arriba abajo.** Va por gravedad: CRITICAL y HIGH se corrigen antes de implementar; MEDIUM y LOW se anotan (Luis las recoge para el paso 10).
- **Luego, la cobertura.** Busca un «No» en «¿Tiene tarea?» y comprueba que las pruebas van antes que el código de su historia.
- **Una incidencia con la constitución sería siempre CRITICAL.** Y los números T0xx son los de `tasks.md`: ábrelo al lado, porque el informe los cita pero no los copia.

### Cómo comprobarlo

La tabla de cobertura sale de `tasks.md`, no de memoria. Desde la carpeta del ejemplo canónico, este bucle da las tareas que citan cada requisito (T023 solo sale en RF-001 y RF-007 porque cita el rango «RF-001 a RF-007»; por eso lleva asterisco en el informe):

```bash
for n in 001 002 003 004 005 006 007 008 009 010 011 012; do
  echo "RF-$n: $(grep "RF-$n" tasks.md | grep -oE '^- \[.\] T[0-9]{3}' | grep -oE 'T[0-9]{3}' | tr '\n' ' ')"
done
grep -cE '^- \[.\] T[0-9]{3}' tasks.md                                                           # 47 tareas
grep -E '^- \[.\] T[0-9]{3}' tasks.md | grep -vE 'RF-0|\[HU' | grep -oE '^- \[.\] T[0-9]{3}'    # las 18 sin requisito ni historia
```

## Paso 9: el cambio de 30 a 60 días, por dentro

Es el lunes 2026-10-26. La primera versión quedó guardada el 2026-10-12 (las tareas se habían generado el 2026-10-09), así que han pasado dos semanas. Ana ha visto que los equipos quieren reservar con más de un mes de antelación las reuniones de planificación del trimestre y decide ampliar la antelación máxima de 30 a 60 días.

Con *vibe coding* (programar a golpe de instrucciones sueltas, improvisando con el asistente de IA), Luis buscaría «30» en el código y lo cambiaría a mano. Con SDD el cambio sigue otro orden: Ana lo pide, Luis lo escribe en la especificación y Ana relee el texto nuevo y lo aprueba; después vienen el plan, `/speckit.converge` e `/speckit.implement`. No se relanza `/speckit.tasks`, que rehace la lista entera.

### 1. La especificación cambia primero

Luis le da al asistente el primer *prompt* del paso 9 (la instrucción que le escribes al asistente; aquí, sin comando `speckit`). Solo cambia `spec.md`, y `git diff` lo confirma:

```text
$ git diff --stat
 specs/001-reserva-salas/spec.md | 8 ++++++--
 1 file changed, 6 insertions(+), 2 deletions(-)
```

Así son los cambios (`git diff -U1`). Los números tras `@@` son los del `spec.md` del ejemplo canónico; he quitado la línea `index` y el texto que Git añade tras cada `@@`:

```diff
diff --git a/specs/001-reserva-salas/spec.md b/specs/001-reserva-salas/spec.md
--- a/specs/001-reserva-salas/spec.md
+++ b/specs/001-reserva-salas/spec.md
@@ -87,3 +87,3 @@
 - **«Para ya mismo» con la sala ocupada:** si son las 10:10 y alguien pide Mediterráneo de 10:00 a 11:00 pero está reservada, el sistema rechaza la petición e indica hasta qué hora está ocupada. Reservar una franja que ya ha empezado está permitido mientras la hora de fin sea futura.
-- **Antelación excesiva:** una reserva para dentro de 45 días se rechaza (máximo 30 días; ver Aclaraciones).
+- **Antelación excesiva:** una reserva para dentro de 75 días se rechaza (máximo 60 días; ver Aclaraciones).
 - **Fin anterior al inicio:** una franja de 11:00 a 10:00 se rechaza con un mensaje claro.
@@ -101,2 +101,6 @@
 
+### Sesión 2026-10-26
+
+- P: ¿Con cuánta antelación máxima se puede reservar? → R: 60 días, para poder reservar con tiempo las reuniones de planificación del trimestre. Sustituye a la respuesta de la sesión 2026-10-07.
+
 ## Requisitos (Requirements)
@@ -112,3 +116,3 @@
 - **RF-005**: SI la franja solicitada se solapa con otra reserva de la misma sala, ENTONCES el sistema deberá rechazar la reserva e indicar qué franja está ocupada.
-- **RF-006**: SI la franja solicitada queda fuera del horario de oficina (08:00-20:00), dura más de 4 horas, termina en el pasado o empieza más de 30 días después de hoy, ENTONCES el sistema deberá rechazar la reserva e indicar qué límite se incumple.
+- **RF-006**: SI la franja solicitada queda fuera del horario de oficina (08:00-20:00), dura más de 4 horas, termina en el pasado o empieza más de 60 días después de hoy, ENTONCES el sistema deberá rechazar la reserva e indicar qué límite se incumple.
 - **RF-007**: MIENTRAS una sala esté marcada en mantenimiento, el sistema deberá impedir nuevas reservas en ella.
```

Son tres bloques de cambio: el caso límite pasa a 75 días (sigue siendo un rechazo), nace una sesión de aclaraciones con la fecha de hoy y RF-006 dice 60. La sesión del 2026-10-07 no se borra: es el historial de la decisión, y por eso el «30» solo sobrevive en ella. Ana relee estas líneas en la vista de GitHub, las aprueba y Luis guarda el paso con un *commit* (una versión guardada en Git):

```bash
git add -A
git commit -m "Antelación máxima de 60 días: especificación"
```

### 2. El plan y la lista de verificación

El segundo *prompt* del ejercicio pide actualizar el plan y «cualquier otro fichero» de la carpeta que mencione el límite, salvo `tasks.md`. Un `grep -rc "30 días" specs/001-reserva-salas/` dice cuáles son. Uso las rutas de un proyecto real: en el ejemplo canónico la lista de verificación se llama `checklist.md` y el modelo de datos (`data-model.md` en tu proyecto) está dentro de `plan.md`.

| Fichero | Al empezar | Al terminar | Qué se hace con él |
|---|---|---|---|
| `spec.md` | 3 | 1 | Cambian RF-006 y el caso límite; la sesión del 2026-10-07 se queda (historial) |
| `plan.md` | 1 | 0 | Cambia la restricción de `inicio` en el modelo de datos |
| `checklists/requirements.md` | 2 | 1 | Cambia CHK014; la nota con el resultado del 2026-10-07 se queda (historial) |
| `tasks.md` | 2 | 2 | No se toca: T014 y T019 son lo que se hizo; las sustituirán T048 y T049 |
| `aclaraciones.md` | 2 | 2 | Solo existe en el ejemplo canónico: es el acta de la sesión del 2026-10-07, la aclaración antigua de `spec.md` |

Cambia una línea en dos ficheros (`git diff -U1`, desde el *commit* anterior):

```diff
diff --git a/specs/001-reserva-salas/checklists/requirements.md b/specs/001-reserva-salas/checklists/requirements.md
--- a/specs/001-reserva-salas/checklists/requirements.md
+++ b/specs/001-reserva-salas/checklists/requirements.md
@@ -32,3 +32,3 @@
 - [x] CHK013 No hay adjetivos vagos sin cifra («rápido», «sencillo», «intuitivo») en requisitos ni en criterios de éxito.
-- [x] CHK014 Los límites numéricos están cerrados: horario 08:00-20:00, máximo 4 horas, antelación máxima 30 días, 12 salas en 3 plantas.
+- [x] CHK014 Los límites numéricos están cerrados: horario 08:00-20:00, máximo 4 horas, antelación máxima 60 días, 12 salas en 3 plantas.
 - [x] CHK015 Los roles están definidos sin ambigüedad. — Dos roles (empleado y administración) y qué puede hacer cada uno (RF-008, RF-009, RF-010).
diff --git a/specs/001-reserva-salas/plan.md b/specs/001-reserva-salas/plan.md
--- a/specs/001-reserva-salas/plan.md
+++ b/specs/001-reserva-salas/plan.md
@@ -117,3 +117,3 @@
 | `persona_id` | entero | obligatorio; referencia a `persona` (principio 5) |
-| `inicio`, `fin` | texto ISO 8601 (`2026-10-22T10:00`) | `fin` posterior a `inicio`; dentro de 08:00-20:00; duración máxima 4 h; `fin` en el futuro; `inicio` como máximo 30 días después de hoy (RF-006) |
+| `inicio`, `fin` | texto ISO 8601 (`2026-10-22T10:00`) | `fin` posterior a `inicio`; dentro de 08:00-20:00; duración máxima 4 h; `fin` en el futuro; `inicio` como máximo 60 días después de hoy (RF-006) |
 | `motivo` | texto | opcional, máximo 120 caracteres |
```

No cambia nada más. Las dos notas del 2026-10-07 (la de la lista de verificación y la sesión de `spec.md`) siguen diciendo 30 días a propósito: cuentan lo que se decidió ese día.

### 3. Qué encuentra converge

Ahora, `/speckit.converge`. Compara el código con la especificación, el plan y las tareas tal como están hoy (no mira el historial de Git) y enseña esto antes de escribir nada:

```markdown
## Hallazgos de convergencia (Convergence Findings)

| ID | Tipo (Gap Type) | Gravedad (Severity) | Origen (Source) | Evidencia (Evidence) | Trabajo pendiente (Remaining Work) |
|----|-----------------|---------------------|-----------------|----------------------|------------------------------------|
| F1 | partial | HIGH | RF-006 | `tests/unitarias/test_limites.py` (T014) comprueba el límite antiguo; ninguna prueba exige que 45 o 60 días se acepten | Actualizar las pruebas de límites a 60 días |
| F2 | contradicts | HIGH | RF-006 | `src/reservasalas/servicios/reservas.py` (T019) y su mensaje en `src/reservasalas/textos.py` rechazan lo que empieza a más de 30 días; RF-006 ya dice 60 | Cambiar el límite y el mensaje de rechazo a 60 días |

**Métricas (Summary metrics):**

- Requisitos y criterios de aceptación revisados: 28 (12 RF y 16 criterios de aceptación)
- Decisiones del plan revisadas: 6
- Principios de la constitución revisados: 5
- Hallazgos por tipo: missing 0 · partial 1 · contradicts 1 · unrequested 0
- Hallazgos por gravedad: CRITICAL 0 · HIGH 2 · MEDIUM 0 · LOW 0

**Siguientes acciones (Next Actions):** he añadido 2 tareas en la fase `## Phase 7: Convergence` de `tasks.md` (T048 y T049). Ejecuta `/speckit.implement` para completarlas; un nuevo `/speckit.converge` encontrará menos hallazgos o ninguno.
```

F2 es el que anuncia el ejercicio: el código sigue rechazando lo que va de 31 a 60 días (`contradicts`). F1 es más discreto: las pruebas existen, pero miran el valor antiguo (`partial`). Ninguno es CRITICAL: no viola un principio de la constitución ni impide reservar una sala. En este ejemplo, las tareas manuales T044 y T045 ya las hicieron personas y están marcadas `[X]`; si no, `converge` las volvería a señalar y habría que recordarle que son manuales.

### 4. Las tareas nuevas

`converge` solo escribe en `tasks.md`: añade una fase al final, con números a continuación de la última tarea (T047) y de la última fase (la 6). Esto es lo único que cambia en el fichero:

```markdown
## Phase 7: Convergence

- [ ] T048 Actualizar las pruebas de límites en `tests/unitarias/test_limites.py`: una reserva a 45 días y otra a 60 días se aceptan, y una a 61 días y otra a 75 días se rechazan indicando que el máximo son 60 días, según RF-006 (partial)
- [ ] T049 Cambiar a 60 días el límite de antelación de la validación en `src/reservasalas/servicios/reservas.py` y de su mensaje de rechazo en `src/reservasalas/textos.py`, según RF-006 (contradicts)
```

Cada tarea lleva su ruta de fichero, su requisito de origen y el tipo de desviación entre paréntesis, y las pruebas (T048) van antes que el código (T049), como pide el principio 3. Spec Kit escribe el encabezado tal cual (`## Phase 7: Convergence`); en el `tasks.md` canónico los demás están traducidos, y tu asistente puede traducir también este. T001 a T047 no se tocan, y T014 y T019 siguen diciendo 30 días porque son lo que se hizo.

### 5. Implementar la convergencia

Luis lanza `/speckit.implement solo la fase de convergencia`. Esto es lo que hace el asistente, en orden (un resumen, no la salida literal):

```text
Listas de verificación: requirements.md, 23 de 23 marcadas. Sigo.
T048  Escribo las pruebas de antelación (45, 60, 61 y 75 días) y las ejecuto:
      pytest tests/unitarias/test_limites.py -k antelacion → 4 failed   [rojo]
T049  Cambio el límite y su mensaje de rechazo a 60 días y las vuelvo a ejecutar:
      pytest tests/unitarias/test_limites.py -k antelacion → 4 passed   [verde]
      pytest (toda la batería) → todo en verde
Marcadas como [X] en tasks.md: T048, T049
```

Primero rojo, después verde: es el principio 3 en pequeño. Un segundo `/speckit.converge` ya no encuentra nada, y como no hay trabajo pendiente, deja `tasks.md` exactamente como está:

```text
✅ Converged: la implementación cumple la especificación, el plan y las tareas.
Revisado: 12 requisitos, 16 criterios de aceptación, 6 decisiones del plan y 5 principios. Hallazgos: 0.
Siguiente paso: pasar a revisión.
```

Si en tu proyecto señalara T014 o T019 por decir 30 días, no las edites: dile que las sustituyen T048 y T049 y vuelve a lanzar `converge`.

### 6. Tres comprobaciones a mano

Si la aplicación está arrancada con `--reload`, se recarga sola. Luis comprueba tres cosas:

```text
1. pytest → toda la batería en verde.
2. Mediterráneo para dentro de 45 días (10 de diciembre, de 10:00 a 11:00) → aceptada: «Reserva confirmada: Mediterráneo, jueves 10 de diciembre, de 10:00 a 11:00».
3. Mediterráneo para dentro de 75 días (9 de enero de 2027, de 10:00 a 11:00) → rechazada: «La antelación máxima es de 60 días. Elige una fecha más cercana.»
```

El orden es siempre especificación, plan, `converge` e `implement` porque lo escrito manda y el código solo se mueve cuando una tarea lo pide: si empiezas por el código, no queda nada contra lo que compararlo.

## Paso 10: una reflexión de ejemplo

El ejercicio pide dos líneas por pregunta en `docs/reflexion.md`. Este es el de Luis, que no ha escrito código y ha leído sobre todo pruebas, plan y especificación. Son respuestas de ejemplo: las tuyas serán otras, y lo que cuenta es que sean concretas y no lleven cifras que no hayas medido.

```markdown
# Reflexión: ReservaSalas con SDD

*Respuestas de ejemplo de Luis; escribe las tuyas.*

**1. ¿Cuántas líneas de código has escrito tú? ¿Y cuántas has leído?**
Ninguna: lo que he escrito es castellano (la constitución, la especificación, las respuestas de Ana y la tecnología del plan).
He leído sobre todo pruebas, plan y especificación; del código, solo lo justo para entender por qué fallaba una prueba.

**2. ¿Qué artefacto te costó más revisar? ¿En cuál detectaste un error antes de que llegara al código?**
El plan técnico: es largo, mezcla decisiones, modelo de datos y contratos, y comprobarlo contra los cinco principios me costó más que leer la especificación.
Los huecos aparecieron antes del código: la lista de verificación marcó tres pendientes (alcance, antelación y quién cancela una reserva ajena) y el análisis avisó de que ninguna prueba cubría una franja que ya ha empezado; esto último lo dejé anotado.

**3. Si mañana Ana pide que administración pueda cancelar cualquier reserva con un motivo obligatorio, ¿qué fichero abres primero?**
`spec.md`: ahí hablan de administración RF-010 y el criterio 5 de la historia 2, y ahí escribo el motivo obligatorio y una sesión nueva de aclaraciones; Ana lo aprueba antes de seguir.
Después, el plan (el motivo es un dato nuevo y lo compruebo contra el principio 4), `/speckit.converge` e `/speckit.implement`; el código, el último.

**4. ¿Qué habrías hecho distinto con *vibe coding* y cuánto habrías tardado en descubrir, tres meses después, que el límite de antelación seguía en 30 días en algún rincón del código?**
Habría buscado «30» en el código y cambiado lo primero que apareciera; el mensaje de error o una prueba con el número viejo se habrían quedado ahí sin que nadie lo supiera.
No sé cuánto habría tardado, quizá hasta que alguien chocara con el límite. Con SDD lo encontró `converge` el mismo día, porque había una especificación contra la que comparar.
```

## En tres frases

1. El informe de `/speckit.analyze` se lee por las métricas, las incidencias y la cobertura, en ese orden: en el ejemplo canónico no hay incidencias CRITICAL ni HIGH, la cobertura es del 100 % y las tres incidencias menores son reales y se comprueban en los ficheros.
2. Un cambio de límite empieza en la especificación, sigue por el plan y deja que `/speckit.converge` e `/speckit.implement` hagan el resto: el «30» solo sobrevive donde es historial (la aclaración antigua, la nota del 2026-10-07 y las tareas T014 y T019).
3. La reflexión del paso 10 no cuenta líneas de código, cuenta dónde estuvo tu atención: leer pruebas, plan y especificación, y saber qué fichero abrir primero cuando Ana cambia de opinión.

## Siguiente paso

Vuelve al [ejercicio 03](../03-reserva-salas-paso-a-paso.md) y cierra el paso 10 con tu propia reflexión; tus ficheros irán un cambio por delante de [los del ejemplo canónico](03-reserva-salas/README.md). Después continúa con el [ejercicio 04: dinámica de equipo de 20 minutos](../04-dinamica-de-equipo-20-minutos.md) o, para seguir con las herramientas, con el [ejercicio 05](../05-arreglar-una-especificacion-mala.md).

---

⬅️ [Ejercicio 03](../03-reserva-salas-paso-a-paso.md) · 🏠 [Índice de soluciones](README.md)
