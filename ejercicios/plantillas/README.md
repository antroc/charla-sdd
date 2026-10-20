# Plantillas de los artefactos SDD

> **Para quién:** todos los perfiles (negocio, RRHH, managers y quien programa) · **Tiempo de lectura:** ~6 min · **Nivel:** 🟢 básico

Esta carpeta contiene las seis plantillas en castellano de los documentos que produce el SDD (*Spec-Driven Development*, desarrollo guiado por especificaciones): una por artefacto. Están pensadas para copiar, renombrar y rellenar. Bajo cada título llevan una ayuda visible, una línea en cursiva dentro de una cita, que explica qué va en esa sección, para quién es y un consejo; y traen un ejemplo a medio rellenar con ReservaSalas.

No hace falta instalar nada para usarlas. Si trabajas con GitHub Spec Kit (la herramienta gratuita de GitHub que añade este flujo a tu asistente de IA; ver [Herramientas](../../docs/07-herramientas.md)), el asistente genera su equivalente; entonces las plantillas te sirven de guía para revisar lo que ha escrito.

## Qué hay en esta carpeta

| Plantilla | Para qué sirve | Quién la rellena | En qué paso del flujo |
|---|---|---|---|
| [constitucion.md](constitucion.md) | Los principios innegociables del proyecto: sencillez, pruebas, datos, accesibilidad… | Quien encarga el proyecto y quien lo construye, juntos | 0 · Constitución |
| [especificacion.md](especificacion.md) | **Qué** queremos y **por qué**: historias priorizadas, requisitos en EARS (*Easy Approach to Requirements Syntax*, una forma sencilla y estructurada de redactar requisitos), criterios de éxito, casos límite | Negocio (quien pide), con revisión de quien construye | 1 · Especificar |
| [lista-de-aclaraciones.md](lista-de-aclaraciones.md) | Registro de preguntas y respuestas que afinan la especificación | Pregunta quien construye (o el asistente de IA); responde quien encarga | 2 · Aclarar |
| [plan-tecnico.md](plan-tecnico.md) | **Cómo** lo haremos: tecnología, estructura, modelo de datos (qué información guarda el sistema), contratos (qué entra y qué sale en cada operación) y riesgos | Quien construye (con el asistente de IA); revisa alguien con experiencia técnica | 3 · Planificar |
| [tareas.md](tareas.md) | Lista ordenada y troceada de trabajo, agrupada por historia de usuario | Quien construye (con el asistente de IA) | 4 · Trocear en tareas |
| [lista-de-verificacion.md](lista-de-verificacion.md) | Preguntas de sí o no para comprobar la calidad de la especificación | Alguien que *no* la escribió: otra persona del equipo o negocio. Con Spec Kit, la lista automática la evalúa el asistente de IA; las listas por tema las marca quien revisa | 5 · Analizar (y antes, al revisar la especificación) |

El paso 6, implementar, no tiene plantilla: su resultado es el código, y lo que se revisa son las tareas marcadas y las pruebas.

## Cómo se usa una plantilla

1. Copia el fichero a la carpeta de tu proyecto. Sin herramientas, cualquier carpeta vale; con Spec Kit, junto a los ficheros que genera el asistente.
2. Renómbralo con el nombre real que indica su aviso inicial: `constitution.md`, `spec.md`, `aclaraciones.md`, `plan.md`, `tasks.md` o `checklist.md`.
3. Rellena todo lo que va entre corchetes `[…]` con tu proyecto y borra lo que no aplique.
4. Lee las ayudas: son las líneas en cursiva que hay bajo cada título, con este formato: *Qué se escribe: … · Para quién: … · Consejo: …*. Se ven en la vista normal de GitHub, en cualquier editor y en el documento donde las pegues; úsalas de guía y bórralas cuando el documento esté listo.
5. Pasa la lista de verificación antes de dar la especificación por terminada.

Las plantillas no llevan el bloque «Qué vas a encontrar» que abre los documentos largos de este repositorio: están pensadas para copiarse y rellenarse, y sus secciones cambian con cada proyecto. Si tu documento final queda largo, añádeselo tú; el ejemplo resuelto lo lleva.

> [!TIP]
> Si vas a rellenarlas a mano y no te apetece pelearte con Markdown, abre la plantilla en GitHub (la vista normal, sin pulsar «Raw»), selecciona desde el primer título hasta el final, copia y pégalo en tu documento (Word, Google Docs…): se pega con formato. Las ayudas de cada sección aparecen en cursiva bajo su título; bórralas cuando termines. Lo que importa son las secciones y las preguntas, no el formato.

## Cuándo usar las plantillas

- **Sin herramientas.** No tienes Spec Kit ni un asistente de programación con IA, o el proyecto no es de software (un proceso de RRHH, un procedimiento de oficina). Rellenas las plantillas a mano o con un chat de IA genérico autorizado por la empresa. Es la vía de los ejercicios [01](../01-tu-primera-especificacion-sin-codigo.md) y [04](../04-dinamica-de-equipo-20-minutos.md).
- **Para revisar.** Trabajas con Spec Kit y el asistente de IA ya ha generado `spec.md` o `plan.md`. Abres la plantilla al lado y compruebas que no falta ninguna sección, que los requisitos siguen EARS y que no se ha colado tecnología en la especificación.
- **Para formación.** Usas las plantillas como guion en un taller o para explicar a alguien qué contiene cada artefacto. El ejemplo de ReservaSalas ya viene a medio rellenar, así que no hace falta inventar nada.

## Correspondencia con los ficheros reales de Spec Kit

Spec Kit genera sus ficheros en inglés y con otros nombres. Esta tabla dice qué plantilla corresponde a cada uno y qué comando del asistente lo produce.

| Plantilla | Fichero en un proyecto Spec Kit | Lo genera |
|---|---|---|
| `constitucion.md` | `.specify/memory/constitution.md` | `/speckit.constitution` |
| `especificacion.md` | `specs/001-nombre-corto/spec.md` | `/speckit.specify` |
| `lista-de-aclaraciones.md` | No hay fichero aparte: es la sección «Clarifications» dentro de `spec.md` | `/speckit.clarify` |
| `plan-tecnico.md` | `specs/001-nombre-corto/plan.md`, más `research.md`, `data-model.md`, `contracts/` y `quickstart.md` (aquí resumidos dentro del plan) | `/speckit.plan` |
| `tareas.md` | `specs/001-nombre-corto/tasks.md` | `/speckit.tasks` |
| `lista-de-verificacion.md` | `specs/001-nombre-corto/checklists/requirements.md` (automática) y `checklists/[tema].md` (una por tema) | `/speckit.specify` y `/speckit.checklist` |

Dos diferencias que conviene conocer. Spec Kit numera los requisitos como `FR-001` y los criterios de éxito como `SC-001`; en este material los escribimos como `RF-001` y `CE-001`. Y en las tareas marca las historias como `[US1]`; nosotros usamos `[HU1]`. El significado es el mismo. Los comandos están explicados en [Herramientas](../../docs/07-herramientas.md) y las secciones de cada artefacto, una a una, en [Los artefactos](../../docs/04-los-artefactos.md).

## Ejemplo resuelto

Las seis plantillas rellenas del todo, con ReservaSalas y tal como las produciría una buena sesión con Spec Kit, están en [el ejemplo resuelto del ejercicio 03](../soluciones/03-reserva-salas/README.md). Si dudas de cómo quedaría una sección, mira allí antes de inventar.

## En tres frases

1. Hay una plantilla por artefacto del flujo SDD, en castellano, con una ayuda visible en cursiva bajo cada título y un ejemplo de ReservaSalas a medio rellenar.
2. Sirven para trabajar sin herramientas, para revisar lo que genera el asistente de IA y para formar a otras personas.
3. Cada plantilla se corresponde con un fichero (o una sección) real de Spec Kit: cambia el nombre, no el contenido.

## Siguiente paso

Continúa con el [Ejercicio 01: tu primera especificación sin código](../01-tu-primera-especificacion-sin-codigo.md), copiando antes [especificacion.md](especificacion.md). Si prefieres ver primero cómo queda todo relleno, abre el [ejemplo resuelto de ReservaSalas](../soluciones/03-reserva-salas/README.md).

---

⬅️ [Anterior: Ejercicio 06, reto final](../06-reto-final-tu-propio-proyecto.md) · 🏠 [Índice de ejercicios](../README.md) · ➡️ [Siguiente: Soluciones](../soluciones/README.md)
