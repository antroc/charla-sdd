# Tarjetas resueltas del ejercicio 04

Este documento amplía la [solución del ejercicio 04](README.md). Cada tarjeta admite más de una respuesta correcta; las siguientes sirven para comparar prioridades, requisitos, preguntas y alcance.

## Tarjeta 1 · Plazas de parking

**P1:** Como empleado que viene en coche, quiero consultar las plazas libres de un día y reservar una, para no depender del reparto por correo.

**Requisitos posibles**

- El sistema deberá mostrar las plazas libres de cada día con su número y ubicación.
- CUANDO una persona confirma una reserva, el sistema deberá registrarla a su nombre para ese día.
- SI la plaza ya está reservada, ENTONCES el sistema deberá rechazar la operación.
- MIENTRAS una plaza esté marcada como no disponible, el sistema deberá impedir reservarla.
- DONDE la persona tenga permisos de Oficina, el sistema deberá permitir marcar una plaza como no disponible.

**Aclaraciones:** antelación máxima, plazas asignadas y reservas de varios días.

**Fuera de alcance:** visitas, abonos mensuales y control de acceso físico.

## Tarjeta 2 · Dudas de nóminas

**P1:** Como empleado, quiero consultar dudas habituales de nómina y recibir una respuesta aprobada por RRHH, para no repetir las mismas preguntas por correo.

**Requisitos posibles**

- El sistema deberá mostrar únicamente respuestas aprobadas por RRHH.
- CUANDO una consulta coincida con una respuesta aprobada, el sistema deberá mostrarla.
- SI una persona solicita datos de una nómina concreta, ENTONCES el sistema deberá rechazar la consulta y remitirla al canal de RRHH.
- MIENTRAS una respuesta esté retirada, el sistema deberá dejar de mostrarla.
- DONDE la persona tenga permisos de RRHH, el sistema deberá permitir publicar y retirar respuestas.

**Aclaraciones:** qué ocurre cuando no hay respuesta, quién aprueba contenidos y si se conserva la consulta.

**Fuera de alcance:** mostrar nóminas, reclamaciones e historial personal de conversaciones.

## Tarjeta 3 · Estado de proyectos

**P1:** Como responsable de proyecto, quiero actualizar su estado en un único lugar, para que dirección y managers puedan consultarlo sin recopilar presentaciones.

**Requisitos posibles**

- El sistema deberá mostrar el estado, responsable y fecha de última actualización de cada proyecto.
- CUANDO una persona responsable actualiza su proyecto, el sistema deberá registrar el nuevo estado y la fecha.
- SI una persona sin permisos intenta modificar un proyecto, ENTONCES el sistema deberá rechazar el cambio.
- MIENTRAS un proyecto lleve `[NECESITA ACLARACIÓN: días]` sin actualizarse, el sistema deberá marcarlo como desactualizado.
- DONDE la persona sea responsable del proyecto, el sistema deberá permitirle cambiar su estado.

**Aclaraciones:** estados permitidos, plazo para considerar un dato antiguo y permisos de managers.

**Fuera de alcance:** histórico completo, avisos automáticos y métricas financieras.

## Tarjeta 4 · Material de oficina

**P1:** Como empleado, quiero pedir material y consultar el estado del pedido, para no tener que perseguir a Oficina por correo.

**Requisitos posibles**

- El sistema deberá mostrar a cada persona sus pedidos y su estado.
- CUANDO una persona envía un pedido, el sistema deberá registrarlo y mostrar una confirmación.
- SI existe un pedido pendiente del mismo artículo para esa persona, ENTONCES el sistema deberá advertirlo.
- MIENTRAS un pedido no esté entregado, el sistema deberá mantenerlo en la lista de pendientes.
- DONDE la persona tenga permisos de Oficina, el sistema deberá permitir cambiar el estado del pedido.

**Aclaraciones:** catálogo cerrado, bloqueo o aviso de duplicados y notificación de entrega.

**Fuera de alcance:** proveedores, compras, facturación y control de stock.

## Tarjeta 5 · Cursos internos

**P1:** Como empleado, quiero ver cursos con plazas disponibles e inscribirme, para no apuntarme a un curso lleno.

**Requisitos posibles**

- El sistema deberá mostrar las plazas totales y libres de cada curso.
- CUANDO una persona se inscribe en un curso con plazas, el sistema deberá registrar la inscripción y confirmarla.
- SI el curso está completo, ENTONCES el sistema deberá rechazar la inscripción.
- MIENTRAS un curso esté por debajo del mínimo de inscritos, el sistema deberá mostrarlo a RRHH como pendiente de decisión.
- DONDE la persona tenga permisos de RRHH, el sistema deberá permitir publicar cursos y fijar sus plazas.

**Aclaraciones:** lista de espera, mínimo de inscritos y cancelación de una inscripción.

**Fuera de alcance:** certificados, evaluaciones y aprobación del manager.

## Tarjeta 6 · Visitas en recepción

**P1:** Como persona de recepción, quiero registrar la llegada de una visita y avisar a quien la espera, para evitar esperas sin atender.

**Requisitos posibles**

- El sistema deberá pedir únicamente el nombre de la visita y la persona visitada.
- CUANDO recepción registra una llegada, el sistema deberá avisar a la persona visitada.
- SI un registro supera el plazo de conservación, ENTONCES el sistema deberá eliminarlo.
- MIENTRAS una visita no tenga salida registrada, el sistema deberá mostrarla como presente en el edificio.
- DONDE la persona tenga permisos de seguridad, el sistema deberá permitir consultar las visitas presentes.

**Aclaraciones:** plazo de conservación, necesidad de documento de identidad y medio de aviso.

**Fuera de alcance:** citas previas, escaneo de documentos y apertura de tornos.

## Qué se compara

No se compara la redacción literal. Comprueba que:

- la P1 resuelve algo útil por sí sola;
- cada requisito tiene una sola lectura;
- las preguntas cambian historias, requisitos o alcance;
- lo desconocido no se inventa;
- los datos personales se limitan a lo necesario;
- la primera versión queda claramente acotada.

## Vaguedades habituales

| Frase | Problema | Mejora |
|---|---|---|
| «Debe ser fácil y rápido» | Adjetivos sin medida | Crear criterios de éxito con cifras |
| «El usuario deberá actualizar…» | El sujeto no es el sistema | Describir qué permite o impide el sistema |
| «El sistema controlará las plazas» | No hay disparador ni respuesta | Indicar cuándo actúa y qué ocurre |
| «Se guardará en una hoja o base de datos» | Tecnología en la spec | Trasladarlo al plan técnico |
| «Permitirá pedir y entregar» | Dos capacidades independientes | Separar requisitos y permisos |

---

⬅️ [Portada de la solución](README.md) · 🏠 [Índice de soluciones](../README.md)
