# Plantilla: tareas

> [!TIP]
> Este fichero es la lista de trabajo: el plan troceado en tareas pequeñas, ordenadas y comprobables, agrupadas por historia de usuario. La ejecuta quien construye (o el asistente de IA, tarea a tarea); negocio puede seguir el avance por los puntos de control. Copia este fichero junto al plan, renómbralo `tasks.md`, rellena los corchetes y borra este aviso; el título pasa a ser `# Tareas: <nombre de la funcionalidad>`.
>
> Con Spec Kit, `/speckit.tasks` genera su equivalente a partir de `plan.md` y `spec.md`, y `/speckit.implement` va marcando cada tarea como hecha. Esta plantilla sirve para trabajar sin herramientas o para revisar la lista que genere el asistente de IA.
>
> Una buena tarea cabe en una línea, toca un fichero concreto y se puede dar por terminada con un sí o un no.

<!--
  Qué es: la lista ordenada y troceada de todo lo que hay que hacer para construir lo que dice el plan, agrupada por historia de usuario.
  Para quién: la ejecuta quien construye (o el asistente de IA, tarea a tarea); la revisa quien quiera saber cuánto queda. Negocio puede leer los títulos de fase y los puntos de control.
  Consejo: si una tarea no cabe en una línea, son dos tareas.
-->

**Entrada:** [plan.md y spec.md de `specs/001-reserva-salas/`] · **Requisitos previos:** [plan.md (obligatorio) y spec.md (para las historias)] · **Pruebas:** [sí: la constitución exige al menos una prueba por funcionalidad] · **Organización:** [por historia de usuario, para construir y probar cada una por separado]

## Formato: `[ID] [P?] [Historia] Descripción`
<!-- Qué se escribe: nada que rellenar; es la leyenda. Para quién: quien lea o escriba tareas. Consejo: respeta el formato aunque trabajes sin herramientas; así cualquiera entiende la lista. -->

- **T001, T002…**: identificador único y correlativo.
- **[P]**: se puede hacer en paralelo con otras tareas [P] de la misma fase (ficheros distintos, sin dependencias entre sí).
- **[HU1], [HU2], [HU3]**: historia de usuario a la que pertenece (solo en las fases de historia).
- **🎯 MVP** (*Minimum Viable Product*, producto mínimo viable): marca la primera historia completa, lo más pequeño que ya se puede enseñar y usar.
- La descripción nombra el fichero que toca. Al terminar, `[ ]` pasa a `[X]`.

## Convenciones de rutas
<!-- Dónde vive el código según el plan. Para quién: quien escriba las rutas de cada tarea. Consejo: cópialo de «Estructura del proyecto» del plan. -->

- [Un solo proyecto: código en `src/reservasalas/` y pruebas en `tests/`, en la raíz del repositorio.]

## Fase 1: Preparación (infraestructura compartida)
<!-- Qué se escribe: crear la estructura, instalar dependencias, configurar herramientas. Para quién: quien construye. Consejo: 2-4 tareas; si hay más, algo sobra. -->

- [ ] T001 [Crear la estructura de carpetas del plan: `src/reservasalas/` (con `servicios/`, `rutas/` y `plantillas/`) y `tests/` (con `unitarias/`, `contrato/` e `integracion/`)]
- [ ] T002 [Iniciar el proyecto Python 3.12 con fastapi, uvicorn y jinja2, y en el grupo de desarrollo pytest y httpx, en `pyproject.toml`]
- [ ] T003 [P] [Preparar `tests/conftest.py`: base de datos temporal por prueba, cliente de pruebas y correo simulado]

## Fase 2: Base compartida (requisitos bloqueantes)
<!-- Qué se escribe: lo que *todas* las historias necesitan antes de empezar: modelo de datos, base de datos, datos iniciales. Para quién: quien construye. Consejo: aquí no va nada que pertenezca a una sola historia. -->

- [ ] T004 [Crear la base de datos SQLite y su esquema en `src/reservasalas/db.py`]
- [ ] T005 [P] [Modelos Sala, Persona y Reserva en `src/reservasalas/modelos.py`]
- [ ] T006 [P] [Mensajes de confirmación y de error en castellano en `src/reservasalas/textos.py`]
- [ ] T007 [Cargar las 12 salas iniciales (Mediterráneo, Cantábrico, Atlántico…) desde `datos/salas.sql` al arrancar, en `src/reservasalas/db.py` (depende de T004)]
- [ ] T008 [Crear la aplicación y la plantilla base en `src/reservasalas/app.py` y `src/reservasalas/plantillas/base.html`]

**Punto de control:** [la base está lista; las historias pueden empezar, incluso en paralelo]

## Fase 3: Historia de usuario 1 - [Reservar una sala] (Prioridad: P1) 🎯 MVP
<!--
  Qué se escribe: todo lo necesario para que la historia P1 funcione *sola*: primero sus pruebas, luego la implementación.
  Para quién: quien construye; negocio puede probar al llegar al punto de control.
  Consejo: cuando esta fase termina ya tienes algo que enseñar. Enséñalo antes de seguir.
-->

**Objetivo:** [ver salas libres en una franja, elegir una y confirmar] · **Prueba independiente:** [reservar la sala Mediterráneo el jueves de 10:00 a 11:00 y comprobar que aparece ocupada]

### Pruebas de la historia 1
<!-- Se escriben *antes* de implementar y tienen que fallar al principio. Es la forma de saber que prueban algo. -->

- [ ] T009 [P] [HU1] [Prueba de contrato de «listar disponibilidad» en `tests/contrato/test_api_salas.py`]
- [ ] T010 [P] [HU1] [Prueba de integración «reservar sala libre», «rechazar solapamiento» y «se envía el correo de confirmación» (RF-003, RF-005, RF-011) en `tests/integracion/test_hu1_reservar.py`]

### Implementación de la historia 1
<!-- Orden habitual: modelos (si la historia necesita alguno nuevo), luego servicios, luego rutas y pantallas, luego mensajes de error. -->

- [ ] T011 [HU1] [Servicio de disponibilidad y detección de solapamientos en `src/reservasalas/servicios/reservas.py`]
- [ ] T012 [P] [HU1] [Envío del correo de confirmación en `src/reservasalas/servicios/correo.py`, con versión simulada para pruebas (RF-011)]
- [ ] T013 [HU1] [Rutas «listar disponibilidad» y «crear reserva» en `src/reservasalas/rutas/api.py` (depende de T011 y T012)]
- [ ] T014 [HU1] [Página de disponibilidad y reserva en `src/reservasalas/rutas/paginas.py` y `src/reservasalas/plantillas/reservar.html`]
- [ ] T015 [HU1] [Mensajes de rechazo: solapamiento, fuera de horario, más de 4 horas, sala en mantenimiento (RF-005, RF-006, RF-007) en `src/reservasalas/servicios/reservas.py` y `src/reservasalas/textos.py`]

**Punto de control:** [la historia 1 funciona y se puede probar sola]

## Fase 4: Historia de usuario 2 - [Cancelar o modificar mi reserva] (Prioridad: P2)
<!-- Misma estructura que la fase 3. Puede apoyarse en la historia 1, pero tiene que poder probarse por separado. -->

**Objetivo:** [...] · **Prueba independiente:** [...]

### Pruebas de la historia 2
<!-- Primero las pruebas, otra vez. -->

- [ ] T016 [P] [HU2] [Prueba de integración «cancelar mi reserva», «modificar mi reserva» y «no poder cancelar una ajena» (RF-010) en `tests/integracion/test_hu2_cancelar_modificar.py`]

### Implementación de la historia 2
<!-- Ficheros concretos. Si una tarea toca el mismo fichero que otra, no lleva [P]. -->

- [ ] T017 [HU2] [Ruta «cancelar reserva» en `src/reservasalas/rutas/api.py`, con la comprobación de permisos: solo la persona responsable o administración (RF-010)]
- [ ] T018 [HU2] [Ruta «modificar reserva» en `src/reservasalas/rutas/api.py`: valida límites y solapamiento sin contar la propia reserva]

**Punto de control:** [las historias 1 y 2 funcionan por separado]

## Fase 5: Historia de usuario 3 - [Ver mis reservas y las de hoy en cada sala] (Prioridad: P3)
<!-- Las P3 van al final: si se acaba el tiempo, se quedan fuera sin romper nada. -->

**Objetivo:** [...] · **Prueba independiente:** [...]

### Pruebas de la historia 3
<!-- Una prueba por criterio de aceptación es una buena medida. -->

- [ ] T019 [P] [HU3] [...]

### Implementación de la historia 3
<!-- Si la historia 3 necesita algo de la 1 o la 2, dilo en la tarea («depende de T013»). -->

- [ ] T020 [HU3] [...]

**Punto de control:** [todas las historias funcionan por separado]

## Fase 6: Remate y aspectos transversales
<!-- Qué se escribe: lo que afecta a varias historias o a ningún recorrido concreto (administración), documentación, limpieza, revisión contra la constitución. Para quién: quien construye. Consejo: incluye siempre «revisar contra la constitución» como última tarea. -->

- [ ] T021 [P] [Ruta y botón «marcar sala en mantenimiento», solo para administración, en `src/reservasalas/rutas/api.py` y `src/reservasalas/plantillas/reservar.html`, con su prueba en `tests/contrato/test_api_salas.py` (RF-009)]
- [ ] T022 [P] [Escribir `README.md` con la guía de arranque rápido del plan]
- [ ] T023 [Revisar el código contra los cinco principios de la constitución]
- [ ] T024 [Ejecutar todas las pruebas y limpiar código sin uso]

## Dependencias y orden de ejecución
<!-- Qué se escribe: qué bloquea a qué. Para quién: quien reparta el trabajo. Consejo: en un proyecto pequeño basta con esta lista. -->

- Fase 1 → Fase 2 → historias (fases 3, 4 y 5) → Fase 6.
- [Las historias pueden hacerse en paralelo si hay varias personas, o en orden P1 → P2 → P3 si hay una.]
- [Dentro de cada historia: pruebas, servicios, rutas y pantallas, mensajes, en ese orden.]

## Estrategia de implementación
<!-- Qué se escribe: por dónde se empieza y dónde se para a enseñar. Para quién: quien construye y quien espera resultados. Consejo: primero el MVP (fases 1 a 3), se valida, y solo entonces se sigue. -->

1. [Fases 1 y 2: preparación y base.]
2. [Fase 3: historia 1. *Parar*, probar y enseñársela a la responsable de Oficina.]
3. [Fases 4 y 5, de una en una, probando cada una.]
4. [Fase 6: remate.]

## Notas
<!-- Avisos para quien ejecute la lista. -->

- [Las tareas se marcan `[X]` al terminar; con Spec Kit lo hace el asistente de IA.]
- [Si una tarea revela que la especificación estaba mal, se corrige la especificación y se regeneran plan y tareas: no se parchea el código.]

<!-- Volver al índice de plantillas: abre README.md en esta misma carpeta (ejercicios/plantillas/README.md). -->
