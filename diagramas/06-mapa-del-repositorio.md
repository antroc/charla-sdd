# Mapa del repositorio

> **Para quién:** todos los perfiles (managers, RRHH, negocio y quien programa) · **Tiempo de lectura:** ~8 min · **Nivel:** 🟢 básico

Este repositorio es el material de formación interno sobre SDD (*Spec-Driven Development*, desarrollo guiado por especificaciones). Tiene cinco partes y unos cincuenta ficheros, pero nadie tiene que leerlos todos: cada perfil tiene su propio camino. Esta página es el plano del edificio: primero un mapa con todo lo que hay, después el itinerario de cada perfil y, al final, una tabla con cada fichero, de qué va, para quién es y cuánto se tarda. Si acabas de llegar, lo más cómodo es empezar por la [portada](../README.md), que tiene estos mismos itinerarios en forma de enlaces.

**Qué vas a encontrar**

- [El repositorio de un vistazo](#el-repositorio-de-un-vistazo)
- [Itinerarios por perfil](#itinerarios-por-perfil)
- [Todos los ficheros, uno por línea](#todos-los-ficheros-uno-por-línea)

## El repositorio de un vistazo

El mapa mental muestra el repositorio entero: en el centro, su nombre; alrededor, cinco partes (la raíz y las cuatro carpetas de contenido: `docs/`, `diagramas/`, `ejercicios/` y `charla/`), y dentro de cada parte sus ficheros con el nombre abreviado.

```mermaid
mindmap
  root((Charla SDD))
    Raíz
      README portada
      CONTRIBUIR cómo proponer mejoras
    docs
      01 El problema del vibe coding
      02 Qué es SDD
      03 El flujo paso a paso
      04 Los artefactos
      05 Escribir requisitos claros EARS
      06 Roles y quién hace qué
      07 Herramientas
      08 Buenas prácticas y errores comunes
      09 Preguntas frecuentes
      10 Glosario
    diagramas
      01 Vibe coding frente a SDD
      02 Flujo completo de SDD
      03 Artefactos y relaciones
      04 Roles y participación
      05 Anatomía de un requisito EARS
      06 Mapa del repositorio
      svg y png exportaciones automáticas
    ejercicios
      00 Preparación del entorno
      01 Tu primera especificación sin código
      02 Practicar requisitos EARS
      03 ReservaSalas paso a paso
      04 Dinámica de equipo de 20 minutos
      05 Arreglar una especificación mala
      06 Reto final con tu propio proyecto
      plantillas
        constitución
        especificación
        lista de aclaraciones
        plan técnico
        tareas
        lista de verificación
      soluciones
        01 solicitud de vacaciones
        02 requisitos EARS resueltos
        03 ReservaSalas ejemplo completo
        05 especificación arreglada
    charla
      Guion de 20 minutos
      Guía del facilitador
```

De dentro hacia fuera: la raíz tiene la portada (`README.md`) y la guía para proponer mejoras (`CONTRIBUIR.md`). `docs/` es la teoría, en diez documentos numerados que se leen en orden (aunque cada perfil puede saltarse algunos): van desde el problema del *vibe coding* (programar a golpe de instrucciones sueltas, improvisando con el asistente de IA) hasta el glosario. `diagramas/` cuenta lo mismo en dibujos; esta página es el último. `ejercicios/` es la práctica: siete ejercicios, las plantillas de los artefactos listas para copiar y las soluciones, entre ellas el ejemplo completo de ReservaSalas: los seis ficheros que produce el flujo y un README que explica cómo se generaron. `charla/` es para quien tiene que contárselo a los demás.

Para no recargar el mapa no aparecen los índices: cada carpeta (también `plantillas/`, `soluciones/` y `soluciones/03-reserva-salas/`) tiene su propio `README.md`, y los encontrarás todos en la tabla del final. `diagramas/svg/` y `diagramas/png/` guardan una exportación automática de cada diagrama (SVG para PowerPoint y documentos; PNG para Google Slides o el correo), útil para pegarlo en una presentación; no se editan a mano.

## Itinerarios por perfil

Cada diagrama es un camino de lectura: empiezas por la izquierda y sigues las flechas. Cada recuadro dice de qué carpeta es (doc, diagrama, ejercicio o charla) y debajo tienes los enlaces en el mismo orden. Los tiempos son aproximados; los exactos están en la cabecera de cada fichero.

### Manager o responsable de equipo (unas 3 horas)

Este camino te da lo justo para decidir si tu equipo prueba SDD y saber qué te va a pedir: el problema, la idea, tu papel y lo que suele salir mal.

```mermaid
flowchart LR
  a["docs 01 y 02: el problema del vibe coding y qué es SDD"] --> b["diagramas 01 y 02: los dos caminos y el flujo completo"]
  b --> c["doc 06: roles, quién hace qué"]
  c --> d["docs 08 y 09: buenas prácticas y preguntas frecuentes"]
  d --> e["ejercicio 01: tu primera especificación sin código"]
  e --> f["charla: el guion de 20 minutos"]
  f --> g["ejercicio 04: la dinámica de 20 minutos, con tu equipo"]
```

De izquierda a derecha: empiezas por [El problema del vibe coding](../docs/01-el-problema-del-vibe-coding.md) y [Qué es SDD](../docs/02-que-es-sdd.md); los ves dibujados en [Vibe coding frente a SDD](01-vibe-coding-vs-sdd.md) y [Flujo completo de SDD](02-flujo-completo-sdd.md); en [Roles: quién hace qué](../docs/06-roles-quien-hace-que.md) encuentras tu papel, y [Buenas prácticas y errores comunes](../docs/08-buenas-practicas-y-errores-comunes.md) y [Preguntas frecuentes](../docs/09-preguntas-frecuentes.md) te preparan para las dudas del equipo. Escribes una especificación sin código en el [ejercicio 01](../ejercicios/01-tu-primera-especificacion-sin-codigo.md); si quieres contárselo a tu equipo, tienes el [guion de 20 minutos](../charla/guion-20-minutos.md), y terminas probándolo con ellos en la [dinámica de 20 minutos](../ejercicios/04-dinamica-de-equipo-20-minutos.md).

### RRHH y perfiles de negocio (unas 3 horas)

Si pides software o lo usas, este camino te enseña a escribir lo que necesitas de forma que no se pueda malinterpretar.

```mermaid
flowchart LR
  a["docs 01 y 02: el problema del vibe coding y qué es SDD"] --> b["diagrama 01: los dos caminos, uno al lado del otro"]
  b --> c["doc 05: escribir requisitos claros con EARS"]
  c --> d["doc 06: roles, quién hace qué"]
  d --> e["ejercicios 01 y 02: una especificación sin código y práctica de EARS"]
  e --> f["doc 10: glosario, para consultar cuando haga falta"]
```

De izquierda a derecha: [El problema del vibe coding](../docs/01-el-problema-del-vibe-coding.md) y [Qué es SDD](../docs/02-que-es-sdd.md) explican de qué va esto, y [Vibe coding frente a SDD](01-vibe-coding-vs-sdd.md) lo resume en dos dibujos. [Escribir requisitos claros (EARS)](../docs/05-escribir-requisitos-claros-ears.md) es la pieza clave para ti: cómo pedir las cosas de forma comprobable; [Roles: quién hace qué](../docs/06-roles-quien-hace-que.md) te dice en qué pasos participas. Lo practicas con el [ejercicio 01](../ejercicios/01-tu-primera-especificacion-sin-codigo.md) y el [ejercicio 02](../ejercicios/02-practicar-requisitos-ears.md), y el [glosario](../docs/10-glosario.md) queda a mano para cualquier término que se te resista.

### Programador junior (10-12 horas, en varios días)

Es el itinerario completo: toda la teoría, todos los diagramas y los ejercicios con herramientas, hasta construir ReservaSalas y un proyecto propio.

```mermaid
flowchart LR
  a["docs 01 a 10, en orden"] --> b["diagramas 01 a 06"]
  b --> c["ejercicio 00: preparación del entorno, vía B"]
  c --> d["ejercicio 02: practicar requisitos EARS"]
  d --> e["ejercicio 03: ReservaSalas paso a paso"]
  e --> f["ejercicio 05: arreglar una especificación mala"]
  f --> g["ejercicio 06: reto final, tu propio proyecto"]
```

De izquierda a derecha: lees los diez documentos de [`docs/`](../docs/README.md) en orden, desde [El problema del vibe coding](../docs/01-el-problema-del-vibe-coding.md) hasta el [glosario](../docs/10-glosario.md), y después los seis [diagramas](README.md). Luego la práctica: instalas lo necesario en el [ejercicio 00](../ejercicios/00-preparacion-del-entorno.md) (vía B), afinas los requisitos en el [ejercicio 02](../ejercicios/02-practicar-requisitos-ears.md), construyes ReservaSalas con Spec Kit en el [ejercicio 03](../ejercicios/03-reserva-salas-paso-a-paso.md), entrenas el ojo crítico en el [ejercicio 05](../ejercicios/05-arreglar-una-especificacion-mala.md) y cierras con un proyecto tuyo en el [ejercicio 06](../ejercicios/06-reto-final-tu-propio-proyecto.md).

### Programador con experiencia (6-8 horas)

Si ya programas con un asistente de IA, puedes saltarte la motivación e ir directamente al flujo, los artefactos y las herramientas.

```mermaid
flowchart LR
  a["doc 02: qué es SDD"] --> b["docs 03 y 04: el flujo paso a paso y los artefactos"]
  b --> c["diagramas 02 y 03: flujo completo y artefactos y relaciones"]
  c --> d["docs 07 y 08: herramientas y buenas prácticas"]
  d --> e["ejercicio 03: ReservaSalas paso a paso"]
  e --> f["ejercicio 06: reto final, tu propio proyecto"]
```

De izquierda a derecha: [Qué es SDD](../docs/02-que-es-sdd.md) fija el vocabulario; [El flujo paso a paso](../docs/03-el-flujo-paso-a-paso.md) y [Los artefactos](../docs/04-los-artefactos.md) son el núcleo, y [Flujo completo de SDD](02-flujo-completo-sdd.md) y [Artefactos y relaciones](03-artefactos-y-relaciones.md) los resumen en dos diagramas; [Herramientas](../docs/07-herramientas.md) y [Buenas prácticas y errores comunes](../docs/08-buenas-practicas-y-errores-comunes.md) te dicen qué instalar y qué evitar. Después construyes ReservaSalas en el [ejercicio 03](../ejercicios/03-reserva-salas-paso-a-paso.md), comparas con la [solución canónica](../ejercicios/soluciones/03-reserva-salas/README.md) y aplicas el flujo a un problema real en el [ejercicio 06](../ejercicios/06-reto-final-tu-propio-proyecto.md).

### Facilitador de la charla o del taller

Si vas a presentar SDD o a dirigir un taller, lo tuyo es la carpeta `charla/`, la dinámica en grupo y todos los diagramas para proyectar. La primera vez, prepararlo lleva unas 2 horas.

```mermaid
flowchart LR
  a["charla: README de la carpeta"] --> b["charla: guion de 20 minutos"]
  b --> c["charla: guía del facilitador"]
  c --> d["ejercicio 04: dinámica de equipo de 20 minutos"]
  d --> e["diagramas 01 a 06, para proyectar"]
  e --> f["diagramas en SVG y PNG, para las diapositivas"]
```

De izquierda a derecha: el [índice de `charla/`](../charla/README.md) te dice qué hay; el [guion de 20 minutos](../charla/guion-20-minutos.md) es la charla minuto a minuto, y la [guía del facilitador](../charla/guia-del-facilitador.md) explica cómo montar un taller de dos horas o un itinerario de autoformación. La [dinámica de equipo de 20 minutos](../ejercicios/04-dinamica-de-equipo-20-minutos.md) es el ejercicio en grupo sin ordenador; los seis [diagramas](README.md) sirven para proyectar y sus versiones en [`svg/`](svg/) y [`png/`](png/) para pegarlas en las diapositivas. Las mejoras que te sugiera el público se recogen como explica [CONTRIBUIR.md](../CONTRIBUIR.md).

## Todos los ficheros, uno por línea

La tabla recorre el repositorio en el mismo orden que el mapa. Para cada fichero: de qué va en una línea, a quién le interesa y el tiempo con su nivel (🟢 básico, 🟡 intermedio, 🔴 avanzado), tal como figuran en su cabecera; en los ejercicios, el tiempo es el de hacerlos. «Consulta» quiere decir que es material de referencia: se abre cuando hace falta, no se lee de principio a fin.

| Fichero | De qué va | Para quién | Tiempo y nivel |
|---|---|---|---|
| [README.md](../README.md) | Portada: qué es el repositorio, para quién es y por dónde empezar según tu perfil | Todos | ~5 min · 🟢 |
| [CONTRIBUIR.md](../CONTRIBUIR.md) | Cómo proponer mejoras al material, la guía de estilo resumida y qué no incluir | Todos | ~7 min · 🟢 |
| [docs/README.md](../docs/README.md) | Índice detallado de la documentación con las rutas de lectura por perfil | Todos | ~3 min · 🟢 |
| [docs/01-el-problema-del-vibe-coding.md](../docs/01-el-problema-del-vibe-coding.md) | Qué es el *vibe coding*, por qué engancha y lo que le cuesta a la empresa después | Todos | ~8 min · 🟢 |
| [docs/02-que-es-sdd.md](../docs/02-que-es-sdd.md) | Qué es SDD en una frase, qué cambia respecto a antes y qué no es | Todos | ~10 min · 🟢 |
| [docs/03-el-flujo-paso-a-paso.md](../docs/03-el-flujo-paso-a-paso.md) | Los siete pasos del flujo: qué entra, qué sale y qué puede salir mal en cada uno | Junior y quien quiera el detalle de cada paso | ~15 min · 🟡 |
| [docs/04-los-artefactos.md](../docs/04-los-artefactos.md) | Los cinco artefactos (constitución, especificación, plan técnico, tareas y lista de verificación) con extractos de ReservaSalas | Junior y quien vaya a escribir o revisar una especificación | ~15 min · 🟡 |
| [docs/05-escribir-requisitos-claros-ears.md](../docs/05-escribir-requisitos-claros-ears.md) | Cómo escribir requisitos claros con EARS: patrones, reglas de oro y ejemplos antes y después | Todos | ~12 min · 🟢 |
| [docs/06-roles-quien-hace-que.md](../docs/06-roles-quien-hace-que.md) | Quién lidera, revisa o consulta en cada paso, incluidas las personas que no programan | Todos | ~10 min · 🟢 |
| [docs/07-herramientas.md](../docs/07-herramientas.md) | Spec Kit, Kiro y la vía sin herramientas: qué hace falta instalar (o no) según tu perfil | Junior y quien decida qué instalar | ~12 min · 🟡 |
| [docs/08-buenas-practicas-y-errores-comunes.md](../docs/08-buenas-practicas-y-errores-comunes.md) | Buenas prácticas, errores comunes con su remedio y señales de que vas bien | Todos, sobre todo quien encarga, lidera o revisa | ~12 min · 🟡 |
| [docs/09-preguntas-frecuentes.md](../docs/09-preguntas-frecuentes.md) | Preguntas frecuentes agrupadas por perfil, con enlace al documento que amplía cada respuesta | Todos | ~10 min · 🟢 |
| [docs/10-glosario.md](../docs/10-glosario.md) | Glosario: los términos del material explicados en lenguaje llano, con enlaces | Todos | ~15 min o consulta · 🟢 |
| [diagramas/README.md](README.md) | Índice de los diagramas, cómo verlos en GitHub, cómo editarlos y dónde están los SVG | Todos | ~3 min · 🟢 |
| [diagramas/01-vibe-coding-vs-sdd.md](01-vibe-coding-vs-sdd.md) | Los dos caminos, uno al lado del otro: el bucle de parches frente al flujo con especificación | Managers, RRHH, negocio y junior | ~6 min · 🟢 |
| [diagramas/02-flujo-completo-sdd.md](02-flujo-completo-sdd.md) | El diagrama principal: los siete pasos, sus ficheros, quién participa y los bucles de vuelta | Junior, managers y quien quiera ver el proceso entero | ~10 min · 🟡 |
| [diagramas/03-artefactos-y-relaciones.md](03-artefactos-y-relaciones.md) | Cómo se alimentan los artefactos entre sí y qué fichero es cada cosa | Junior y perfiles técnicos | ~8 min · 🟡 |
| [diagramas/04-roles-y-participacion.md](04-roles-y-participacion.md) | Quién lidera y quién revisa en cada paso, con la matriz rol × paso | Todos | ~7 min · 🟢 |
| [diagramas/05-anatomia-de-un-requisito-ears.md](05-anatomia-de-un-requisito-ears.md) | Un requisito EARS pieza a pieza y el árbol de decisión para elegir patrón | Managers, RRHH, negocio y junior | ~6 min · 🟢 |
| [diagramas/06-mapa-del-repositorio.md](06-mapa-del-repositorio.md) | Esta página: el mapa del repositorio, los itinerarios por perfil y esta tabla | Todos | ~8 min · 🟢 |
| [diagramas/svg/](svg/) | Exportación automática de cada diagrama en SVG (PowerPoint, documentos), lista para pegar en una presentación; no se edita a mano | Facilitadores y quien prepare diapositivas | ~1 min · 🟢 |
| [diagramas/png/](png/) | La misma exportación en PNG (Google Slides, correo, chats); no se edita a mano | Facilitadores y quien prepare diapositivas | ~1 min · 🟢 |
| [ejercicios/README.md](../ejercicios/README.md) | Índice de ejercicios, niveles, itinerarios por perfil y cómo usarlos | Todos | ~4 min · 🟢 |
| [ejercicios/00-preparacion-del-entorno.md](../ejercicios/00-preparacion-del-entorno.md) | Preparar el entorno: vía A sin instalar nada y vía B con Git, un asistente de IA y Spec Kit | Todos (vía A) y quien programa (vía B) | 10-45 min · 🟡 |
| [ejercicios/01-tu-primera-especificacion-sin-codigo.md](../ejercicios/01-tu-primera-especificacion-sin-codigo.md) | Escribir la especificación de «Solicitud de vacaciones» con la plantilla, sin código | Managers, RRHH y negocio | 60-90 min · 🟢 |
| [ejercicios/02-practicar-requisitos-ears.md](../ejercicios/02-practicar-requisitos-ears.md) | Reescribir doce frases vagas en EARS, clasificar patrones y cazar errores | RRHH, negocio, managers y junior | 30 min · 🟢 |
| [ejercicios/03-reserva-salas-paso-a-paso.md](../ejercicios/03-reserva-salas-paso-a-paso.md) | Construir ReservaSalas de principio a fin con Spec Kit y un asistente de IA; el ejercicio central | Junior y cualquiera que programe | 90-120 min · 🟡 |
| [ejercicios/04-dinamica-de-equipo-20-minutos.md](../ejercicios/04-dinamica-de-equipo-20-minutos.md) | Taller en grupo sin ordenador: de una petición vaga a historias, requisitos y preguntas | Facilitadores; todos como participantes | 20 min · 🟢 |
| [ejercicios/05-arreglar-una-especificacion-mala.md](../ejercicios/05-arreglar-una-especificacion-mala.md) | Detectar diez problemas en una especificación mala de ReservaSalas y reescribirla | Junior y negocio que haya hecho el 02 | 30-40 min · 🟡 |
| [ejercicios/06-reto-final-tu-propio-proyecto.md](../ejercicios/06-reto-final-tu-propio-proyecto.md) | Recorrer el flujo completo con un problema real tuyo, con rúbrica de autoevaluación | Quien programa y ha terminado el 03 | 3-4 h · 🔴 |
| [ejercicios/plantillas/README.md](../ejercicios/plantillas/README.md) | Qué plantillas hay y cómo usarlas con y sin Spec Kit | Todos | ~6 min · 🟢 |
| [ejercicios/plantillas/constitucion.md](../ejercicios/plantillas/constitucion.md) | Plantilla de constitución: principios numerados con su porqué, restricciones y proceso de cambio | Quien encarga y quien construye, juntos | Consulta |
| [ejercicios/plantillas/especificacion.md](../ejercicios/plantillas/especificacion.md) | Plantilla de especificación: historias priorizadas, casos límite, requisitos EARS y criterios de éxito | Quien pide el software, con ayuda de quien construye | Consulta |
| [ejercicios/plantillas/lista-de-aclaraciones.md](../ejercicios/plantillas/lista-de-aclaraciones.md) | Plantilla de registro de preguntas y respuestas, con su impacto en la especificación | Quien construye pregunta, quien encarga responde | Consulta |
| [ejercicios/plantillas/plan-tecnico.md](../ejercicios/plantillas/plan-tecnico.md) | Plantilla de plan técnico: decisiones, estructura, modelo de datos, contratos y comprobación contra la constitución | Quien construye | Consulta |
| [ejercicios/plantillas/tareas.md](../ejercicios/plantillas/tareas.md) | Plantilla de lista de tareas por fases, con las marcas `[P]` y `[HUn]` | Quien construye | Consulta |
| [ejercicios/plantillas/lista-de-verificacion.md](../ejercicios/plantillas/lista-de-verificacion.md) | Plantilla de preguntas sí/no para revisar la calidad de una especificación | Quien no escribió la especificación | Consulta |
| [ejercicios/soluciones/README.md](../ejercicios/soluciones/README.md) | Índice de soluciones y recordatorio de que son ejemplos, no la única respuesta correcta | Todos | ~2 min · 🟢 |
| [ejercicios/soluciones/01-solicitud-de-vacaciones/especificacion.md](../ejercicios/soluciones/01-solicitud-de-vacaciones/especificacion.md) | Especificación completa y ejemplar de «Solicitud de vacaciones», la del ejercicio 01 | Quien haya hecho el 01 | ~12 min · 🟢 |
| [ejercicios/soluciones/02-requisitos-ears-resueltos.md](../ejercicios/soluciones/02-requisitos-ears-resueltos.md) | Las doce reescrituras, la clasificación por patrón y el «caza el error», comentados | Quien haya hecho el 02 | ~10 min · 🟢 |
| [ejercicios/soluciones/03-reserva-salas/README.md](../ejercicios/soluciones/03-reserva-salas/README.md) | Qué contiene el ejemplo canónico de ReservaSalas, en qué orden leerlo y cómo se generó | Junior y quien quiera un ejemplo completo | ~25 min · 🟡 |
| [ejercicios/soluciones/03-reserva-salas/constitution.md](../ejercicios/soluciones/03-reserva-salas/constitution.md) | La constitución de ReservaSalas: sus cinco principios | Todos | Consulta |
| [ejercicios/soluciones/03-reserva-salas/spec.md](../ejercicios/soluciones/03-reserva-salas/spec.md) | La especificación de referencia: historias P1-P3, requisitos RF-001 a RF-012 en EARS y criterios de éxito | Todos | Consulta |
| [ejercicios/soluciones/03-reserva-salas/aclaraciones.md](../ejercicios/soluciones/03-reserva-salas/aclaraciones.md) | Las cinco preguntas del asistente de IA y las respuestas de Ana | Todos | Consulta |
| [ejercicios/soluciones/03-reserva-salas/plan.md](../ejercicios/soluciones/03-reserva-salas/plan.md) | El plan técnico: tecnología elegida, estructura, modelo de datos, contratos y decisiones justificadas | Perfiles técnicos | Consulta |
| [ejercicios/soluciones/03-reserva-salas/tasks.md](../ejercicios/soluciones/03-reserva-salas/tasks.md) | La lista de tareas por fases e historias de usuario, con las marcas `[P]` y `[HUn]` | Perfiles técnicos | Consulta |
| [ejercicios/soluciones/03-reserva-salas/checklist.md](../ejercicios/soluciones/03-reserva-salas/checklist.md) | La lista de verificación de calidad de la especificación, ya pasada y marcada | Todos | Consulta |
| [ejercicios/soluciones/05-especificacion-arreglada.md](../ejercicios/soluciones/05-especificacion-arreglada.md) | Lista numerada de problemas con su explicación y la especificación corregida | Quien haya hecho el 05 | ~15 min · 🟡 |
| [charla/README.md](../charla/README.md) | Índice de la carpeta: qué hay para presentar SDD o para facilitar un taller | Facilitadores | ~3 min · 🟢 |
| [charla/guion-20-minutos.md](../charla/guion-20-minutos.md) | Guion minuto a minuto de la charla de 20 minutos: qué decir, qué mostrar y posibles preguntas | Quien presenta SDD a la empresa | ~15 min · 🟢 |
| [charla/guia-del-facilitador.md](../charla/guia-del-facilitador.md) | Cómo formar a un equipo con este material: formatos, agendas, adaptación al público y cómo medir si ha funcionado | Quien organiza un taller o un itinerario | ~15 min · 🟢 |

## En tres frases

1. El repositorio tiene cinco partes: la portada y la guía de contribución en la raíz, la teoría en `docs/`, los dibujos en `diagramas/`, la práctica en `ejercicios/` y el material para presentarlo en `charla/`.
2. No hace falta leerlo todo: cada perfil tiene su itinerario, desde unas tres horas para managers, RRHH y negocio hasta varios días de práctica para quien programa, y los diagramas de esta página lo recorren paso a paso con sus enlaces.
3. Cuando dudes de qué fichero abrir, la tabla final te dice de qué va cada uno, para quién es y cuánto se tarda.

## Siguiente paso

Vuelve a la [portada del repositorio](../README.md) y elige tu itinerario. Si quieres repasar la teoría desde el principio, empieza por [El problema del vibe coding](../docs/01-el-problema-del-vibe-coding.md).

---

⬅️ [Anterior: Anatomía de un requisito EARS](05-anatomia-de-un-requisito-ears.md) · 🏠 [Índice de diagramas](README.md)
