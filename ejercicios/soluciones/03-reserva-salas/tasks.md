# Tareas: ReservaSalas

> [!NOTE]
> Este fichero es la **lista de tareas** (`tasks.md`): el plan técnico troceado en pasos pequeños, ordenados y comprobables, agrupados por historia de usuario. Es el paso 4 del flujo SDD (*Spec-Driven Development*, desarrollo guiado por especificaciones) y se genera con `/speckit.tasks`; después `/speckit.implement` las ejecuta una a una y va marcando las casillas. En un proyecto real vive en `specs/001-reserva-salas/tasks.md`.

**Entrada:** [plan.md](plan.md), [spec.md](spec.md) y [constitution.md](constitution.md) · **Generada:** 2026-10-09

**Pruebas:** sí. El principio 3 de la constitución exige que cada historia tenga pruebas escritas antes que su implementación, así que cada fase de historia empieza por sus pruebas, y estas tienen que **fallar** antes de implementar.

**Organización:** las tareas se agrupan por historia de usuario para que cada historia se pueda implementar, probar y enseñar por separado.

**Qué vas a encontrar**

- [Fase 1: Preparación](#fase-1-preparación-infraestructura-compartida-setup)
- [Fase 2: Base compartida](#fase-2-base-compartida-requisitos-bloqueantes-foundational)
- [Fase 3: Historia 1, reservar una sala](#fase-3-historia-de-usuario-1--reservar-una-sala-prioridad-p1--mvp)
- [Fase 4: Historia 2, cancelar o modificar](#fase-4-historia-de-usuario-2--cancelar-o-modificar-mi-reserva-prioridad-p2)
- [Fase 5: Historia 3, ver mis reservas y las de hoy](#fase-5-historia-de-usuario-3--ver-mis-reservas-y-las-de-hoy-en-cada-sala-prioridad-p3)
- [Fase 6: Remate](#fase-6-remate-y-aspectos-transversales-polish--cross-cutting-concerns)
- [Dependencias y orden de ejecución](#dependencias-y-orden-de-ejecución)
- [Estrategia de implementación](#estrategia-de-implementación)

## Formato de cada tarea

`- [ ] T000 [P] [HU1] Descripción con ruta de fichero`

- **[P]**: se puede hacer en paralelo con otras tareas [P] de la misma fase (ficheros distintos, sin dependencias pendientes).
- **[HU1] / [HU2] / [HU3]**: historia de usuario a la que pertenece la tarea (solo en las fases de historia).
- **🎯 MVP** (producto mínimo viable): marca la fase que, por sí sola, ya resuelve el problema principal y se puede enseñar.
- **(tarea manual…)**: la tarea solo la puede hacer una persona (una prueba con usuarios, una revisión con lector de pantalla). El asistente de IA no la da por hecha: la deja sin marcar y la marca quien la haga.
- Todas las rutas son relativas a la raíz del proyecto `reserva-salas/`.

## Fase 1: Preparación, infraestructura compartida (Setup)

**Objetivo:** que el proyecto arranque vacío y las pruebas se ejecuten.

- [ ] T001 Crear la estructura de carpetas del plan (`src/reservasalas/`, `servicios/`, `rutas/`, `plantillas/`, `estatico/`, `tests/unitarias/`, `tests/contrato/`, `tests/integracion/`, `datos/`, `docs/`) con sus `__init__.py`
- [ ] T002 Crear `pyproject.toml` con Python 3.12 y las dependencias fastapi, uvicorn, jinja2 y python-multipart, y pytest y httpx como extra `dev` en `[project.optional-dependencies]`
- [ ] T003 [P] Crear `src/reservasalas/config.py` con la ruta de la base de datos, los datos del servidor de correo, la variable `RESERVASALAS_USUARIO_DEV` (vacía en producción) y la lista de correos con permisos de administración `RESERVASALAS_ADMINISTRACION`, todo leído del entorno
- [ ] T004 [P] Crear `tests/conftest.py` con una base de datos SQLite temporal por prueba (ruta en una carpeta temporal) y un envío de correo simulado que guarda los mensajes en una lista; el cliente de pruebas de FastAPI se añade en T012, cuando exista la aplicación
- [ ] T005 [P] Crear `README.md` del proyecto con el contenido de la guía de arranque rápido del plan

## Fase 2: Base compartida, requisitos bloqueantes (Foundational)

**Objetivo:** lo que necesitan todas las historias. Ninguna historia puede empezar hasta terminar esta fase.

- [ ] T006 Crear `src/reservasalas/db.py` con la conexión a SQLite (control manual de transacciones, `isolation_level=None`), la creación de las tablas `sala`, `persona` y `reserva` según el modelo de datos del plan, el índice `(sala_id, inicio)` y la carga de `datos/salas.sql` al arrancar si la tabla `sala` está vacía
- [ ] T007 [P] Crear `datos/salas.sql` con las 12 salas, su planta y su aforo, según los supuestos de la especificación: planta 1, Mediterráneo, Cantábrico, Atlántico y Egeo; planta 2, Báltico, Adriático, Jónico y Tirreno; planta 3, Caribe, Índico, Ártico y Mar del Norte; aforo de 8 personas en Mediterráneo, 12 en Báltico, 4 en Ártico y 6 en las demás
- [ ] T008 [P] Crear `src/reservasalas/modelos.py` con las dataclasses `Sala`, `Persona` y `Reserva` y sus estados (`disponible`/`mantenimiento`, `empleado`/`administracion`, `activa`/`cancelada`)
- [ ] T009 [P] Crear `src/reservasalas/textos.py` con todos los mensajes de confirmación y de error en castellano; cada error dice qué ha pasado y qué puede hacer la persona (principio 2)
- [ ] T010 Crear `src/reservasalas/repositorio.py` con las consultas básicas: listar salas, buscar o crear persona por correo, insertar y leer reservas (depende de T006 y T008)
- [ ] T011 Crear `src/reservasalas/identidad.py`, que lee la cabecera `X-Usuario` (o `RESERVASALAS_USUARIO_DEV` en desarrollo) y devuelve la `Persona`, creándola si no existe, con rol `administracion` si su correo está en `RESERVASALAS_ADMINISTRACION` y `empleado` en caso contrario; sin cabecera ni variable de desarrollo, rechaza la petición (depende de T010)
- [ ] T012 Crear `src/reservasalas/app.py` con la aplicación FastAPI, el montaje de `estatico/` con `src/reservasalas/estatico/estilo.css`, la configuración de Jinja2 y la plantilla `src/reservasalas/plantillas/base.html` (cabecera, navegación y zona de mensajes, con etiquetas y contraste accesibles); añadir a `tests/conftest.py` el cliente de pruebas de FastAPI (depende de T004)

**Punto de control:** `uvicorn reservasalas.app:app` arranca y `pytest` ejecuta `conftest.py` sin errores.

## Fase 3: Historia de usuario 1 — Reservar una sala (Prioridad: P1) 🎯 MVP

**Objetivo:** ver qué salas están libres en una franja, elegir una y confirmar (RF-001 a RF-007 y RF-011).

**Prueba independiente:** crear una reserva desde cero y comprobar que la sala deja de aparecer libre en esa franja.

### Pruebas de la historia 1 (se escriben primero y tienen que fallar)

- [ ] T013 [P] [HU1] Pruebas unitarias de solapamiento en `tests/unitarias/test_solapamiento.py`: solapamiento parcial, total, franjas consecutivas que no chocan y sala distinta que no choca (RF-005, CE-002)
- [ ] T014 [P] [HU1] Pruebas unitarias de límites en `tests/unitarias/test_limites.py`: antes de 08:00, después de 20:00, más de 4 horas, fin anterior al inicio, fin en el pasado y más de 30 días de antelación (RF-006)
- [ ] T015 [P] [HU1] Pruebas de contrato de `GET /api/salas` en `tests/contrato/test_api_salas.py`: lista con planta y aforo, disponibilidad por franja, sala en mantenimiento marcada y no libre (RF-001, RF-002, RF-007)
- [ ] T016 [P] [HU1] Pruebas de contrato de `POST /api/reservas` en `tests/contrato/test_api_reservas.py`: `201` con mensaje de confirmación y responsable, `409` por solapamiento con la franja ocupada, `400` por límite (uno por cada límite de RF-006; el `422` es solo para cuerpos mal formados), `409` por mantenimiento (RF-003, RF-004, RF-005, RF-006, RF-007)
- [ ] T017 [P] [HU1] Prueba de integración del recorrido completo en `tests/integracion/test_hu1_reservar.py`: consultar disponibilidad, reservar Mediterráneo, volver a consultar y ver la sala ocupada, y comprobar que se ha enviado un correo de confirmación (escenarios 1-3 de la historia, RF-011)

### Implementación de la historia 1

- [ ] T018 [HU1] Implementar `src/reservasalas/servicios/disponibilidad.py`: salas libres en una franja, marcando las ocupadas (con la franja y el responsable) y las que están en mantenimiento (RF-001, RF-002, RF-007)
- [ ] T019 [HU1] Implementar en `src/reservasalas/servicios/reservas.py` la validación de límites (horario 08:00-20:00, máximo 4 horas, fin futuro, máximo 30 días de antelación) con los mensajes de `textos.py` (RF-006)
- [ ] T020 [HU1] Implementar en `src/reservasalas/servicios/reservas.py` la creación de reserva: comprobación de solapamiento e inserción dentro de una transacción abierta con `BEGIN IMMEDIATE` explícito (así la segunda petición simultánea espera y recibe el rechazo por solapamiento, no un error de bloqueo), y rechazo si la sala está en mantenimiento (RF-003, RF-005, RF-007, CE-002)
- [ ] T021 [P] [HU1] Implementar `src/reservasalas/servicios/correo.py`: envío por el servidor corporativo con asunto y cuerpo en castellano, y la versión simulada para pruebas (RF-011)
- [ ] T022 [HU1] Implementar las rutas `GET /api/salas` y `POST /api/reservas` en `src/reservasalas/rutas/api.py` según los contratos del plan
- [ ] T023 [HU1] Crear la página `/` en `src/reservasalas/rutas/paginas.py` con la plantilla `src/reservasalas/plantillas/disponibilidad.html`: formulario de fecha y franja, lista de salas con planta, aforo y estado, botón «Reservar» y mensaje de confirmación o de error (RF-001 a RF-007)
- [ ] T024 [HU1] Ejecutar `pytest` y comprobar que las pruebas T013-T017 pasan; revisar que todos los mensajes salen de `src/reservasalas/textos.py`

**Punto de control:** la historia 1 funciona de principio a fin y se puede enseñar a Ana. Es el producto mínimo viable.

## Fase 4: Historia de usuario 2 — Cancelar o modificar mi reserva (Prioridad: P2)

**Objetivo:** que la persona responsable (o administración) pueda cancelar o cambiar una reserva y la franja anterior quede libre (RF-008, RF-010, RF-011).

**Prueba independiente:** crear una reserva, cancelarla y ver la franja libre; modificarla y ver la franja antigua libre y la nueva ocupada.

### Pruebas de la historia 2 (se escriben primero y tienen que fallar)

- [ ] T025 [P] [HU2] Pruebas unitarias de permisos en `tests/unitarias/test_permisos.py`: la responsable puede, otra persona no puede, administración puede (RF-010)
- [ ] T026 [P] [HU2] Pruebas de contrato de `DELETE` y `PUT /api/reservas/{id}` en `tests/contrato/test_api_reservas.py`: `200` al cancelar, `200` al modificar a una franja libre, `409` al modificar a una franja ocupada sin tocar la original, `403` sin permiso, `cancelada_por` cuando cancela administración y `modificada_por` cuando modifica administración (RF-008, RF-010, principio 5)
- [ ] T027 [P] [HU2] Prueba de integración en `tests/integracion/test_hu2_cancelar_modificar.py`: reservar, modificar, cancelar y comprobar la disponibilidad y los correos en cada paso (escenarios 1-5 de la historia, RF-011)

### Implementación de la historia 2

- [ ] T028 [HU2] Implementar en `src/reservasalas/servicios/reservas.py` la comprobación de permisos: persona responsable o rol `administracion` (RF-010)
- [ ] T029 [HU2] Implementar en `src/reservasalas/servicios/reservas.py` cancelar (estado `cancelada` y `cancelada_por`) y modificar (validar límites y solapamiento excluyendo la propia reserva y guardar `modificada_por`; si falla, no cambiar nada), con envío del correo correspondiente (RF-008, RF-011, principio 5)
- [ ] T030 [HU2] Implementar las rutas `PUT` y `DELETE /api/reservas/{id}` en `src/reservasalas/rutas/api.py`
- [ ] T031 [HU2] Crear la página `/reservas/{id}` en `src/reservasalas/rutas/paginas.py` con la plantilla `src/reservasalas/plantillas/reserva.html`: detalle de la reserva con responsable, formulario para cambiar la franja y botón «Cancelar reserva» con confirmación
- [ ] T032 [HU2] Ejecutar `pytest` y comprobar que las pruebas T025-T027 pasan sin romper las de la historia 1

**Punto de control:** las historias 1 y 2 funcionan juntas y por separado.

## Fase 5: Historia de usuario 3 — Ver mis reservas y las de hoy en cada sala (Prioridad: P3)

**Objetivo:** que cada persona vea sus reservas futuras y cualquiera vea las reservas de hoy por sala, con responsable (RF-004, RF-012).

**Prueba independiente:** crear reservas de varias personas y comprobar que cada una ve solo las suyas y que la vista de hoy muestra todas con nombre.

### Pruebas de la historia 3 (se escriben primero y tienen que fallar)

- [ ] T033 [P] [HU3] Pruebas de contrato de `GET /api/mis-reservas` en `tests/contrato/test_api_mis_reservas.py` (solo las futuras de la persona, ordenadas por fecha; las canceladas no aparecen) y de `GET /api/hoy` en `tests/contrato/test_api_hoy.py` (las 12 salas con sus reservas de hoy y el nombre del responsable) (RF-004, RF-012)
- [ ] T034 [P] [HU3] Prueba de integración en `tests/integracion/test_hu3_ver.py`: tres personas reservan, cada una ve lo suyo, la vista de hoy muestra las tres reservas, una persona sin reservas ve «No tienes reservas» y una reserva cancelada desaparece de «Mis reservas» (escenarios 1-4 de la historia)

### Implementación de la historia 3

- [ ] T035 [HU3] Añadir a `src/reservasalas/repositorio.py` las consultas «reservas futuras de una persona» y «reservas activas de hoy agrupadas por sala»
- [ ] T036 [HU3] Implementar las rutas `GET /api/mis-reservas` y `GET /api/hoy` en `src/reservasalas/rutas/api.py` según los contratos del plan
- [ ] T037 [HU3] Crear la página `/mis-reservas` en `src/reservasalas/rutas/paginas.py` con la plantilla `src/reservasalas/plantillas/mis_reservas.html`, con enlace a cada reserva y el mensaje «No tienes reservas» con enlace para reservar
- [ ] T038 [HU3] Crear la página `/hoy` en `src/reservasalas/rutas/paginas.py` (mismo fichero que T037: en orden, no en paralelo) con la plantilla `src/reservasalas/plantillas/hoy.html`: una fila por sala con sus reservas de hoy y el nombre del responsable
- [ ] T039 [HU3] Ejecutar `pytest` y comprobar que las pruebas T033-T034 pasan sin romper las anteriores

**Punto de control:** las tres historias funcionan de forma independiente.

## Fase 6: Remate y aspectos transversales (Polish & Cross-Cutting Concerns)

**Objetivo:** administración, comprobación de los criterios de éxito y revisión final contra la constitución.

- [ ] T040 Prueba de contrato de `PUT /api/salas/{id}/mantenimiento` en `tests/contrato/test_api_salas.py`: administración marca y desmarca una sala, la sala deja de aparecer libre y sus reservas existentes se mantienen; una persona sin permisos recibe `403` (RF-009). Se escribe primero y tiene que fallar
- [ ] T041 Implementar la ruta `PUT /api/salas/{id}/mantenimiento` en `src/reservasalas/rutas/api.py` y el botón correspondiente en `src/reservasalas/plantillas/disponibilidad.html`, visible solo para administración (RF-009)
- [ ] T042 [P] Verificar CE-002 añadiendo en `tests/integracion/test_hu1_reservar.py` una prueba con dos peticiones simultáneas a la misma sala y franja: solo una se guarda y la otra recibe el `409` por solapamiento, no un error de bloqueo de la base de datos
- [ ] T043 Verificar CE-004 añadiendo en `tests/contrato/test_api_salas.py` (mismo fichero que T040: después de ella) una prueba que carga un mes de reservas en las 12 salas y comprueba que `GET /api/salas` responde en menos de 2 segundos
- [ ] T044 [P] Verificar CE-001 y CE-003 con una sesión de prueba con 10 personas de distintos equipos siguiendo `specs/001-reserva-salas/quickstart.md`; anotar tiempos y resultado en `docs/prueba-con-usuarios.md` (tarea manual: la hace una persona; el asistente la deja sin marcar)
- [ ] T045 [P] Revisar todas las plantillas de `src/reservasalas/plantillas/` con teclado y lector de pantalla, como pide el principio 2: etiquetas en todos los campos, botones con texto, mensajes de error junto al campo (tarea manual: la hace una persona; el asistente la deja sin marcar)
- [ ] T046 Revisar el código contra los cinco principios de `.specify/memory/constitution.md` y anotar el resultado en `docs/revision-constitucion.md`; corregir cualquier desviación antes de entregar
- [ ] T047 Completar `README.md` con la configuración del despliegue interno: servidor de correo, acceso corporativo (la aplicación solo escucha detrás de él), `RESERVASALAS_USUARIO_DEV` vacía y la lista `RESERVASALAS_ADMINISTRACION`

## Dependencias y orden de ejecución

- **Fase 1 → Fase 2 → historias:** ninguna historia empieza hasta que la base compartida está lista.
- **Historias:** se hacen en orden de prioridad (HU1 → HU2 → HU3). Son independientes entre sí: HU2 y HU3 usan las reservas que crea HU1, pero sus pruebas crean sus propios datos.
- **Dentro de cada historia:** pruebas → servicios → rutas → páginas → ejecución de pruebas. Las pruebas tienen que fallar antes de implementar y pasar al terminar.
- **Remate:** después de las tres historias.

## Ejemplo en paralelo: historia 1

Las cinco pruebas de la historia 1 tocan ficheros distintos y no dependen entre sí, así que se pueden escribir a la vez:

```text
T013 tests/unitarias/test_solapamiento.py
T014 tests/unitarias/test_limites.py
T015 tests/contrato/test_api_salas.py
T016 tests/contrato/test_api_reservas.py
T017 tests/integracion/test_hu1_reservar.py
```

Después, T018 y T021 también pueden ir en paralelo; T019 y T020 tocan el mismo fichero y van en orden.

## Estrategia de implementación

1. **Primero el producto mínimo viable:** fases 1, 2 y 3. Parar, ejecutar `pytest`, enseñárselo a Ana y recoger cambios en la especificación.
2. **Entrega incremental:** añadir HU2, probar y enseñar; añadir HU3, probar y enseñar. Cada historia suma valor sin romper las anteriores.
3. **Si algo no cuadra:** no se parchea el código. Ana decide el cambio y lo pide; Luis lo escribe en `spec.md`, y Ana relee el texto nuevo y lo aprueba. Después Luis actualiza el plan, deja que `/speckit.converge` añada a este fichero las tareas que faltan y las ejecuta con `/speckit.implement` (es el paso 9 del [ejercicio 03](../../03-reserva-salas-paso-a-paso.md)). No se relanza `/speckit.tasks`, que rehace la lista entera.

Resumen: 47 tareas (5 de preparación, 7 de base compartida, 12 de HU1, 8 de HU2, 7 de HU3 y 8 de remate), 20 de ellas paralelizables. Cada RF de la especificación aparece en al menos una tarea; los cuatro criterios de éxito se comprueban en la fase de remate (T042 a T044) o en las pruebas de HU1 (CE-002).

---

⬅️ [Anterior: Plan técnico](plan.md) · 🏠 [Índice de la solución](README.md)
