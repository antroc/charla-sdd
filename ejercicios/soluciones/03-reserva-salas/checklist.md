# Lista de verificación de calidad de la especificación: ReservaSalas

> [!NOTE]
> Este fichero es la **lista de verificación** (*checklist*) de calidad de la especificación: un control de calidad del texto de `spec.md`, no del código (en Spec Kit lo llaman «las pruebas unitarias de la especificación»). Spec Kit la crea automáticamente al ejecutar `/speckit.specify` (como `checklists/requirements.md`) y la vuelve a evaluar tras `/speckit.clarify`; con `/speckit.checklist` se generan otras centradas en un tema (accesibilidad, seguridad…). Forma parte del paso 5 del flujo SDD (*Spec-Driven Development*, desarrollo guiado por especificaciones), el paso de analizar, aunque se usa desde el paso 1.
>
> La lista automática de Spec Kit tiene tres categorías y 16 comprobaciones sin numerar. Aquí la hemos ampliado con dos categorías («Claridad y medibilidad» y «Coherencia») y con la numeración CHK que usan las listas de `/speckit.checklist`, para que coincida con la [plantilla](../../plantillas/lista-de-verificacion.md) de este repositorio.

**Propósito:** comprobar que la especificación está completa, es clara y se puede planificar sin ambigüedades · **Creada:** 2026-10-06 (reevaluada el 2026-10-07 tras aclarar) · **Funcionalidad:** [spec.md](spec.md)

Una casilla marcada (`[x]`) significa que ese criterio de calidad se ha comprobado en el texto de la especificación; no significa que la funcionalidad esté implementada. En la lista automática las marca el asistente de IA al ejecutar `/speckit.specify` y `/speckit.clarify`; en las listas por tema de `/speckit.checklist` las marca la persona que revisa.

## Calidad del contenido (Content Quality)

- [x] CHK001 La especificación no contiene detalles de implementación (lenguajes, bases de datos, herramientas). — Las entidades se describen por lo que son, no por cómo se guardan.
- [x] CHK002 Está centrada en el valor para las personas y en el problema de negocio (choques, salas vacías, reservas fantasma).
- [x] CHK003 Puede leerla alguien sin perfil técnico. — Ana la revisó y la aprobó sin preguntas sobre el formato.
- [x] CHK004 Todas las secciones obligatorias están completas (historias, requisitos, criterios de éxito, supuestos).

## Completitud de los requisitos (Requirement Completeness)

- [x] CHK005 No queda ningún marcador «[NECESITA ACLARACIÓN]» (la etiqueta que el asistente de IA deja en la especificación donde le falta información). — No hubo marcadores: donde faltaba un dato, el asistente tomó una decisión razonable y la anotó en «Supuestos»; los huecos de alcance y de permisos los cerró después la sesión de aclarar del 2026-10-07.
- [x] CHK006 Cada requisito es comprobable y no admite dos lecturas. — Los doce siguen el formato EARS (*Easy Approach to Requirements Syntax*, una forma sencilla y estructurada de redactar requisitos): sistema y respuesta y, cuando toca, disparador o condición.
- [x] CHK007 Cada historia de usuario tiene criterios de aceptación en formato Dado/Cuando/Entonces, incluidos los de error.
- [x] CHK008 Los casos límite están identificados. — Nueve casos, cada uno con el comportamiento esperado.
- [x] CHK009 El alcance está delimitado. — Sección «Fuera de alcance» con cinco exclusiones explícitas, dos de ellas fruto de aclarar.
- [x] CHK010 Las dependencias y los supuestos están documentados. — Seis supuestos, incluido el servidor de correo corporativo.

## Claridad y medibilidad (Clarity & Measurability)

- [x] CHK011 Los criterios de éxito son medibles (tiempo, porcentaje o recuento) y dicen cómo se van a medir.
- [x] CHK012 Los criterios de éxito no mencionan tecnología. — «Menos de 2 segundos» describe lo que ve la persona, no la base de datos.
- [x] CHK013 No hay adjetivos vagos sin cifra («rápido», «sencillo», «intuitivo») en requisitos ni en criterios de éxito.
- [x] CHK014 Los límites numéricos están cerrados: horario 08:00-20:00, máximo 4 horas, antelación máxima 30 días, 12 salas en 3 plantas.
- [x] CHK015 Los roles están definidos sin ambigüedad. — Dos roles (empleado y administración) y qué puede hacer cada uno (RF-008, RF-009, RF-010).

## Coherencia (Consistency)

- [x] CHK016 Los requisitos no se contradicen entre sí ni con los casos límite. — RF-005 y el caso «dos personas a la vez» describen el mismo resultado.
- [x] CHK017 Las entidades que usan los requisitos (Sala, Reserva, Persona) están definidas en «Entidades clave» con los atributos que los requisitos necesitan (estado de la sala, rol de la persona).
- [x] CHK018 La terminología es la misma en todo el documento: «franja», «reserva», «responsable», «administración». — Se cambió «usuario» por «persona» en dos escenarios.
- [x] CHK019 La especificación respeta la constitución: solo nombre y correo de cada persona (principio 4); toda reserva tiene responsable visible (principio 5).

## Preparación de la funcionalidad (Feature Readiness)

- [x] CHK020 Cada requisito funcional está cubierto por al menos un criterio de aceptación o un caso límite. — RF-011 en el criterio 7 de la historia 1; RF-009 en el caso límite «Marcar una sala en mantenimiento»; los demás, en los criterios de su historia.
- [x] CHK021 Las historias cubren los flujos principales y la P1 vale por sí sola como producto mínimo.
- [x] CHK022 Los criterios de éxito se pueden verificar al terminar sin conocer la implementación.
- [x] CHK023 Nada en la especificación obliga a una decisión técnica concreta en el plan.

## Notas

- Resultado tras `/speckit.specify` (2026-10-06): 20 de 23 criterios superados. Pendientes: CHK009 (el alcance no decía nada de las reservas recurrentes ni de la asistencia), CHK014 (faltaba el límite de antelación) y CHK015 (no estaba dicho quién puede cancelar una reserva ajena).
- Resultado tras `/speckit.clarify` (2026-10-07): 23 de 23. Las respuestas sobre alcance (recurrentes, asistencia), antelación (30 días) y permisos (solo administración) cerraron los tres pendientes.
- `/speckit.implement` lee el estado de estas casillas antes de empezar: si alguna está sin marcar, pregunta si se quiere seguir. No las modifica.
- Las comprobaciones del tipo «verificar que la aplicación…» no pertenecen aquí: eso son pruebas del código y viven en `tests/`.

---

⬅️ [Anterior: Aclaraciones](aclaraciones.md) · 🏠 [Índice de la solución](README.md) · ➡️ [Siguiente: Plan técnico](plan.md)
