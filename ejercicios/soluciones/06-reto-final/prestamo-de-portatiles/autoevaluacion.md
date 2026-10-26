# Autoevaluación: PrestamoPortatiles

> [!NOTE]
> Este fichero es la **autoevaluación** (`docs/autoevaluacion.md`): la rúbrica del [ejercicio 06](../../../06-reto-final-tu-propio-proyecto.md#rúbrica-de-autoevaluación) puntuada por Luis, con una línea de justificación por criterio y tres cosas que haría distinto. Es el paso 11 del reto. Un 17 sobre 20 con los fallos a la vista vale más que un 20 que nadie se cree: ahí está la gracia.

**Proyecto:** PrestamoPortatiles · **Autor:** Luis · **Fecha:** 2026-11-05

| Criterio | Nivel (1-4) | Por qué |
|---|---|---|
| Claridad de la especificación | 4 | Ana leyó la especificación entera antes de planificar y corrigió algo en ella: quería que el rechazo por equipo ocupado dijera quién lo tiene, no solo que está ocupado (criterio 3 de la historia 1 y RF-004). Una compañera de RRHH la leyó y la entendió sin preguntar nada. |
| Calidad de los requisitos EARS | 3 | Los nueve requisitos siguen un patrón y dicen una sola cosa, numerados sin huecos. Dos no tienen criterio de aceptación que los compruebe: RF-008 (la prórroga aceptada) y RF-009 (el aviso); solo los comprueban las pruebas automáticas y CE-004. Por eso no llega al 4. |
| Coherencia especificación-plan-tareas | 3 | El primer `/speckit.analyze` encontró una incidencia HIGH (RF-009 no tenía ninguna tarea) y se corrigió `tasks.md` antes de implementar; el segundo salió limpio. Pero tras implementar el cambio de Ana, de diez a cinco días laborables, no repetí `/speckit.converge` para confirmar que todo convergía. |
| Pruebas y verificación | 3 | Pruebas antes que implementación en cada historia, todas pasan y las reglas de negocio (calendario, solapamiento, límites, prórroga, permisos y avisos) tienen pruebas propias. Nadie más ha seguido todavía el `quickstart.md`: no llega al 4, y T028 y T029, las tareas manuales, siguen pendientes. |
| Fidelidad a la constitución | 4 | La constitución frenó una propuesta: guardar el departamento de cada persona, que el asistente incluyó en la primera versión del plan. Está anotado en la tabla «Decisiones y alternativas» de `plan.md`, y la revisión de T030 no encontró nada en el código que la contradiga. |

**Total:** 17 de 20

**Tres cosas que haría distinto:**

1. Escribir, antes de planificar, un criterio de aceptación para la prórroga y otro para el aviso. Dos requisitos sin criterio se ven al cruzar la tabla de requisitos por historia con los criterios de aceptación de cada una, y yo no lo hice hasta puntuar la rúbrica.
2. Repetir `/speckit.converge` después de cada cambio, aunque `pytest` esté en verde. Tras el cambio de Ana me quedé con las pruebas y no con la comprobación que cubre también el plan y las tareas.
3. Pedir a otra persona que siga el `quickstart.md` antes de enseñárselo a Ana, y hacer T028 y T029 antes de abrir la *pull request*, no después.

## Lista de entrega

La [lista de entrega del ejercicio 06](../../../06-reto-final-tu-propio-proyecto.md#lista-de-verificación-de-entrega), repasada antes de compartir:

| Fichero | Estado |
|---|---|
| `peticion.md` | Completo, con el visto bueno de Ana |
| `.specify/memory/constitution.md` | Completo: cuatro principios, versión 1.0.0 |
| `specs/001-prestamo-portatiles/spec.md` | Completo, con la salvedad de RF-008 y RF-009 sin criterio de aceptación |
| `specs/001-prestamo-portatiles/checklists/requirements.md` | Completo, con todas las casillas marcadas tras aclarar |
| `specs/001-prestamo-portatiles/plan.md` (con `research.md`, `data-model.md` y `quickstart.md`) | Completo, sin «NEEDS CLARIFICATION» y con una sola desviación en el registro de complejidad |
| `specs/001-prestamo-portatiles/tasks.md` | Completo: todas las tareas marcadas salvo T028 y T029, que son manuales y quedan anotadas como pendientes |
| Código y pruebas (`src/` y `tests/`) | Completos: `pytest` pasa al 100 % |
| `README.md` | Completo, con el despliegue y la programación de los avisos |
| `docs/autoevaluacion.md` | Este fichero |
| `.gitignore` | Completo: excluye `.venv/` y `prestamo.db` |

---

⬅️ [Anterior: Tareas](tasks.md) · 🏠 [Índice del ejemplo](README.md)
