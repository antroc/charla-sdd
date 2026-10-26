# Solución del ejercicio 03: ReservaSalas con Spec Kit

> **Para quién:** cualquier persona que quiera ver un ejemplo completo · **Tiempo de lectura:** ~25 min · **Nivel:** 🟡 intermedio

Esta carpeta contiene el **ejemplo canónico de ReservaSalas**: los artefactos que produce una sesión completa y bien hecha de SDD (*Spec-Driven Development*, desarrollo guiado por especificaciones) con GitHub Spec Kit (<https://github.com/github/spec-kit>), traducidos al castellano. Es el resultado de seguir el [ejercicio 03](../../03-reserva-salas-paso-a-paso.md) de principio a fin, y es el ejemplo que usan todos los documentos de este repositorio. Si en el paso 9 del ejercicio pides un cambio, tus ficheros irán un paso por delante de estos.

> [!IMPORTANT]
> Es **un** ejemplo, no «la única respuesta correcta». Si has hecho el ejercicio y tus ficheros no coinciden con estos, no pasa nada: cada asistente de IA redacta distinto y cada equipo toma decisiones distintas. Lo que importa es que tu especificación cumpla la lista de verificación y que el plan y las tareas sean coherentes con ella.

## Qué contiene

| Fichero | Qué es | Paso del flujo | Comando de Spec Kit que lo produce |
|---|---|---|---|
| [constitution.md](constitution.md) | Constitución: los 5 principios innegociables del proyecto | 0. Constitución | `/speckit.constitution` |
| [spec.md](spec.md) | Especificación: historias de usuario, requisitos en EARS (una forma sencilla y estructurada de redactar requisitos), criterios de éxito, casos límite y aclaraciones | 1. Especificar y 2. Aclarar | `/speckit.specify` y después `/speckit.clarify` |
| [aclaraciones.md](aclaraciones.md) | Las 5 preguntas del asistente y las respuestas de Ana, con su impacto en la especificación | 2. Aclarar | `/speckit.clarify` (en Spec Kit queda dentro de `spec.md`) |
| [checklist.md](checklist.md) | Lista de verificación de calidad de la especificación, con todo marcado | 1. Especificar y 5. Analizar | `/speckit.specify` la crea; `/speckit.clarify` la reevalúa; `/speckit.checklist` genera otras |
| [plan.md](plan.md) | Plan técnico: tecnología, modelo de datos, contratos, estructura y arranque | 3. Planificar | `/speckit.plan` (con `research.md`, `data-model.md`, `contracts/` y `quickstart.md` resumidos dentro) |
| [tasks.md](tasks.md) | Lista de tareas por fases e historias, con marcas `[P]` y `[HU1]`/`[HU2]`/`[HU3]` | 4. Trocear en tareas | `/speckit.tasks` |

No incluimos el código: el paso 6 (implementar, `/speckit.implement`) lo genera tu asistente a partir de estos ficheros, y cada asistente lo escribe distinto. Tampoco hay fichero para lo que el ejercicio hace después: el informe de `/speckit.analyze` (paso 7), el cambio de antelación de 30 a 60 días (paso 9) y la reflexión (paso 10). Están contados, con ejemplos y comprobables contra estos ficheros, en [los pasos 7 a 10 de ReservaSalas](../03-reserva-salas-pasos-7-a-10.md).

## Orden de lectura recomendado

1. **constitution.md** (5 min): las reglas del juego.
2. **spec.md** (10 min): fíjate en las prioridades P1/P2/P3 (P1 es lo imprescindible), en los requisitos funcionales (RF) redactados en EARS (*Easy Approach to Requirements Syntax*) y en los criterios de éxito con cifra.
3. **aclaraciones.md** y **checklist.md** (3 min): cómo se cerraron los huecos y cómo se comprobó la calidad.
4. **plan.md** (5 min): mira sobre todo la tabla «Comprobación contra la constitución» y los contratos.
5. **tasks.md** (3 min): comprueba que cada requisito funcional (RF) de la especificación aparece en alguna tarea y que las pruebas van antes que el código.

## Cómo se generó

Luis siguió el ejercicio 03 con un asistente de programación con IA compatible con Spec Kit, en este orden:

```text
specify init reserva-salas --integration claude   # crea .specify/ y los comandos de Spec Kit en el asistente
/speckit.constitution ...    # los 5 principios dictados por Ana   → .specify/memory/constitution.md
/speckit.specify ...         # descripción de ReservaSalas, sin tecnología → specs/001-reserva-salas/spec.md
                             #                                      y checklists/requirements.md
/speckit.clarify             # 5 preguntas, respuestas de Ana       → spec.md (sección Aclaraciones)
/speckit.plan ...            # Python 3.12 + FastAPI + SQLite + Jinja2, pytest → plan.md, research.md,
                             #                                      data-model.md, contracts/, quickstart.md
/speckit.tasks               # → tasks.md
/speckit.analyze             # informe de coherencia (no crea ficheros): sin incidencias CRITICAL ni HIGH
                             #   y con cobertura del 100 % (cada requisito tiene al menos una tarea)
/speckit.implement           # genera el código y ejecuta las pruebas
/speckit.converge            # comprueba que el código cubre spec, plan y tareas; añade tareas si falta algo
```

Según el asistente, los comandos aparecen con punto (`/speckit.specify`) o con guion (`/speckit-specify`, como en Claude Code, la integración del ejemplo); hacen lo mismo. Si usas otro asistente, cambia `claude` por su clave (la lista está en [Herramientas](../../../docs/07-herramientas.md)). Los textos exactos de cada *prompt* (la instrucción que le escribes al asistente) están en los pasos del [ejercicio 03](../../03-reserva-salas-paso-a-paso.md).

Lo que hemos cambiado respecto a la salida en bruto de Spec Kit: títulos de sección en castellano (con el original en inglés entre paréntesis), los ficheros de apoyo del plan resumidos dentro de `plan.md`, las aclaraciones también en un fichero aparte para que se vea el proceso, y la lista de verificación automática (`checklists/requirements.md`, que en Spec Kit tiene tres categorías y 16 comprobaciones sin numerar) ampliada con dos categorías y numerada al estilo de `/speckit.checklist`: 23 comprobaciones en cinco categorías, con una numeración propia que no coincide con la de la [plantilla](../../plantillas/lista-de-verificacion.md) (19 comprobaciones en tres categorías). Además, cada fichero empieza con un aviso que explica qué es y termina con una línea de navegación; no llevan la cabecera ni las secciones finales («En tres frases», «Siguiente paso») del resto del repositorio porque imitan los ficheros reales de un proyecto.

## En tres frases

1. Esta carpeta es el ejemplo completo de ReservaSalas: constitución, especificación con aclaraciones, lista de verificación, plan técnico y tareas, tal y como los produciría una buena sesión de Spec Kit.
2. Los ficheros son coherentes entre sí: cada requisito de la especificación lo cubre el plan y lo implementa alguna tarea, y las pruebas van siempre antes que el código.
3. Úsalo para comparar con tu propio resultado, no para copiarlo: la especificación es tuya y de tu equipo.

## Siguiente paso

Compara estos ficheros con los que hayas generado en el [ejercicio 03](../../03-reserva-salas-paso-a-paso.md) y continúa con [la solución del ejercicio 05: una especificación arreglada](../05-especificacion-arreglada.md).

---

⬅️ [Anterior: Requisitos EARS resueltos](../02-requisitos-ears-resueltos.md) · 🏠 [Índice de soluciones](../README.md) · ➡️ [Siguiente: Especificación arreglada](../05-especificacion-arreglada.md)
