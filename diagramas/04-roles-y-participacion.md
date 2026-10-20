# Roles y participación

> **Para quién:** managers, RRHH, perfiles de negocio y quien programa · **Tiempo de lectura:** ~7 min · **Nivel:** 🟢 básico

Cuando alguien oye hablar por primera vez de SDD (*Spec-Driven Development*, desarrollo guiado por especificaciones) suele preguntar lo mismo: «¿y yo qué pinto ahí?». Este diagrama lo responde con ReservaSalas: Ana (responsable de Oficina) encarga la aplicación, Luis (programador junior) la construye con un asistente de IA, y Marta (manager de un equipo) y Jorge (RRHH) la van a usar. Lo que hace cada rol, explicado con calma, está en [Roles: quién hace qué](../docs/06-roles-quien-hace-que.md); los pasos del flujo, en [el diagrama 02](02-flujo-completo-sdd.md).

Iconos que usamos: 👤 negocio (quien encarga o usa la aplicación), 👩‍💻 quien programa, 🤖 asistente de IA.

**Qué vas a encontrar:**

- [Pasos 0 a 2: pensar, lidera negocio](#pasos-0-a-2-pensar-lidera-negocio)
- [Pasos 3 a 6: construir, lidera quien programa](#pasos-3-a-6-construir-lidera-quien-programa)
- [Cómo vive cada paso cada persona](#cómo-vive-cada-paso-cada-persona)
- [Matriz de roles y pasos](#matriz-de-roles-y-pasos)

## Pasos 0 a 2: pensar, lidera negocio

El diagrama muestra, para cada uno de los tres primeros pasos del flujo, quién lidera y quién revisa: cada casilla lo dice con su primera palabra, y el color indica si es negocio (naranja) o quien programa (azul).

```mermaid
flowchart TD
  subgraph p0 ["0 · Constitución"]
    l0["👤 Lideran: Ana y Luis, juntos (el 🤖 asistente redacta)"]
    r0["👩‍💻 Revisa: programador senior"]
  end
  subgraph p1 ["1 · Especificar"]
    l1["👤 Lidera: Ana (el 🤖 asistente redacta el borrador)"]
    r1["👩‍💻 Revisan: Luis y QA · se consulta a Marta y Jorge"]
  end
  subgraph p2 ["2 · Aclarar"]
    l2["🤖 Pregunta el asistente · 👤 responde Ana"]
    r2["👩‍💻 Revisa: Luis, que ejecuta el comando y comprueba que la especificación se actualiza"]
  end
  l0 ~~~ r0
  l1 ~~~ r1
  l2 ~~~ r2
  p0 --> p1 --> p2
  classDef negocio fill:#FDF2E9,stroke:#B7791F;
  classDef dev fill:#E8F0FE,stroke:#1A56DB;
  class l0,l1,l2 negocio;
  class r0,r1,r2 dev;
```

De arriba abajo: la constitución la fijan juntos quien encarga y quien construye, y la revisa alguien con experiencia técnica. La especificación la lidera Ana: ella dice qué quiere y por qué, el asistente de IA lo redacta con historias y requisitos, y Luis y QA revisan que no se haya colado tecnología ni frases vagas; a Marta y Jorge se les pregunta cómo usan hoy las salas. En aclarar, el asistente hace las preguntas, Ana responde y Luis se ocupa de que las respuestas acaben dentro de la especificación. En estos tres pasos nadie programa nada.

## Pasos 3 a 6: construir, lidera quien programa

El diagrama sigue con los cuatro pasos restantes, con el mismo esquema: una casilla «Lidera» y otra «Revisa» por paso, naranja para negocio y azul para quien programa.

```mermaid
flowchart TD
  subgraph p3 ["3 · Planificar"]
    l3["👩‍💻 Lidera: Luis (el 🤖 asistente redacta el plan)"]
    r3["👩‍💻 Revisa: programador senior, contra la constitución"]
  end
  subgraph p4 ["4 · Trocear en tareas"]
    l4["👩‍💻 Lidera: Luis (el 🤖 asistente genera la lista)"]
    r4["👩‍💻 Revisan: senior y QA (tareas pequeñas, pruebas primero)"]
  end
  subgraph p5 ["5 · Analizar"]
    l5["👩‍💻 Lidera: Luis (el 🤖 asistente informa de incoherencias)"]
    r5["👤 Revisan: Ana (criterios de éxito) y QA (lista de verificación)"]
  end
  subgraph p6 ["6 · Implementar"]
    l6["👩‍💻 Lidera: Luis (el 🤖 asistente ejecuta las tareas)"]
    r6["👤 Revisan y prueban: Ana, Marta y Jorge · QA revisa las pruebas"]
  end
  l3 ~~~ r3
  l4 ~~~ r4
  l5 ~~~ r5
  l6 ~~~ r6
  p3 --> p4 --> p5 --> p6
  classDef negocio fill:#FDF2E9,stroke:#B7791F;
  classDef dev fill:#E8F0FE,stroke:#1A56DB;
  class l3,l4,l5,l6,r3,r4 dev;
  class r5,r6 negocio;
```

De arriba abajo: a partir del plan técnico lidera Luis, y el asistente de IA hace el trabajo pesado: redacta el plan, genera la lista de tareas, informa de incoherencias y, al final, ejecuta las tareas. La revisión técnica (plan y tareas) la hace alguien con experiencia. Negocio vuelve a aparecer en los dos últimos pasos: Ana comprueba que los criterios de éxito siguen siendo los suyos, y Ana, Marta y Jorge prueban la aplicación antes de darla por buena. Fíjate en que el asistente aparece en todos los pasos, pero nunca en una casilla «Revisa»: redacta y ejecuta, no aprueba.

## Cómo vive cada paso cada persona

Una lectura más ligera del mismo recorrido: el diagrama muestra, paso a paso, lo cómodo que suele resultar cada paso para quien participa en él (cara contenta = paso cómodo y vistoso; cara seria = paso tedioso o de espera). Es una estimación hecha desde nuestra experiencia, no una medición.

```mermaid
journey
  title Comodidad de cada paso para quien participa (estimación)
  section Pensar
    Constitución: 4: Ana, Luis
    Especificar: 5: Ana
    Aclarar: 3: Ana, Luis
  section Construir
    Planificar: 4: Luis
    Trocear en tareas: 4: Luis
    Analizar: 3: Luis
    Implementar: 5: Luis, Ana
```

De izquierda a derecha: los pasos más agradecidos son especificar (Ana por fin dice lo que necesita, sin traducirlo a jerga) e implementar (la aplicación aparece y se puede tocar). Las caras más serias están en aclarar y analizar: son pasos de preguntas y comprobaciones en los que no se ve avanzar nada, y por eso son los que más tentación dan de saltarse. Precisamente ahí se evitan los disgustos de después.

## Matriz de roles y pasos

La tabla resume la participación de cada rol en cada paso. **L** = lidera (es responsable de que el paso salga bien) · **R** = revisa (aprueba o pide cambios) · **C** = consulta (se le pregunta o aporta información) · **—** = no participa. La fila del asistente de IA va en palabras, porque no lidera ni revisa: produce borradores y ejecuta lo que las personas aprueban.

| Rol (en ReservaSalas) | 0 Constitución | 1 Especificar | 2 Aclarar | 3 Planificar | 4 Tareas | 5 Analizar | 6 Implementar |
|---|---|---|---|---|---|---|---|
| Quien encarga el proyecto (Ana, responsable de Oficina) | L | L | L | C | — | R | R |
| Manager de un equipo que la usará (Marta): prioridades y uso real | — | C | C | — | — | — | C |
| RRHH y otros perfiles de negocio (Jorge): datos de las personas y uso real | — | C | C | — | — | — | C |
| Programador junior (Luis) | L | R | R | L | L | L | L |
| Programador senior | R | C | — | R | R | R | R |
| QA (calidad y pruebas) | — | R | C | C | R | R | R |
| 🤖 Asistente de IA | redacta | redacta | pregunta | diseña | trocea | informa | ejecuta |

Dos formas de leer la tabla. Por filas: si eres de negocio, estás en la primera mitad (pensar) y en la prueba final, siempre sin tocar código; si programas, participas en los siete pasos y lideras los cuatro últimos. Por columnas: ningún paso tiene como único participante al asistente de IA, y ningún paso lo lidera él.

> [!TIP]
> Si en tu equipo no hay QA ni programador senior, sus casillas las cubre otra persona del equipo que **no** haya escrito el artefacto que revisa. Lo importante es que haya cuatro ojos, no el cargo.

## En tres frases

1. Negocio lidera la primera mitad del flujo (constitución, especificar, aclarar) y vuelve al final para comprobar criterios y probar; quien programa lidera la segunda mitad.
2. El asistente de IA participa en todos los pasos, pero siempre redactando, generando o ejecutando: nunca lidera y nunca aprueba.
3. Cada paso tiene una persona que lidera y otra distinta que revisa; los pasos menos vistosos (aclarar y analizar) son los que más disgustos evitan.

## Siguiente paso

Continúa con [Roles: quién hace qué](../docs/06-roles-quien-hace-que.md), que desarrolla esta matriz rol a rol y explica qué cambia en el trabajo de cada persona. Para practicarlo en equipo, está [la dinámica de 20 minutos](../ejercicios/04-dinamica-de-equipo-20-minutos.md).

---

⬅️ [Anterior: Artefactos y relaciones](03-artefactos-y-relaciones.md) · 🏠 [Índice de diagramas](README.md) · ➡️ [Siguiente: Anatomía de un requisito EARS](05-anatomia-de-un-requisito-ears.md)
