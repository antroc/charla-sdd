# Plantilla: tareas

> *Qué es: la lista ordenada y troceada de todo lo que hay que hacer para construir lo que dice el plan, agrupada por historia de usuario. · Para quién: la ejecuta quien construye (o el asistente de IA, tarea a tarea) y la revisa quien quiera saber cuánto queda; negocio puede seguir el avance por los títulos de fase y los puntos de control. · Consejo: si una tarea no cabe en una línea, son dos tareas.*

> [!TIP]
> Copia este fichero junto al plan, renómbralo `tasks.md`, rellena los corchetes y borra este aviso; el título pasa a ser `# Tareas: [nombre de la funcionalidad]`.
>
> Con Spec Kit, `/speckit.tasks` genera su equivalente a partir de `plan.md` y `spec.md`, y `/speckit.implement` va marcando cada tarea como hecha. Esta plantilla sirve para trabajar sin herramientas o para revisar la lista que genere el asistente de IA.
>
> Una buena tarea cabe en una línea, toca un fichero concreto y se puede dar por terminada con un sí o un no.
>
> Los ejemplos entre corchetes son tareas de la [solución del ejercicio 03](../soluciones/03-reserva-salas/tasks.md), recortadas y con su mismo número; por eso la numeración da saltos. En tu lista, numera seguido (T001, T002, T003…). Las ayudas de cada sección van en cursiva bajo su título; bórralas cuando el documento esté listo.

**Entrada:** [plan.md y spec.md de `specs/001-reserva-salas/`] · **Requisitos previos:** [plan.md (obligatorio) y spec.md (para las historias)] · **Pruebas:** [sí: la constitución exige al menos una prueba por funcionalidad] · **Organización:** [por historia de usuario, para construir y probar cada una por separado]

## Formato: `[ID] [P?] [Historia] Descripción`

> *Qué se escribe: nada que rellenar; es la leyenda. · Para quién: quien lea o escriba tareas. · Consejo: respeta el formato aunque trabajes sin herramientas; así cualquiera entiende la lista.*

- **T001, T002…**: identificador único y correlativo.
- **[P]**: se puede hacer en paralelo con otras tareas [P] de la misma fase (ficheros distintos, sin dependencias entre sí).
- **[HU1], [HU2], [HU3]**: historia de usuario a la que pertenece (solo en las fases de historia).
- **🎯 MVP** (*Minimum Viable Product*, producto mínimo viable): marca la primera historia completa, lo más pequeño que ya se puede enseñar y usar.
- La descripción nombra el fichero que toca. Al terminar, `[ ]` pasa a `[X]`.
- **(tarea manual: …)**: al final de una tarea que solo puede hacer una persona (una prueba con usuarios, una revisión con lector de pantalla). El asistente de IA la deja sin marcar; la marca quien la haga.

## Convenciones de rutas

> *Qué se escribe: dónde vive el código según el plan. · Para quién: quien escriba las rutas de cada tarea. · Consejo: cópialo de «Estructura del proyecto» del plan.*

- [Un solo proyecto: código en `src/reservasalas/` y pruebas en `tests/`, en la raíz del repositorio.]

## Fase 1: Preparación (infraestructura compartida)

> *Qué se escribe: crear la estructura, instalar dependencias y configurar herramientas. · Para quién: quien construye. · Consejo: pocas tareas (en la solución del ejercicio 03, cinco); si salen muchas más, algo sobra.*

- [ ] T001 [Crear la estructura de carpetas del plan: `src/reservasalas/` (con `servicios/`, `rutas/` y `plantillas/`), `tests/` (con `unitarias/`, `contrato/` e `integracion/`) y `datos/`]
- [ ] T002 [Crear `pyproject.toml` con Python 3.12 y las dependencias fastapi, uvicorn y jinja2, con pytest y httpx para desarrollo]
- [ ] T004 [P] [Crear `tests/conftest.py` con una base de datos temporal por prueba y un correo simulado; el cliente de pruebas se añade en T012, cuando ya exista la aplicación]
- [ ] T005 [P] [Crear `README.md` con la guía de arranque rápido del plan]

## Fase 2: Base compartida (requisitos bloqueantes)

> *Qué se escribe: lo que todas las historias necesitan antes de empezar: modelo de datos, base de datos y datos iniciales. · Para quién: quien construye. · Consejo: aquí no va nada que pertenezca a una sola historia.*

- [ ] T006 [Crear `src/reservasalas/db.py` con la conexión a SQLite, las tablas `sala`, `persona` y `reserva` según el modelo de datos del plan y la carga de `datos/salas.sql` al arrancar]
- [ ] T007 [P] [Crear `datos/salas.sql` con las 12 salas (Mediterráneo, Cantábrico, Atlántico…), su planta y su aforo]
- [ ] T008 [P] [Crear `src/reservasalas/modelos.py` con `Sala`, `Persona` y `Reserva` y sus estados]
- [ ] T009 [P] [Crear `src/reservasalas/textos.py` con los mensajes de confirmación y de error en castellano; cada error dice qué ha pasado y qué puede hacer la persona]
- [ ] T012 [Crear `src/reservasalas/app.py` con la aplicación y la plantilla `src/reservasalas/plantillas/base.html`; añadir a `tests/conftest.py` el cliente de pruebas (depende de T004)]

**Punto de control:** [la base está lista; las historias pueden empezar, incluso en paralelo]

## Fase 3: Historia de usuario 1 - [Reservar una sala] (Prioridad: P1) 🎯 MVP

> *Qué se escribe: todo lo necesario para que la historia P1 funcione sola: primero sus pruebas, luego la implementación. · Para quién: quien construye; negocio puede probar al llegar al punto de control. · Consejo: cuando esta fase termina ya tienes algo que enseñar; enséñalo antes de seguir.*

**Objetivo:** [ver salas libres en una franja, elegir una y confirmar] · **Prueba independiente:** [reservar la sala Mediterráneo el jueves de 10:00 a 11:00 y comprobar que aparece ocupada]

### Pruebas de la historia 1

> *Se escriben antes de implementar y tienen que fallar al principio: es la forma de saber que prueban algo.*

- [ ] T013 [P] [HU1] [Pruebas unitarias de solapamiento en `tests/unitarias/test_solapamiento.py`: solapamiento parcial, total y franjas consecutivas que no chocan (RF-005, CE-002)]
- [ ] T014 [P] [HU1] [Pruebas unitarias de límites en `tests/unitarias/test_limites.py`: antes de 08:00, después de 20:00, más de 4 horas y fin anterior al inicio (RF-006)]
- [ ] T015 [P] [HU1] [Pruebas de contrato de «listar salas y disponibilidad» en `tests/contrato/test_api_salas.py`, con la sala en mantenimiento marcada y no libre (RF-001, RF-002, RF-007)]
- [ ] T016 [P] [HU1] [Pruebas de contrato de «crear reserva» en `tests/contrato/test_api_reservas.py`: confirmación con responsable y rechazo por solapamiento, por cada límite y por mantenimiento (RF-003 a RF-007)]
- [ ] T017 [P] [HU1] [Prueba de integración del recorrido completo en `tests/integracion/test_hu1_reservar.py`: consultar, reservar Mediterráneo, ver la sala ocupada y comprobar que se ha enviado el correo de confirmación (RF-011)]

### Implementación de la historia 1

> *Orden habitual: modelos (si la historia necesita alguno nuevo), servicios, rutas, páginas y, al final, ejecutar las pruebas de la historia.*

- [ ] T018 [HU1] [Implementar `src/reservasalas/servicios/disponibilidad.py`: salas libres en una franja, marcando las ocupadas y las que están en mantenimiento (RF-001, RF-002, RF-007)]
- [ ] T019 [HU1] [Implementar en `src/reservasalas/servicios/reservas.py` la validación de límites (horario 08:00-20:00, máximo 4 horas, fin futuro) con los mensajes de `textos.py` (RF-006)]
- [ ] T020 [HU1] [Implementar en `src/reservasalas/servicios/reservas.py` la creación de reserva: comprobación de solapamiento e inserción en una sola transacción, y rechazo si la sala está en mantenimiento (RF-003, RF-005, RF-007, CE-002)]
- [ ] T021 [P] [HU1] [Implementar `src/reservasalas/servicios/correo.py`: envío por el servidor corporativo y versión simulada para pruebas (RF-011)]
- [ ] T022 [HU1] [Implementar las rutas «listar disponibilidad» y «crear reserva» en `src/reservasalas/rutas/api.py` según los contratos del plan]
- [ ] T023 [HU1] [Crear la página de disponibilidad y reserva en `src/reservasalas/rutas/paginas.py` con la plantilla `src/reservasalas/plantillas/disponibilidad.html`: formulario de fecha y franja, lista de salas y mensaje de confirmación o de error (RF-001 a RF-007)]
- [ ] T024 [HU1] [Ejecutar `pytest` y comprobar que pasan las pruebas T013-T017; revisar que todos los mensajes salen de `src/reservasalas/textos.py`]

**Punto de control:** [la historia 1 funciona y se puede probar sola]

## Fase 4: Historia de usuario 2 - [Cancelar o modificar mi reserva] (Prioridad: P2)

> *Consejo: misma estructura que la fase 3. Puede apoyarse en la historia 1, pero tiene que poder probarse por separado.*

**Objetivo:** [...] · **Prueba independiente:** [...]

### Pruebas de la historia 2

> *Primero las pruebas, otra vez.*

- [ ] T025 [P] [HU2] [Pruebas unitarias de permisos en `tests/unitarias/test_permisos.py`: la responsable puede, otra persona no, administración sí (RF-010)]
- [ ] T027 [P] [HU2] [Prueba de integración en `tests/integracion/test_hu2_cancelar_modificar.py`: reservar, modificar, cancelar y comprobar la disponibilidad y los correos en cada paso (RF-008, RF-011)]
- [ ] [...]

### Implementación de la historia 2

> *Consejo: ficheros concretos. Si una tarea toca el mismo fichero que otra, no lleva [P].*

- [ ] T028 [HU2] [Implementar en `src/reservasalas/servicios/reservas.py` la comprobación de permisos: persona responsable o administración (RF-010)]
- [ ] T029 [HU2] [Implementar en `src/reservasalas/servicios/reservas.py` cancelar y modificar (validar límites y solapamiento sin contar la propia reserva; si falla, no cambiar nada), con su correo (RF-008, RF-011)]
- [ ] [...]

**Punto de control:** [las historias 1 y 2 funcionan por separado]

## Fase 5: Historia de usuario 3 - [Ver mis reservas y las de hoy en cada sala] (Prioridad: P3)

> *Consejo: las P3 van al final; si se acaba el tiempo, se quedan fuera sin romper nada.*

**Objetivo:** [...] · **Prueba independiente:** [...]

### Pruebas de la historia 3

> *Consejo: una prueba por criterio de aceptación es una buena medida.*

- [ ] T033 [P] [HU3] [...]

### Implementación de la historia 3

> *Consejo: si la historia 3 necesita algo de la 1 o la 2, dilo en la tarea («depende de T020»).*

- [ ] T035 [HU3] [...]

**Punto de control:** [todas las historias funcionan por separado]

## Fase 6: Remate y aspectos transversales

> *Qué se escribe: lo que afecta a varias historias o a ningún recorrido concreto (administración), documentación, limpieza y revisión contra la constitución. · Para quién: quien construye. · Consejo: incluye siempre una revisión contra la constitución antes de entregar, y separa la prueba de la implementación también aquí.*

- [ ] T040 [Prueba de contrato de «marcar sala en mantenimiento» en `tests/contrato/test_api_salas.py`: administración marca y desmarca una sala, y una persona sin permisos recibe un rechazo (RF-009). Se escribe primero y tiene que fallar]
- [ ] T041 [Ruta y botón «marcar sala en mantenimiento», solo para administración, en `src/reservasalas/rutas/api.py` y `src/reservasalas/plantillas/disponibilidad.html` (RF-009)]
- [ ] T044 [P] [Verificar CE-001 y CE-003 con una sesión de prueba con 10 personas y anotar tiempos y resultado] (tarea manual: la hace una persona; el asistente la deja sin marcar)
- [ ] T046 [Revisar el código contra los cinco principios de la constitución y anotar el resultado]
- [ ] [...]

## Dependencias y orden de ejecución

> *Qué se escribe: qué bloquea a qué. · Para quién: quien reparta el trabajo. · Consejo: en un proyecto pequeño basta con esta lista.*

- Fase 1 → Fase 2 → historias (fases 3, 4 y 5) → Fase 6.
- [Las historias pueden hacerse en paralelo si hay varias personas, o en orden P1 → P2 → P3 si hay una.]
- [Dentro de cada historia: pruebas, servicios, rutas, páginas y ejecución de las pruebas, en ese orden.]

## Estrategia de implementación

> *Qué se escribe: por dónde se empieza y dónde se para a enseñar. · Para quién: quien construye y quien espera resultados. · Consejo: primero el MVP (fases 1 a 3), se valida, y solo entonces se sigue.*

1. [Fases 1 y 2: preparación y base.]
2. [Fase 3: historia 1. *Parar*, probar y enseñársela a la responsable de Oficina.]
3. [Fases 4 y 5, de una en una, probando cada una.]
4. [Fase 6: remate.]

## Notas

> *Qué se escribe: avisos para quien ejecute la lista.*

- [Las tareas se marcan `[X]` al terminar; con Spec Kit lo hace el asistente de IA, salvo las tareas manuales, que marca quien las hace.]
- [Si una tarea revela que la especificación estaba mal, no se parchea el código. Quien encarga decide el cambio y lo pide; quien construye lo escribe en la especificación, y quien encarga relee el texto nuevo y lo aprueba. Después se actualiza el plan y, con Spec Kit, `/speckit.converge` añade a esta lista las tareas que faltan y `/speckit.implement` las ejecuta; no se relanza `/speckit.tasks`, que rehace la lista entera.]

> *Volver al [índice de plantillas](README.md). Borra esta línea cuando copies la plantilla.*
