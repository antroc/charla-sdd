# El problema del *vibe coding*

> **Para quién:** todos los perfiles (managers, RRHH, negocio y quien programa) · **Tiempo de lectura:** ~8 min · **Nivel:** 🟢 básico

Este es el primer documento del itinerario. Cuenta qué pasa cuando se construye software con un asistente de IA sin un texto claro que diga qué tiene que hacer, y por qué eso acaba costando tiempo y dinero a la empresa. No hace falta saber programar para seguirlo: basta con haber pedido alguna vez que te hicieran algo.

**Qué vas a encontrar:**

- [Qué es el vibe coding](#qué-es-el-vibe-coding)
- [Por qué engancha](#por-qué-engancha)
- [Qué pasa después](#qué-pasa-después)
- [ReservaSalas v0: la historia de Luis y Ana](#reservasalas-v0-la-historia-de-luis-y-ana)
- [La reforma sin plano](#la-reforma-sin-plano)
- [Lo que le cuesta a la empresa](#lo-que-le-cuesta-a-la-empresa)
- [Síntomas y causa raíz](#síntomas-y-causa-raíz)
- [Tres preguntas antes de aceptar una demo](#tres-preguntas-antes-de-aceptar-una-demo)
- [El problema no es el asistente de IA](#el-problema-no-es-el-asistente-de-ia)

## Qué es el *vibe coding*

Imagina esta escena. Luis, programador junior, abre su asistente de programación con IA y escribe: «Hazme una aplicación para reservar las salas de reuniones de la empresa». Treinta segundos después tiene una pantalla con un calendario, una lista de salas y un botón de «Reservar».

Pide un cambio: «que se vea en qué planta está cada sala». Luego otro: «que avise si la sala está ocupada». Luego otro. Cada petición es una frase suelta, escrita según se le ocurre.

Eso es el *vibe coding*: programar a golpe de instrucciones sueltas, improvisando con el asistente de IA. Se pide lo que apetece en cada momento, se mira si «parece que funciona» y se sigue pidiendo. No existe ningún texto que diga qué tiene que hacer el sistema, para quién, con qué límites ni por qué.

El nombre viene de *vibe*, «sensación»: programas guiándote por la sensación de que va bien, no por una comprobación. Cada una de esas peticiones es un *prompt* (la instrucción que le escribes al asistente), y en el *vibe coding* los *prompts* son lo único que existe: no se guardan, no se revisan y nadie más los lee.

> [!NOTE]
> Para un experimento de una tarde, una demostración o un prototipo que se va a tirar, el *vibe coding* está bien. El problema empieza cuando ese prototipo se convierte, sin que nadie lo decida, en «la aplicación que usa toda la empresa».

## Por qué engancha

Si solo tuviera inconvenientes, nadie lo haría. Engancha por tres motivos muy humanos.

- **Es rápido.** En minutos hay algo en pantalla que se puede enseñar. Comparado con semanas de reuniones y documentos, parece un milagro.
- **Es divertido.** Pides, aparece, pides otra cosa, aparece. Es la sensación de progreso continuo de un videojuego.
- **Parece magia.** La primera vez que un asistente de IA genera en segundos una pantalla que funciona, cuesta no pensar que el trabajo ya está hecho.

Y hay un cuarto motivo, más serio: por primera vez, alguien que no programa puede obtener software hablando. Esa puerta abierta es buena. Lo que falla no es la puerta, sino entrar sin saber qué se busca.

## Qué pasa después

La semana uno es magnífica. El problema suele aparecer hacia la tercera semana, cuando la aplicación ya la usa gente de verdad.

### La «demo bonita» que no aguanta

La pantalla que impresionó en la reunión funcionaba con tres salas y dos reservas de prueba. Con doce salas, doscientas personas y reservas que se cruzan, empiezan a pasar cosas raras: una reserva que desaparece, dos equipos en la misma sala, un mensaje de error en rojo que nadie entiende.

### El código que nadie entiende

El asistente ha escrito cientos de líneas de código en un orden que solo tenía sentido en la conversación de aquel día. Luis no las leyó a fondo (iba rápido) y nadie más las ha visto. Cuando algo falla, la única opción es volver a preguntarle al asistente, que tampoco recuerda aquella conversación.

### Cada corrección rompe otra cosa

Se pide «evita que dos personas puedan reservar la misma sala a la misma hora» y, de paso, el asistente cambia cómo se guardan las horas. Ahora el solapamiento está resuelto, pero las reservas de más de una hora han dejado de funcionar. Se arregla eso y se rompe la lista de «mis reservas». Cada parche se apoya en el anterior, y nadie tiene una lista de lo que no debe romperse.

### Nadie sabe qué debía hacer el sistema

Es el síntoma más grave y el menos visible. Cuando Ana pregunta «¿las reservas pueden durar más de cuatro horas?», no hay dónde mirar. Ni Luis ni el asistente lo decidieron: simplemente salió así. El comportamiento del sistema es el que es, no el que alguien quiso que fuera.

## ReservaSalas v0: la historia de Luis y Ana

ReservaSalas es el ejemplo que acompaña a todo este repositorio: una pequeña aplicación interna para reservar las 12 salas de reuniones de la empresa, repartidas en 3 plantas. La versión buena, hecha con SDD (*Spec-Driven Development*, desarrollo guiado por especificaciones), la verás en los documentos siguientes. Esta es la historia de la versión anterior, la «v0», antes de que Luis y Ana conocieran SDD.

**El encargo.** Ana, responsable de Oficina, está harta de la hoja de cálculo compartida: dos equipos en la misma sala, salas reservadas que se quedan vacías y reservas «fantasma» de las que nadie sabe quién es el responsable. Se lo pide a Luis de pasada, en un pasillo: «¿Puedes hacernos algo para reservar salas? Con esos asistentes de IA eso se hace en una tarde, ¿no?».

**La tarde.** Luis le escribe al asistente «hazme una app de reservas de salas» y, efectivamente, en una tarde tiene algo. Lo enseña el viernes. Ana está encantada.

**El lunes.** Marta, manager de un equipo, reserva la sala Mediterráneo de 10:00 a 11:00. Jorge, de RRHH, la reserva de 10:30 a 11:30. A las 10:30 se encuentran los dos equipos en la puerta. El asistente nunca supo que dos reservas no pueden cruzarse, porque nadie se lo dijo.

**La segunda semana.** Luis pide al asistente que impida los choques. Lo hace, pero de paso fija las reservas a bloques de una hora exacta, porque en algún *prompt* Luis escribió «bloques de una hora» pensando en otra cosa. Las reuniones de hora y media ya no caben. Además, en la lista aparecen dos salas, «Baltico» y «Báltico», una sin tilde y otra con ella: alguien escribió el nombre dos veces y el sistema las tomó por salas distintas.

**La cuarta semana.** Ana pregunta por qué no se puede reservar antes de las 09:00, si la oficina abre a las 08:00. Nadie lo decidió: el asistente supuso un horario «normal» y nadie lo revisó. Luis busca en el historial del chat, pero la conversación de aquella tarde ya no está. Para cambiarlo hay que leer el código, y leerlo lleva más que haberlo escrito.

**El final.** Luis cambia de equipo. La aplicación sigue en marcha, pero nadie sabe qué hace exactamente ni se atreve a tocarla. Ana vuelve, en parte, a la hoja de cálculo.

Nada de esto es culpa de Luis ni del asistente. Lo que faltaba cabe en una lista corta:

- **Un texto que dijera qué tenía que hacer la aplicación**: salas con nombre único, horario de 08:00 a 20:00, máximo 4 horas, dos reservas de la misma sala no pueden solaparse, toda reserva tiene un responsable visible. Esa es, muy resumida, la [especificación](../ejercicios/soluciones/03-reserva-salas/spec.md) (`spec.md`) de ReservaSalas que verás más adelante.
- **Unas reglas del juego acordadas antes de empezar**: qué datos se guardan y cuáles no, y que nada se da por hecho sin una prueba automática. Eso es la constitución del proyecto (`constitution.md`).
- **Una lista de lo que no debía romperse**, para comprobarla después de cada cambio. Eso son las pruebas automáticas (pequeños programas que comprueban solos, después de cada cambio, que la aplicación sigue haciendo lo que debe), y se escriben a partir de la especificación.
- **Un sitio donde quedaran las decisiones** («bloques de una hora», «solo se reserva a partir de las 09:00»), en vez de en un chat que desaparece.

Los documentos siguientes explican cómo se consigue cada una de estas cuatro cosas.

## La reforma sin plano

Si no programas, la analogía más útil es una reforma en casa.

Imagina que encargas la reforma de la cocina a un albañil rapidísimo y muy voluntarioso, sin plano y sin presupuesto. Le dices «quiero la cocina más grande» y el lunes ya ha tirado un tabique. El martes le comentas que la nevera no cabe donde la ha puesto; la mueve, y para eso desvía una tubería. El jueves descubres que el baño se ha quedado sin agua. Cada día arregla lo del día anterior, y cada arreglo genera el problema del siguiente.

¿El albañil es malo? No: es rápido y hace lo que le pides. El problema es que nadie escribió qué tenía que tener la cocina (cuántos fuegos, dónde va la nevera, qué tabique es de carga) ni cuánto podía costar. Sin plano, cada decisión se toma sobre la marcha y se olvida al momento.

Con el software y un asistente de IA pasa igual, solo que este albañil trabaja a una velocidad que hace el desorden todavía más rápido. El plano es la especificación; el presupuesto y las decisiones de obra son el plan técnico. El [documento siguiente](02-que-es-sdd.md) explica qué contiene cada uno.

## Lo que le cuesta a la empresa

Los costes del *vibe coding* son invisibles al principio, porque la primera semana solo se ven beneficios. Después aparecen en cuatro formas.

| Coste | En qué se nota | Ejemplo en ReservaSalas v0 |
|---|---|---|
| **Retrabajo** | Se hace, se deshace y se vuelve a hacer lo mismo varias veces | Los choques de sala se «arreglaron» tres veces, y cada arreglo rompió otra cosa |
| **Deuda técnica** | Atajos que hoy ahorran una hora y dentro de unos meses cuestan una semana | Las salas «Baltico» y «Báltico» obligan a limpiar datos cada vez que se toca la lista de salas |
| **Dependencia de una persona** | Solo quien lo hizo sabe cómo funciona; si se va, nadie se atreve a tocarlo | Cuando Luis cambia de equipo, la aplicación se queda huérfana |
| **Riesgo con los datos** | El sistema guarda o enseña datos que nadie pidió, porque nadie dijo cuáles hacían falta | El asistente añadió «por si acaso» un campo de teléfono y un listado de todas las reservas con el nombre de cada persona, visible para cualquiera |

«Deuda técnica» es la expresión que usamos para los atajos acumulados: como una deuda, se puede vivir con ella un tiempo, pero cobra intereses, y cuanto más tarde se paga, más cuesta. El [glosario](10-glosario.md) recoge esta y otras palabras del repositorio.

> [!WARNING]
> El cuarto coste es el más serio. Una aplicación hecha a golpe de *prompt* puede acabar guardando datos personales que nadie decidió guardar, o enseñándolos a quien no debía. En SDD eso se decide por escrito desde el principio, en la constitución del proyecto (mira el principio «Datos mínimos» en la [constitución de ReservaSalas](../ejercicios/soluciones/03-reserva-salas/constitution.md)).

## Síntomas y causa raíz

Cuando una aplicación hecha con *vibe coding* empieza a dar problemas, lo habitual es culpar al asistente o a la persona. Casi siempre la causa está más abajo: no existe una especificación.

| Síntoma | Lo que parece | Causa raíz |
|---|---|---|
| «Ayer funcionaba y hoy no» | El asistente es poco fiable | Nadie escribió qué comportamiento había que conservar, así que no hay pruebas que lo vigilen |
| Dos equipos en la misma sala | Un fallo de programación | Nadie definió qué es un solapamiento ni qué tiene que pasar cuando ocurre |
| «¿Por qué solo se puede reservar una hora?» | Una decisión rara del asistente | La decisión no está escrita en ningún sitio: salió de un *prompt* que nadie guardó |
| Solo Luis sabe tocar el código | Luis es imprescindible | No hay ningún documento que explique qué hace el sistema; el conocimiento vive en un chat |
| Cada cambio tarda más que el anterior | La aplicación «se ha complicado» | Sin un texto de referencia, cada parche se apila sobre el anterior sin saber qué protege |
| La aplicación guarda datos que nadie pidió | El asistente «se pasó» | Nadie fijó qué datos hacen falta y cuáles no |

Fíjate en la columna de la derecha: todas las filas terminan en lo mismo. Falta un texto que diga qué tiene que hacer el sistema y qué no.

> [!TIP]
> Si ya tienes en marcha una aplicación hecha así, no hace falta tirarla. El primer paso es escribir su especificación a partir de lo que hace hoy (y de lo que debería hacer), y seguir con SDD desde ahí. Qué hacer con los proyectos que ya existen se trata en [Preguntas frecuentes](09-preguntas-frecuentes.md).

## Tres preguntas antes de aceptar una demo

Si alguien te enseña una aplicación hecha en una tarde con un asistente de IA, no hace falta saber programar para saber si estás ante *vibe coding*. Basta con tres preguntas.

1. **¿Dónde está escrito lo que hace?** Si la respuesta es «en el código» o «en el chat con el asistente», no está escrito.
2. **¿Qué pasa cuando dos personas hacen lo mismo a la vez, o cuando alguien se equivoca?** Una demo enseña el camino feliz; los problemas viven en los casos límite: una reserva que se solapa con otra, una fecha pasada, una sala en mantenimiento.
3. **¿Cómo sabremos que sigue funcionando después del próximo cambio?** Si no hay pruebas automáticas, la respuesta real es «probándolo todo a mano otra vez».

Ninguna de las tres preguntas pide ver código. Las tres se responden con una especificación.

## El problema no es el asistente de IA

Es tentador sacar la conclusión equivocada: «los asistentes de IA no sirven para hacer software serio». No es eso. En la historia de ReservaSalas v0 el asistente hizo, cada vez, exactamente lo que se le pidió. El fallo estuvo en lo que no se le pidió.

Lo que faltaba es lo que en cualquier otro encargo llamaríamos un contrato: un texto claro, que todas las partes pueden leer y aceptar, que dice qué se va a construir, para qué, con qué límites y cómo sabremos que está bien. Con un albañil se llama plano y presupuesto. Con un asistente de IA se llama especificación.

Esa es la idea del SDD, el desarrollo guiado por especificaciones: escribir primero ese contrato en lenguaje natural y dejar que el asistente trabaje a partir de él, en vez de a partir de frases sueltas. No elimina los errores (ningún método lo hace), pero convierte «salió así» en «lo decidimos así, y está escrito aquí».

Si prefieres verlo dibujado, el [diagrama 01](../diagramas/01-vibe-coding-vs-sdd.md) compara los dos caminos.

## En tres frases

1. El *vibe coding* es programar a golpe de instrucciones sueltas con un asistente de IA: rápido y divertido al principio, pero sin ningún texto que diga qué tiene que hacer el sistema.
2. Sus costes llegan tarde y en silencio: retrabajo, deuda técnica, dependencia de una persona y riesgo con los datos; casi todos los síntomas tienen la misma causa raíz, la falta de una especificación.
3. El problema no es el asistente de IA, sino la ausencia de un contrato claro; escribirlo antes de pedir código es el punto de partida de SDD.

## Siguiente paso

Continúa con [Qué es SDD](02-que-es-sdd.md), donde se explica en qué consiste ese contrato y cómo cambia la forma de trabajar.

---

🏠 [Índice de documentación](README.md) · ➡️ [Siguiente: Qué es SDD](02-que-es-sdd.md)
