# Tareas: PrestamoPortatiles

> [!NOTE]
> Este fichero es la **lista de tareas** (`tasks.md`): el plan técnico troceado en pasos pequeños, ordenados y comprobables, agrupados por historia de usuario. Es el paso 4 del flujo SDD (*Spec-Driven Development*, desarrollo guiado por especificaciones) y se genera con `/speckit.tasks`; después `/speckit.implement` las ejecuta una a una y va marcando las casillas. Esta es la versión corregida tras el primer `/speckit.analyze`, que detectó que RF-009 no tenía ninguna tarea: se añadieron T021, T024 y T025, y la programación diaria del aviso entró en T031 (la lista pasó de 28 a 31 tareas). En un proyecto real vive en `specs/001-prestamo-portatiles/tasks.md`.

**Entrada:** [plan.md](plan.md), [spec.md](spec.md) y [constitution.md](constitution.md) · **Generada:** 2026-11-05

**Pruebas:** sí. El principio 3 de la constitución exige que cada historia tenga pruebas escritas antes que su implementación, así que cada fase de historia empieza por sus pruebas, y estas tienen que **fallar** antes de implementar.

**Organización:** las tareas se agrupan por historia de usuario para que cada historia se pueda implementar, probar y enseñar por separado.

**Qué vas a encontrar**

- [Formato de cada tarea](#formato-de-cada-tarea)
- [Fase 1: Preparación](#fase-1-preparación-infraestructura-compartida-setup)
- [Fase 2: Base compartida](#fase-2-base-compartida-requisitos-bloqueantes-foundational)
- [Fase 3: Historia 1, pedir un equipo y recogerlo](#fase-3-historia-de-usuario-1--pedir-un-equipo-para-unas-fechas-y-recogerlo-prioridad-p1--mvp)
- [Fase 4: Historia 2, devolver o prorrogar](#fase-4-historia-de-usuario-2--devolver-o-prorrogar-prioridad-p2)
- [Fase 5: Historia 3, ver qué hay hoy](#fase-5-historia-de-usuario-3--ver-qué-hay-disponible-hoy-prioridad-p3)
- [Fase 6: Remate](#fase-6-remate-y-aspectos-transversales-polish--cross-cutting-concerns)
- [Dependencias y orden de ejecución](#dependencias-y-orden-de-ejecución)
- [Estrategia de implementación](#estrategia-de-implementación)

## Formato de cada tarea

`- [ ] T000 [P] [HU1] Descripción con ruta de fichero`

- **[P]**: se puede hacer en paralelo con otras tareas [P] de la misma fase (ficheros distintos, sin dependencias pendientes).
- **[HU1] / [HU2] / [HU3]**: historia de usuario a la que pertenece la tarea (solo en las fases de historia).
- **🎯 MVP** (producto mínimo viable): marca la fase que, por sí sola, ya resuelve el problema principal y se puede enseñar.
- **(tarea manual…)**: la tarea solo la puede hacer una persona (una prueba con usuarios, una revisión con lector de pantalla). El asistente de IA no la da por hecha: la deja sin marcar y la marca quien la haga.
- Todas las rutas son relativas a la raíz del proyecto `prestamo-portatiles/`.

## Fase 1: Preparación, infraestructura compartida (Setup)

**Objetivo:** que el proyecto arranque vacío y las pruebas se ejecuten.

- [ ] T001 Crear la estructura de carpetas del plan (`src/prestamo/`, `servicios/`, `rutas/`, `plantillas/`, `estatico/`, `tests/unitarias/`, `tests/integracion/`, `datos/`, `docs/`) con sus `__init__.py`
- [ ] T002 Crear `pyproject.toml` con Python 3.12 y las dependencias fastapi, uvicorn, jinja2 y python-multipart, y pytest y httpx como extra `dev` en `[project.optional-dependencies]`, y `.gitignore` con `.venv/` y `prestamo.db`
- [ ] T003 [P] Crear `src/prestamo/config.py` con la ruta de la base de datos, los datos del servidor de correo, la variable `PRESTAMO_USUARIO_DEV` (vacía en producción) y la lista de correos con rol de Oficina `PRESTAMO_OFICINA`, todo leído del entorno
- [ ] T004 [P] Crear `tests/conftest.py` con una base de datos SQLite temporal por prueba, un reloj simulado que fija «hoy» (las reglas dependen de la fecha) y un envío de correo simulado que guarda los mensajes en una lista; el cliente de pruebas de FastAPI se añade en T011, cuando exista la aplicación

## Fase 2: Base compartida, requisitos bloqueantes (Foundational)

**Objetivo:** lo que necesitan todas las historias. Ninguna historia puede empezar hasta terminar esta fase.

- [ ] T005 Crear `src/prestamo/db.py` con la conexión a SQLite (control manual de transacciones, `isolation_level=None`), la creación de las tablas `equipo`, `persona` y `prestamo` según el modelo de datos del plan, con `persona_id`, `inicio` y `devolucion` obligatorios (principio 4, CE-003), el índice `(equipo_id, inicio)` y la carga de `datos/equipos.sql` al arrancar si la tabla `equipo` está vacía
- [ ] T006 [P] Crear `datos/equipos.sql` con los 14 equipos, según los supuestos de la especificación: PORT-01 a PORT-10, portátil de 14 pulgadas con cargador, y PROY-01 a PROY-04, proyector con cable HDMI
- [ ] T007 [P] Crear `src/prestamo/modelos.py` con las dataclasses `Equipo`, `Persona` y `Prestamo` y sus estados (`portatil`/`proyector`, `empleado`/`oficina`, `reservado`/`entregado`/`cerrado`)
- [ ] T008 [P] Crear `src/prestamo/textos.py` con todos los mensajes de confirmación y de error en castellano; cada error dice qué ha pasado y qué puede hacer la persona
- [ ] T009 Crear `src/prestamo/repositorio.py` con las consultas básicas: listar equipos, buscar o crear persona por correo, insertar, leer y actualizar préstamos (depende de T005 y T007)
- [ ] T010 Crear `src/prestamo/identidad.py`, que lee la cabecera `X-Usuario` (o `PRESTAMO_USUARIO_DEV` en desarrollo) y devuelve la `Persona`, creándola si no existe, con rol `oficina` si su correo está en `PRESTAMO_OFICINA` y `empleado` en caso contrario; sin cabecera ni variable de desarrollo, rechaza la petición (depende de T009)
- [ ] T011 Crear `src/prestamo/app.py` con la aplicación FastAPI, el montaje de `estatico/` con `src/prestamo/estatico/estilo.css`, la configuración de Jinja2 y la plantilla `src/prestamo/plantillas/base.html` (cabecera, navegación y zona de mensajes, con etiquetas y contraste accesibles); añadir a `tests/conftest.py` el cliente de pruebas de FastAPI (depende de T004)

**Punto de control:** `uvicorn prestamo.app:app` arranca y `pytest` ejecuta `conftest.py` sin errores.

## Fase 3: Historia de usuario 1 — Pedir un equipo para unas fechas y recogerlo (Prioridad: P1) 🎯 MVP

**Objetivo:** ver qué equipos de un tipo están libres en unas fechas, pedir uno y que Oficina lo entregue (RF-002 a RF-006).

**Prueba independiente:** pedir un equipo desde cero, entregarlo y comprobar que figura prestado a nombre de la persona y que nadie más puede pedirlo para esas fechas.

### Pruebas de la historia 1 (se escriben primero y tienen que fallar)

- [ ] T012 [P] [HU1] Pruebas unitarias del calendario en `tests/unitarias/test_calendario.py`: días laborables entre dos fechas (de lunes 16 a viernes 27 de noviembre, diez; hasta el lunes 30, once), fin de semana, siguiente día laborable y anterior (el de un lunes es el viernes) (RF-005)
- [ ] T013 [P] [HU1] Pruebas unitarias de las reglas del préstamo en `tests/unitarias/test_reglas_prestamo.py`: solapamiento parcial, total y por un solo día; fechas consecutivas que no chocan; un préstamo cerrado que ya no ocupa el equipo; empezar antes de hoy, empezar o terminar en fin de semana y superar diez días laborables; y que solo Oficina puede entregar (RF-004, RF-005, RF-006, CE-002)
- [ ] T014 [P] [HU1] Prueba de integración en `tests/integracion/test_hu1_pedir_y_recoger.py`: pedir un tipo de equipo para unas fechas y ver los libres, confirmar y ver el préstamo con su responsable y su fecha de devolución, rechazo por equipo ocupado y por límite, entrega por Oficina, persona sin rol de Oficina sin la opción de entregar y con `403` si envía la petición a mano, y dos peticiones simultáneas al mismo equipo y las mismas fechas: solo una se guarda y la otra recibe el `409` por solapamiento, no un error de bloqueo de la base de datos (escenarios 1-7 de la historia, RF-002 a RF-006, CE-002)

### Implementación de la historia 1

- [ ] T015 [P] [HU1] Implementar `src/prestamo/servicios/calendario.py`: la fecha de hoy (que las pruebas pueden fijar), días laborables entre dos fechas, siguiente día laborable y anterior (RF-005)
- [ ] T016 [P] [HU1] Implementar `src/prestamo/servicios/disponibilidad.py`: equipos libres de un tipo en un periodo (RF-002)
- [ ] T017 [HU1] Implementar en `src/prestamo/servicios/prestamos.py` la validación de límites con los mensajes de `textos.py`, la creación del préstamo (comprobación de solapamiento e inserción dentro de una transacción abierta con `BEGIN IMMEDIATE` explícito, así la segunda petición simultánea espera y recibe el rechazo por solapamiento) y la entrega por Oficina (RF-003, RF-004, RF-005, RF-006, CE-002)
- [ ] T018 [HU1] Crear las rutas `GET /`, `POST /prestamos`, `GET /prestamos/{id}` y `POST /prestamos/{id}/entrega` en `src/prestamo/rutas/paginas.py` con las plantillas `src/prestamo/plantillas/disponibilidad.html` (formulario de tipo y fechas, equipos libres y botón «Pedir») y `src/prestamo/plantillas/prestamo.html` (detalle con responsable y fechas, al que se llega desde el mensaje de confirmación, y botón «Marcar como entregado» visible solo para Oficina, con `403` para quien lo envíe a mano) (RF-002 a RF-006)

**Punto de control:** `pytest` pasa con las pruebas T012-T014 y la historia 1 funciona de principio a fin: se puede enseñar a Ana. Es el producto mínimo viable.

## Fase 4: Historia de usuario 2 — Devolver o prorrogar (Prioridad: P2)

**Objetivo:** que Oficina registre las devoluciones, que la persona responsable pueda prorrogar una vez y que reciba un aviso la víspera de la devolución (RF-004, RF-005, RF-007, RF-008, RF-009).

**Prueba independiente:** registrar la devolución de un préstamo entregado y ver el equipo libre; pedir una prórroga y ver la fecha nueva.

### Pruebas de la historia 2 (se escriben primero y tienen que fallar)

- [ ] T019 [P] [HU2] Pruebas unitarias de la prórroga en `tests/unitarias/test_prorroga.py`: la nueva fecha cuando se acepta; rechazada la segunda vez, al pasar del máximo de días laborables en total, si el préstamo no está entregado o está vencido, si la pide quien no es la persona responsable o si otro préstamo ocupa el equipo justo después (el mensaje dice hasta cuándo está libre) (RF-004, RF-005, RF-008)
- [ ] T020 [P] [HU2] Prueba de integración en `tests/integracion/test_hu2_devolver_prorrogar.py`: devolución por Oficina y equipo libre, cierre de un préstamo reservado que nadie recogió, prórroga aceptada con su fecha nueva, prórroga rechazada por segunda vez, por choque con otro préstamo o por préstamo vencido, y persona sin rol de Oficina sin la opción de registrar la devolución y con `403` si la envía a mano, igual que quien prorroga un préstamo ajeno (escenarios 1-5 de la historia, RF-004, RF-005, RF-007, RF-008)
- [ ] T021 [P] [HU2] Pruebas unitarias de los avisos en `tests/unitarias/test_avisos.py`: se avisa el día laborable anterior a la devolución (si cae en lunes, el viernes) a los préstamos reservados y entregados, no a los cerrados, una sola vez por préstamo y de nuevo si se prorroga, se reintenta si el envío falló, se avisa el mismo día de la devolución si el préstamo se pidió después de las 08:00 de la víspera, y el correo lleva el equipo, la fecha y el enlace a la página del préstamo (RF-009, CE-004)

### Implementación de la historia 2

- [ ] T022 [HU2] Implementar en `src/prestamo/servicios/prestamos.py` la devolución (cierra el préstamo y deja el equipo libre, también si estaba solo reservado) y la prórroga (solo en un préstamo entregado, una sola vez, dentro de los límites y mientras el equipo esté libre, comprobando el solapamiento sin contar el propio préstamo y dentro de una transacción abierta con `BEGIN IMMEDIATE`; vuelve a activar el aviso), con los permisos (la devolución, solo Oficina; la prórroga, solo la persona responsable) y los mensajes de `textos.py` (RF-004, RF-005, RF-007, RF-008)
- [ ] T023 [HU2] Crear las rutas `POST /prestamos/{id}/devolucion` y `POST /prestamos/{id}/prorroga` en `src/prestamo/rutas/paginas.py` y completar `src/prestamo/plantillas/prestamo.html` con el botón «Registrar devolución» (solo Oficina) y el formulario de prórroga (solo la persona responsable), y devolver `403` a quien envíe esas peticiones sin tener permiso (RF-007, RF-008)
- [ ] T024 [P] [HU2] Implementar `src/prestamo/servicios/correo.py`: envío por el servidor corporativo con asunto y cuerpo en castellano, y la versión simulada para pruebas (RF-009)
- [ ] T025 [HU2] Implementar `src/prestamo/avisos.py`, el programa que se ejecuta con `python -m prestamo.avisos`: busca los préstamos reservados o entregados cuya devolución es el siguiente día laborable (o hoy, si todavía no se les ha avisado), envía el correo a la persona responsable, con el equipo, la fecha y el enlace a la página del préstamo, y marca el aviso como enviado (depende de T024) (RF-009, CE-004)

**Punto de control:** `pytest` pasa con las pruebas T019-T021 sin romper las de la historia 1; las historias 1 y 2 funcionan juntas y por separado.

## Fase 5: Historia de usuario 3 — Ver qué hay disponible hoy (Prioridad: P3)

**Objetivo:** que cualquier persona vea los 14 equipos con su estado de hoy y, en los que faltan, quién los tiene y cuándo vuelven (RF-001).

**Prueba independiente:** crear préstamos de varias personas y comprobar que «Hoy» muestra cada equipo con su estado, su responsable y su fecha de devolución.

### Pruebas de la historia 3 (se escriben primero y tienen que fallar)

- [ ] T026 [P] [HU3] Prueba de integración en `tests/integracion/test_hu3_hoy.py`: los 14 equipos con su estado de hoy, los prestados con su responsable y su fecha de devolución, un préstamo vencido marcado como «vencido» (también si solo estaba reservado, y si el mismo equipo tiene otro préstamo que empieza hoy, la fila muestra el vencido) y un equipo devuelto hoy, libre (escenarios 1-3 de la historia, RF-001)

### Implementación de la historia 3

- [ ] T027 [HU3] Añadir a `src/prestamo/servicios/disponibilidad.py` el estado de hoy de cada equipo (libre, prestado o vencido, con responsable y fecha de devolución) y crear la ruta `GET /hoy` en `src/prestamo/rutas/paginas.py` con la plantilla `src/prestamo/plantillas/hoy.html`: una fila por equipo y el enlace para prorrogar solo en los préstamos entregados de quien mira (RF-001)

**Punto de control:** `pytest` pasa con la prueba T026 sin romper las anteriores y las tres historias funcionan de forma independiente.

## Fase 6: Remate y aspectos transversales (Polish & Cross-Cutting Concerns)

**Objetivo:** comprobación de los criterios de éxito, accesibilidad, revisión final contra la constitución y despliegue.

- [ ] T028 [P] Verificar CE-001 con una sesión de prueba con 5 personas de distintos equipos siguiendo `specs/001-prestamo-portatiles/quickstart.md`; anotar tiempos y resultado en `docs/prueba-con-usuarios.md` (tarea manual: la hace una persona; el asistente la deja sin marcar)
- [ ] T029 [P] Revisar todas las plantillas de `src/prestamo/plantillas/` con teclado y lector de pantalla, como pide la restricción de accesibilidad de la constitución: etiquetas en todos los campos, botones con texto, mensajes de error junto al campo (tarea manual: la hace una persona; el asistente la deja sin marcar)
- [ ] T030 Revisar el código contra los cuatro principios de `.specify/memory/constitution.md` y anotar el resultado en `docs/revision-constitucion.md`; comprobar que ningún préstamo puede quedar sin responsable o sin fecha (CE-003) y corregir cualquier desviación antes de entregar
- [ ] T031 Crear `README.md` con qué es la aplicación, el arranque rápido del plan, dónde está la especificación, la configuración del despliegue interno (servidor de correo, acceso corporativo, `PRESTAMO_USUARIO_DEV` vacía y la lista `PRESTAMO_OFICINA`) y la programación del aviso: una entrada en el programador de tareas del servidor que ejecute `python -m prestamo.avisos` de lunes a viernes a las 08:00 (RF-009, CE-004)

## Dependencias y orden de ejecución

- **Fase 1 → Fase 2 → historias:** ninguna historia empieza hasta que la base compartida está lista.
- **Historias:** se hacen en orden de prioridad (HU1 → HU2 → HU3). Son independientes entre sí: HU2 y HU3 usan los préstamos que crea HU1, pero sus pruebas crean sus propios datos.
- **Dentro de cada historia:** pruebas → servicios → rutas y páginas. Las pruebas tienen que fallar antes de implementar y pasar al terminar.
- **Remate:** después de las tres historias. T028 y T029 las hace una persona y pueden ir en paralelo con T030 y T031.

## Ejemplo en paralelo: historia 1

Las tres pruebas de la historia 1 tocan ficheros distintos y no dependen entre sí, así que se pueden escribir a la vez:

```text
T012 tests/unitarias/test_calendario.py
T013 tests/unitarias/test_reglas_prestamo.py
T014 tests/integracion/test_hu1_pedir_y_recoger.py
```

Después, T015 y T016 también pueden ir en paralelo; T017 va detrás de ellas y T018, la última, usa lo que dejan todas.

## Estrategia de implementación

1. **Primero el producto mínimo viable:** fases 1, 2 y 3. Parar, ejecutar `pytest`, enseñárselo a Ana y recoger cambios en la especificación.
2. **Entrega incremental:** añadir HU2, probar y enseñar; añadir HU3, probar y enseñar. Cada historia suma valor sin romper las anteriores.
3. **Si algo no cuadra:** no se parchea el código. Ana decide el cambio y lo pide; Luis lo escribe en `spec.md`, y Ana relee el texto nuevo y lo aprueba. Después Luis actualiza el plan, deja que `/speckit.converge` añada a este fichero las tareas que faltan y las ejecuta con `/speckit.implement` (es el paso 9 del [ejercicio 03](../../../03-reserva-salas-paso-a-paso.md)). No se relanza `/speckit.tasks`, que rehace la lista entera.

Resumen: 31 tareas (4 de preparación, 7 de base compartida, 7 de HU1, 7 de HU2, 2 de HU3 y 4 de remate), 17 de ellas paralelizables. Cada RF de la especificación aparece en al menos una tarea; los cuatro criterios de éxito se comprueban en las pruebas de HU1 (CE-002) y de HU2 (CE-004), en la revisión de T030 (CE-003) y en la sesión de T028 (CE-001).

---

⬅️ [Anterior: Plan técnico](plan.md) · 🏠 [Índice del ejemplo](README.md) · ➡️ [Siguiente: Autoevaluación](autoevaluacion.md)
