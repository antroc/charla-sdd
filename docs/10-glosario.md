# Glosario

> **Para quién:** toda la empresa, para consultar cualquier palabra que no te suene · **Tiempo de lectura:** ~15 min de principio a fin (o consulta puntual) · **Nivel:** 🟢 básico

[A](#a) · [B](#b) · [C](#c) · [D](#d) · [E](#e) · [F](#f) · [G](#g) · [H](#h) · [I](#i) · [J](#j) · [K](#k) · [L](#l) · [M](#m) · [P](#p) · [Q](#q) · [R](#r) · [S](#s) · [T](#t) · [U](#u) · [V](#v)

Este glosario es para consultar, no para leerlo como un capítulo. Recoge los términos que aparecen por el curso y explica qué significan aquí, con un enlace al lugar donde se usan con más contexto.

Los ejemplos siguen siendo los de ReservaSalas. Las palabras inglesas habituales en el sector van en cursiva y los nombres de ficheros o comandos aparecen como código.

> [!TIP]
> Si una palabra no aparece como entrada, búscala con la búsqueda del navegador (Ctrl+F, o Cmd+F en Mac): muchas definiciones explican de paso otras palabras, como *prueba unitaria*, *Dado / Cuando / Entonces* o `specify init`.

## A

- **Aclarar (aclaración)** — Paso 2 del flujo: el asistente de IA relee la especificación, detecta dudas y hace preguntas, de una en una (en Spec Kit, hasta cinco). Quien encarga el proyecto responde por escrito y cada respuesta, una aclaración, se incorpora a la especificación. Ver [El flujo paso a paso](03-el-flujo-paso-a-paso.md#paso-2-aclarar).
- **Agente** — Así llaman muchas herramientas al asistente de IA que, además de responder, actúa por su cuenta: crea ficheros, ejecuta órdenes y lanza pruebas. Spec Kit usa la expresión inglesa *coding agent*; en este material decimos siempre asistente de IA. Ver [Herramientas](07-herramientas.md#cómo-se-inicia-un-proyecto).
- **Analizar** — Paso 5 del flujo: la última comprobación antes de escribir código. Se cruzan especificación, plan, tareas y constitución en busca de huecos y contradicciones (un requisito sin tarea, una tarea que nadie pidió) y se pasan las listas de verificación. Ver [El flujo paso a paso](03-el-flujo-paso-a-paso.md#paso-5-analizar).
- **API** — Una conexión para que otros programas usen una aplicación sin pasar por sus pantallas. Es tecnología, así que va en el plan técnico y nunca en la especificación; en ReservaSalas, el plan añade una pequeña API para que las pruebas automáticas no dependan de las pantallas. Ver [El flujo paso a paso](03-el-flujo-paso-a-paso.md#paso-3-planificar).
- **Artefacto** — Cada documento que deja escrito un paso de SDD. Son cinco (constitución, especificación, plan técnico, lista de tareas y lista de verificación), más el registro de aclaraciones; cada uno alimenta al siguiente o comprueba al anterior. Ver [Los artefactos](04-los-artefactos.md) y el [diagrama 03](../diagramas/03-artefactos-y-relaciones.md#cómo-se-alimentan-los-artefactos).
- **Asistente de IA** — Programa con el que conversas por escrito y que redacta, pregunta y genera código a partir de tus instrucciones; los de programación, además, leen y escriben ficheros y ejecutan órdenes. En SDD participa en todos los pasos, pero nunca aprueba: eso lo hacen las personas. Ver [Roles: quién hace qué](06-roles-quien-hace-que.md#el-asistente-de-ia).

## B

- **Bandera de un comando** — Opción que se añade a un comando de terminal para cambiar lo que hace; también se llama parámetro y empieza por dos guiones. En `specify init reserva-salas --integration claude`, la bandera `--integration` dice qué asistente de IA hay que configurar. Ver [Herramientas](07-herramientas.md#cómo-se-inicia-un-proyecto).

## C

- **Casilla de verificación** — El cuadrado que se marca cuando algo está hecho. En los ficheros del repositorio se escribe `- [ ]` sin marcar y `- [x]` marcada (Spec Kit usa `[X]` para cada tarea terminada); aparece en los pasos de los ejercicios, en las tareas y en las listas de verificación. Ver [Los artefactos](04-los-artefactos.md#la-lista-de-tareas).
- **Caso límite** — Situación rara o incómoda que el sistema tiene que resolver bien: dos personas que reservan la misma sala a la vez, una fecha pasada, una sala en mantenimiento. Las demos enseñan el caso en que todo va bien; los problemas suelen vivir aquí. Ver [El problema del *vibe coding*](01-el-problema-del-vibe-coding.md#tres-preguntas-antes-de-aceptar-una-demo).
- **Código abierto** — Programa cuyo código puede ver, usar y adaptar cualquiera, según lo que permita su licencia. Spec Kit es gratuito y de código abierto, con licencia MIT, que permite usarlo también en empresas. Ver [Herramientas](07-herramientas.md#github-spec-kit).
- **Comando** — Orden escrita que se le da a un programa. En este material hay dos tipos: los de terminal, que empiezan por `specify` (como `specify init`), y los que se escriben en el chat del asistente de IA, como `/speckit.specify`, que según el asistente aparece como `/speckit-specify` o `$speckit-specify`. Ver [Herramientas](07-herramientas.md#los-comandos-del-asistente).
- ***Commit*** — Cada versión guardada en el historial de un repositorio Git, con un mensaje que dice qué ha cambiado; «hacer *commit*» es guardarla. Conviene hacerlo antes de regenerar nada, para poder comparar después. Ver [Buenas prácticas y errores comunes](08-buenas-practicas-y-errores-comunes.md#al-implementar-y-después-paso-6-y-siguientes).
- **Constitución** — Los principios innegociables de un proyecto (`constitution.md`), como «sencillez primero» o «datos mínimos», que la especificación, el plan, las tareas y el código tienen que respetar. Se escribe una vez por proyecto, en el paso 0, y se cambia poco y por escrito. Ver [Los artefactos](04-los-artefactos.md#la-constitución).
- **Contrato** — Texto claro, que todas las partes pueden leer y aceptar, que dice qué se va a construir, con qué límites y cómo sabremos que está bien. En SDD ese contrato entre quien pide el software y quien lo construye es la especificación. Ver [El problema del *vibe coding*](01-el-problema-del-vibe-coding.md#el-problema-no-es-el-asistente-de-ia).
- **Contrato de API** — Parte del plan técnico que describe, operación por operación, qué entra y qué sale: por ejemplo, qué datos hacen falta para crear una reserva y qué responde la aplicación si la sala está ocupada. Spec Kit los guarda en la carpeta `contracts/`. Ver [Los artefactos](04-los-artefactos.md#el-plan-técnico).
- **Criterio de aceptación** — Ejemplo concreto, con nombres, salas y horas, que se comprueba con un sí o un no. Se escribe en tres partes: dado (la situación de partida), cuando (lo que ocurre) y entonces (lo que hace el sistema); en inglés, *Given / When / Then*. Ver [Escribir requisitos claros (EARS)](05-escribir-requisitos-claros-ears.md#de-requisito-a-criterio-de-aceptación).
- **Criterio de éxito** — Resultado medible, con cifra y sin tecnología, que dice cómo sabremos, meses después, que el cambio ha merecido la pena: por ejemplo, CE-001, «reservar una sala lleva menos de 1 minuto». No comprueba una situación concreta, como el criterio de aceptación, sino el resultado. Ver [Escribir requisitos claros (EARS)](05-escribir-requisitos-claros-ears.md#3-la-frase-que-no-es-un-requisito).

## D

- **Deuda técnica** — Atajos acumulados en un programa que hoy ahorran una hora y dentro de unos meses cuestan una semana. Como una deuda, se puede vivir con ella un tiempo, pero cobra intereses: cuanto más tarde se paga, más cuesta. Ver [El problema del *vibe coding*](01-el-problema-del-vibe-coding.md#lo-que-le-cuesta-a-la-empresa).

## E

- **EARS** — Forma sencilla y estructurada de redactar requisitos (*Easy Approach to Requirements Syntax*, propuesta en 2009): cinco plantillas de frase, siempre con «el sistema deberá» y, salvo en la más simple, una palabra clave en mayúsculas (CUANDO, MIENTRAS, SI/ENTONCES, DONDE). Ver [Escribir requisitos claros (EARS)](05-escribir-requisitos-claros-ears.md#qué-es-ears) y el [diagrama 05](../diagramas/05-anatomia-de-un-requisito-ears.md).
- **Entidad clave** — Cada «cosa» de la que el sistema guarda información, con sus datos, descrita sin decir cómo se guarda. En ReservaSalas son tres: Sala, Reserva y Persona. Ver [Los artefactos](04-los-artefactos.md#la-especificación).
- **Especificación** — El documento central de SDD (`spec.md`; en inglés, *spec*): qué queremos y por qué, en lenguaje natural y sin tecnología. Recoge historias de usuario con prioridad, requisitos, criterios de éxito y casos límite, y es la fuente de verdad del proyecto. Ver [Los artefactos](04-los-artefactos.md#la-especificación).
- **Extensión de Spec Kit** — Complemento opcional que añade comandos a Spec Kit; por ejemplo, la extensión `git` crea el repositorio Git y una rama por funcionalidad. Se instala con `specify extension add` seguido de su nombre, y para seguir este material no hace falta ninguna. Ver [Herramientas](07-herramientas.md#github-spec-kit).

## F

- **FastAPI** — Pieza de programación en Python (un lenguaje de programación) que sirve las páginas web de una aplicación y atiende lo que envía quien la usa. Es una de las tecnologías que eligió Luis en el plan técnico de ReservaSalas; no hace falta conocerla para seguir el método. Ver [Roles: quién hace qué](06-roles-quien-hace-que.md#qué-cambia-en-el-trabajo-de-quien-programa).
- **Fuente de verdad** — La referencia que usamos para decidir qué comportamiento se espera del sistema. En el enfoque de este curso ese papel lo tiene la especificación: si cambia la necesidad, se actualiza allí; si la especificación sigue siendo correcta y el código no la cumple, el fallo está en la implementación. Ver [Qué es SDD](02-que-es-sdd.md#qué-cambia-la-especificación-deja-de-ser-documentación-decorativa).
- **Fuera de alcance** — Sección de la especificación con lo que se decide expresamente no hacer en esta versión: en ReservaSalas, las reservas recurrentes o el control de asistencia. Dejarlo escrito evita que alguien lo construya «por si acaso» o lo dé por incluido. Ver [Buenas prácticas y errores comunes](08-buenas-practicas-y-errores-comunes.md#al-especificar-pasos-0-a-2).

## G

- **Git y GitHub** — Git es el programa que guarda el historial de versiones de un proyecto: quién cambió qué y cuándo, con la posibilidad de volver atrás. GitHub es un servicio web donde se guardan y comparten repositorios Git, y la organización que publica Spec Kit. Ver [Herramientas](07-herramientas.md#qué-necesitas).

## H

- **Historia de usuario** — Lo que un tipo de persona quiere conseguir con el sistema, contado en unas líneas: «como empleado, quiero pedir días libres indicando las fechas, para que mi manager los apruebe». Cada una lleva prioridad y criterios de aceptación, y se numera HU1, HU2… Ver [El flujo paso a paso](03-el-flujo-paso-a-paso.md#paso-1-especificar).

## I

- **Implementar** — Paso 6 del flujo: el asistente de IA ejecuta las tareas una a una y escribe el código y sus pruebas, mientras la persona lee, prueba y, si algo no cuadra, corrige la especificación y regenera. En Spec Kit, `/speckit.implement` y después `/speckit.converge`, que comprueba que no falte nada. Ver [El flujo paso a paso](03-el-flujo-paso-a-paso.md#paso-6-implementar).
- **Iteración** — Cada vuelta de un ciclo corto de trabajo: especificar algo pequeño, construirlo, probarlo y corregir lo aprendido antes de seguir. SDD avanza así, funcionalidad a funcionalidad, en vez de planificarlo todo de golpe al principio. Ver [Qué es SDD](02-que-es-sdd.md#qué-no-es-sdd).

## J

- **Jinja2** — Sistema de plantillas que genera las páginas web (HTML) de una aplicación rellenándolas con datos antes de enviarlas al navegador. Es otra de las tecnologías del plan técnico de ReservaSalas y, como todas, va en el plan, no en la especificación. Ver [Qué es SDD](02-que-es-sdd.md#especificación-y-plan-qué-por-qué-cómo).

## K

- **Kiro** — Editor de código de AWS (el programa con el que se escribe y organiza el código) que lleva integrado un flujo del mismo tipo: especificación, diseño y tareas. No necesita Spec Kit; su herramienta de terminal, Kiro CLI, figura además entre los asistentes compatibles con Spec Kit. Ver [Herramientas](07-herramientas.md#kiro-de-aws).

## L

- **Lenguaje natural** — Castellano corriente, el de un correo o una conversación, sin código ni palabras técnicas. Es el idioma de la constitución y de la especificación, para que cualquiera pueda leerlas y aprobarlas. Ver [Qué es SDD](02-que-es-sdd.md#sdd-en-una-frase).
- **Línea de comandos** — Forma de manejar un programa escribiendo órdenes en la terminal en vez de pulsar botones. Spec Kit es una herramienta de línea de comandos: se instala y se pone en marcha así, aunque el resto del trabajo se hace en el chat del asistente de IA. Ver [Herramientas](07-herramientas.md#tres-formas-de-hacer-sdd).
- **Lista de tareas** — El plan técnico troceado en tareas pequeñas y ordenadas (`tasks.md`), agrupadas por fases y por historia de usuario. Cada tarea cabe en una línea, nombra el fichero que toca y se da por terminada con un sí o un no; se numeran T001, T002… Ver [Los artefactos](04-los-artefactos.md#la-lista-de-tareas).
- **Lista de verificación (*checklist*)** — Preguntas de sí o no que comprueban la calidad del texto de la especificación: ¿cada requisito se puede comprobar?, ¿hay casos límite? Revisa lo escrito, no el programa, y conviene que la pase alguien distinto de quien escribió la especificación. Ver [Los artefactos](04-los-artefactos.md#la-lista-de-verificación).

## M

- **Marcador `[NECESITA ACLARACIÓN: …]`** — Señal que se deja en la especificación cuando falta un dato que solo puede dar quien encarga el proyecto, en vez de inventarlo: `[NECESITA ACLARACIÓN: ¿cuántos días de antelación como máximo?]`. Spec Kit deja tres como mucho, en inglés (`NEEDS CLARIFICATION`), y pregunta por ellos. Ver [El flujo paso a paso](03-el-flujo-paso-a-paso.md#paso-1-especificar) y [Si te falta un dato](05-escribir-requisitos-claros-ears.md#si-te-falta-un-dato).
- **Modelo de datos** — Descripción de qué información guarda el sistema y cómo se relaciona: en ReservaSalas, salas, personas y reservas, con sus datos y sus reglas. Forma parte del plan técnico; Spec Kit lo pone en `data-model.md`. Ver [El flujo paso a paso](03-el-flujo-paso-a-paso.md#paso-3-planificar).
- **MVP (producto mínimo viable)** — La versión más pequeña que ya resuelve el problema principal y se puede enseñar (en inglés, *Minimum Viable Product*). Suele coincidir con la historia P1: en ReservaSalas, reservar una sala. Ver [El flujo paso a paso](03-el-flujo-paso-a-paso.md#paso-4-trocear-en-tareas).

## P

- **Plan técnico** — El documento que dice cómo se va a construir lo que pide la especificación (`plan.md`): tecnología, modelo de datos, contratos y estructura, con cada decisión comprobada contra la constitución. Es el primer artefacto en el que aparece tecnología. Ver [Los artefactos](04-los-artefactos.md#el-plan-técnico).
- **Prioridad (P1, P2, P3)** — Orden de importancia de las historias de usuario. La P1 es lo imprescindible y tiene que valer por sí sola (si solo se hiciera eso, ya serviría); la P2 y la P3 pueden esperar si falta tiempo. Ver [Buenas prácticas y errores comunes](08-buenas-practicas-y-errores-comunes.md#al-especificar-pasos-0-a-2).
- ***Prompt*** — La instrucción que le escribes al asistente de IA, en lenguaje natural. En SDD los importantes (la petición para especificar, la tecnología para planificar) quedan guardados en los artefactos, en vez de perderse en el chat. Ver [El problema del *vibe coding*](01-el-problema-del-vibe-coding.md#qué-es-el-vibe-coding).
- **Prueba automática** — Pequeño programa que comprueba solo, después de cada cambio, que la aplicación sigue haciendo lo que debe; las que revisan cada pieza pequeña por separado se llaman pruebas unitarias. En este material se escriben antes que el código y tienen que fallar hasta que la funcionalidad existe. Ver [Buenas prácticas y errores comunes](08-buenas-practicas-y-errores-comunes.md#al-planificar-y-trocear-pasos-3-a-5).
- **Prueba de contrato** — Prueba automática que comprueba que cada operación de la API responde lo acordado en su contrato: con datos correctos, la respuesta prevista; con datos que incumplen una regla (una franja ocupada, una reserva de más de 4 horas), el rechazo y el mensaje previstos. En ReservaSalas son la razón de la pequeña API del plan técnico. Ver [Buenas prácticas y errores comunes](08-buenas-practicas-y-errores-comunes.md#al-planificar-y-trocear-pasos-3-a-5).
- ***Pull request*** — Propuesta de cambios en un repositorio que otras personas revisan y comentan antes de incorporarla a la versión principal. Es la forma de entrega recomendada del reto final. Ver [Ejercicio 06: reto final](../ejercicios/06-reto-final-tu-propio-proyecto.md#opción-a-pull-request-en-un-repositorio-interno).
- **Punto de control** — Parada al final de cada fase de la lista de tareas para comprobar que lo hecho funciona antes de seguir; por ejemplo, «la historia 1 funciona de principio a fin y se puede enseñar a Ana». En Spec Kit se llama *Checkpoint*. Ver [Los artefactos](04-los-artefactos.md#la-lista-de-tareas).
- **pytest** — Herramienta que ejecuta las pruebas automáticas de un programa escrito en Python y dice cuáles pasan y cuáles fallan. Es la que usa el plan técnico de ReservaSalas; en el ejercicio 03 se lanza escribiendo `pytest` en la terminal. Ver [Ejercicio 03](../ejercicios/03-reserva-salas-paso-a-paso.md#pasos).

## Q

- **QA** — Siglas inglesas de control de calidad (*Quality Assurance*): la persona o el equipo que comprueba que la aplicación hace lo que debe. En SDD entra pronto: revisa la especificación con la lista de verificación, no solo el programa terminado. Ver [Roles: quién hace qué](06-roles-quien-hace-que.md#qa-calidad-y-pruebas).

## R

- **Rama** — Línea de trabajo paralela dentro de un repositorio Git: permite hacer cambios sin tocar la versión principal hasta que se revisan, normalmente con una *pull request*. Spec Kit no crea ramas salvo que instales su extensión `git`. Ver [Ejercicio 06: reto final](../ejercicios/06-reto-final-tu-propio-proyecto.md#pasos).
- **Regenerar** — Pedir al asistente que vuelva a producir la parte afectada después de un cambio en la especificación. No significa que todo cambio de código tenga que hacerse así: un bug de implementación puede corregirse directamente y cubrirse con una prueba. Con Spec Kit, `/speckit.converge` detecta trabajo pendiente y `/speckit.implement` ejecuta las tareas. Ver [Qué es SDD](02-que-es-sdd.md#qué-cambia-la-especificación-deja-de-ser-documentación-decorativa) y el paso 9 del [ejercicio 03](../ejercicios/03-reserva-salas-paso-a-paso.md#pasos).
- **Registro de complejidad** — Tabla del plan técnico donde se apunta, con su porqué, cada desviación de la constitución (casi siempre, algo que se sale de la regla de sencillez), junto con la alternativa más simple que se descartó (en inglés, *Complexity Tracking*). En ReservaSalas recoge la pequeña API que necesitan las pruebas de contrato. Ver [Los artefactos](04-los-artefactos.md#el-plan-técnico).
- **Repositorio** — Carpeta compartida donde se guarda un proyecto (código, documentos y artefactos) junto con su historial de versiones. En SDD, la especificación y el resto de artefactos viven en el repositorio, al lado del código. Ver [Buenas prácticas y errores comunes](08-buenas-practicas-y-errores-comunes.md#al-implementar-y-después-paso-6-y-siguientes).
- **Requisito (funcional y no funcional)** — Lo que el sistema tiene que hacer o cumplir. El funcional dice qué hace en una situación concreta, en una frase comprobable (RF-001, RF-002…); el no funcional, cómo de bien lo hace (rapidez, accesibilidad), y aquí suele escribirse como criterio de éxito con cifra o como principio de la constitución. Ver [Escribir requisitos claros (EARS)](05-escribir-requisitos-claros-ears.md#reglas-de-oro).
- **ReservaSalas** — La aplicación ficticia que acompaña a todo el repositorio: una herramienta interna para reservar las 12 salas de reuniones de la empresa, que encarga Ana y construye Luis siguiendo SDD. El ejemplo sin código es «Solicitud de vacaciones». Ver [El problema del *vibe coding*](01-el-problema-del-vibe-coding.md#reservasalas-v0-la-historia-de-luis-y-ana) y [la solución completa](../ejercicios/soluciones/03-reserva-salas/README.md).
- **Rúbrica** — Tabla para puntuar un trabajo: una fila por criterio y una columna por nivel, con lo que hay que cumplir para alcanzar cada uno. El reto final la usa para que te puntúes del 1 al 4 en cinco criterios. Ver [Ejercicio 06: reto final](../ejercicios/06-reto-final-tu-propio-proyecto.md#rúbrica-de-autoevaluación).

## S

- **SDD** — Siglas de *Spec-Driven Development*, desarrollo guiado por especificaciones: forma de construir software en la que primero se escribe, en lenguaje natural, qué queremos y por qué, y a partir de ese texto el asistente de IA genera el plan técnico, las tareas y el código, con una persona revisando cada paso. Ver [Qué es SDD](02-que-es-sdd.md#sdd-en-una-frase) y [El flujo paso a paso](03-el-flujo-paso-a-paso.md#el-flujo-de-un-vistazo).
- ***Skill*** — Carpeta de instrucciones que un asistente de IA carga al arrancar y que le enseña a hacer una tarea concreta. Muchos asistentes reciben así los comandos de Spec Kit, una *skill* por comando, y los escriben con guion: `/speckit-specify`. Ver [Herramientas](07-herramientas.md#cómo-se-escriben-según-el-asistente).
- **Spec Kit** — Conjunto de herramientas gratuito y de código abierto de GitHub para seguir SDD con un asistente de IA. Se instala como la herramienta de terminal `specify`, que prepara el proyecto (`specify init`) y añade al asistente los comandos `/speckit.*`; Claude Code, GitHub Copilot, Cursor o Gemini CLI son ejemplos de asistentes compatibles. Ver [Herramientas](07-herramientas.md#github-spec-kit).
- **SQLite** — Base de datos (el almacén ordenado donde una aplicación guarda su información) que cabe en un único fichero y no necesita un servidor aparte. Es la que eligió el plan técnico de ReservaSalas; en la especificación no aparece, porque es tecnología. Ver [Buenas prácticas y errores comunes](08-buenas-practicas-y-errores-comunes.md#doce-errores-comunes).

## T

- **Tarea paralelizable (`[P]`)** — Tarea que se puede hacer a la vez que otras de su fase, porque toca un fichero distinto y no depende de ninguna pendiente. Se marca con `[P]` en la lista de tareas; dos tareas `[P]` que tocan el mismo fichero son un error. Ver [Los artefactos](04-los-artefactos.md#la-lista-de-tareas).
- **Terminal** — La ventana de texto del ordenador donde se escriben órdenes, una por línea (en Windows, PowerShell). Con Spec Kit, en la terminal se instala la herramienta y se crea el proyecto; el resto del flujo se hace en el chat del asistente de IA. Ver [El flujo paso a paso](03-el-flujo-paso-a-paso.md#cada-herramienta-lo-llama-a-su-manera).

## U

- **`uv`** — Gestor de paquetes: un programa que descarga e instala herramientas de Python y lo que estas necesitan para funcionar. Es la forma recomendada de instalar Spec Kit, con `uv tool install specify-cli`. Ver [Ejercicio 00](../ejercicios/00-preparacion-del-entorno.md#pasos-de-la-vía-b-entorno-completo-con-spec-kit).

## V

- ***Vibe coding*** — Programar a golpe de instrucciones sueltas, improvisando con el asistente de IA: se pide, se mira si «parece que funciona» y se sigue pidiendo, sin ningún texto que diga qué tiene que hacer el sistema. Es rápido el primer día y caro a los tres meses. Ver [El problema del *vibe coding*](01-el-problema-del-vibe-coding.md#qué-es-el-vibe-coding) y el [diagrama 01](../diagramas/01-vibe-coding-vs-sdd.md).

## En tres frases

1. Este glosario reúne, en orden alfabético, sesenta y dos palabras del repositorio con una definición en lenguaje llano y un enlace al documento, diagrama o ejercicio donde se explican con calma.
2. Las palabras centrales son pocas: SDD, especificación (la fuente de verdad), constitución, plan técnico, lista de tareas, lista de verificación, aclarar, analizar, implementar y regenerar; casi todas las demás son piezas de estas.
3. Los nombres de herramientas (Spec Kit, Kiro, FastAPI, SQLite, pytest, `uv`) cambian con el tiempo; el método no: escribir primero qué queremos y por qué, y corregir la especificación, no el código, cuando algo falla.

## Siguiente paso

Has llegado al final de la documentación. Vuelve al [índice de documentación](README.md) para elegir otro documento o a la [portada del repositorio](../README.md) para ver las rutas de lectura por perfil, los diagramas y los ejercicios.

---

⬅️ [Anterior: Preguntas frecuentes](09-preguntas-frecuentes.md) · 🏠 [Índice de documentación](README.md)
