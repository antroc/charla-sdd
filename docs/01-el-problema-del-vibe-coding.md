# El problema del *vibe coding*

> **Para quién:** toda la empresa, sepa programar o no · **Tiempo de lectura:** ~6 min · **Nivel:** 🟢 básico

Pedimos algo a un asistente de IA, aparece una primera versión en pocos minutos y empezamos a corregirla sobre la marcha. La sensación es buenísima: cada instrucción produce un resultado visible.

El problema llega cuando aquello deja de ser una prueba y empieza a convertirse en software que tiene que durar.

## Qué es el *vibe coding*

Imagina que Luis escribe: «Hazme una aplicación para reservar las salas de reuniones». Poco después tiene un calendario, una lista de salas y un botón de «Reservar».

Después pide que se vea la planta, que avise si una sala está ocupada, que permita cancelar y que muestre las reservas propias. Cada cambio se decide en el momento y se añade al anterior.

Eso es *vibe coding*: construir a base de instrucciones sucesivas, mirando si el resultado parece correcto y corrigiendo sobre la marcha. Puede ser una forma estupenda de explorar una idea o montar un prototipo. El riesgo aparece cuando esas conversaciones son el único lugar donde quedan las decisiones.

> [!NOTE]
> Para una prueba de una tarde o algo que sabemos que vamos a tirar, no hay ningún problema en trabajar así. La dificultad empieza cuando el prototipo se queda.

## Por qué engancha

Porque funciona. Al menos al principio.

- **Es rápido:** enseñas algo en minutos.
- **Da sensación de progreso:** pides un cambio y lo ves casi al instante.
- **Reduce la barrera de entrada:** personas que no programan pueden participar mucho más directamente.

Todo eso es valioso. El problema no es usar un asistente de IA, sino que decisiones importantes acaben repartidas entre *prompts*, conversaciones y suposiciones que nadie ha dejado por escrito.

## Qué pasa después

Cuando el proyecto crece empiezan a aparecer preguntas que una demo no responde:

- ¿Pueden solaparse dos reservas?
- ¿Cuánto puede durar una reunión?
- ¿Quién puede cancelar una reserva ajena?
- ¿Qué horario tiene la oficina?
- ¿Qué datos necesitamos guardar realmente?

Si nadie decidió esas cosas de forma explícita, el sistema acaba teniendo respuestas de todos modos. A veces las puso el asistente, a veces aparecieron en una conversación y a veces son consecuencia accidental del código.

Ese es el problema de fondo: no que el asistente se equivoque, sino que ya no sabemos distinguir con facilidad entre **una decisión**, **una suposición** y **un bug**.

## ReservaSalas v0: la historia de Luis y Ana

Ana, responsable de Oficina, quiere sustituir la hoja de cálculo con la que se reservan doce salas. Se lo comenta a Luis y este prepara una primera versión con un asistente de IA.

El viernes la demo funciona muy bien.

El lunes, Marta reserva la sala Mediterráneo de 10:00 a 11:00 y Jorge la reserva de 10:30 a 11:30. Nadie había dicho qué debía ocurrir con un solapamiento, así que el sistema acepta las dos.

Luis pide que lo corrija. El problema desaparece, pero ahora las reservas solo admiten bloques de una hora. Más tarde Ana descubre que no se puede reservar antes de las 09:00, aunque la oficina abre a las 08:00. Tampoco recuerda nadie cuándo se decidió aquello.

Ninguno de esos problemas es especialmente difícil de programar. Lo difícil es saber **qué comportamiento era el correcto**.

Si antes de construir hubieran dejado escritas unas pocas reglas —horario de 08:00 a 20:00, máximo cuatro horas, sin solapamientos y con un responsable visible por reserva—, Luis tendría un sitio al que volver cada vez que apareciera una duda.

Eso es lo que aporta una especificación.

## La reforma sin plano

La analogía es bastante simple: reformar una cocina sin plano.

Puedes tener al mejor albañil del mundo y pedirle cambios sobre la marcha. Mueve la nevera, tira un tabique, desplaza una tubería. Cada petición puede estar perfectamente ejecutada y, aun así, el conjunto terminar mal porque nadie fijó antes qué debía respetarse.

Con el software pasa lo mismo. La velocidad del asistente no elimina la necesidad de decidir; solo hace que lleguemos antes a las consecuencias de no haber decidido.

La especificación hace de plano. El plan técnico viene después y decide cómo construirlo.

## Lo que le cuesta a la empresa

El coste no suele verse en la primera demo. Aparece con los cambios.

| Coste | En qué se nota |
|---|---|
| **Retrabajo** | Se corrige una cosa y hay que volver sobre otras que ya parecían terminadas |
| **Deuda técnica** | Los atajos se acumulan y cada cambio cuesta más que el anterior |
| **Dependencia de personas** | Solo quien estuvo en las conversaciones entiende por qué el sistema funciona así |
| **Riesgo con los datos** | Se guardan o muestran datos que nadie decidió realmente necesitar |

La velocidad inicial sigue siendo real. Lo que cambia es que parte del tiempo ahorrado puede reaparecer después en forma de revisión, correcciones y dudas.

> [!WARNING]
> Con datos personales el problema deja de ser solo de mantenimiento. Un asistente puede añadir campos, informes o comportamientos razonables que nadie pidió. Qué datos se usan y con qué límites debe ser una decisión explícita.

## Síntomas y causa raíz

Algunos síntomas se repiten mucho:

| Síntoma | Pregunta que falta |
|---|---|
| «Ayer funcionaba y hoy no» | ¿Qué comportamientos debían quedar protegidos por pruebas? |
| «¿Por qué solo deja reservar una hora?» | ¿Dónde se decidió ese límite? |
| «Solo Luis sabe tocarlo» | ¿Dónde están documentadas las decisiones funcionales? |
| «Cada cambio rompe algo distinto» | ¿Contra qué comportamiento esperado estamos comprobando el resultado? |

La causa no siempre será la falta de especificación, pero si nadie puede responder a esas preguntas sin abrir el código o buscar un chat antiguo, tenemos una señal bastante clara.

> [!TIP]
> Si el proyecto ya existe, no hace falta empezar de cero. Se puede reconstruir una especificación a partir del comportamiento actual, decidir qué debería cambiar y seguir desde ahí.

## Tres preguntas antes de aceptar una demo

No necesitas leer código. Pregunta:

1. **¿Dónde está escrito lo que tiene que hacer?**
2. **¿Qué pasa en los casos incómodos o excepcionales?**
3. **¿Cómo comprobaremos que el próximo cambio no rompe lo que ya funciona?**

Si las tres respuestas dependen de «lo hablamos con el asistente» o «está en el código», la demo puede ser buena, pero todavía falta convertirla en algo mantenible.

## El problema no es el asistente de IA

Un asistente puede escribir código extraordinariamente rápido y también puede ayudarnos a pensar mejor. Lo que no puede hacer por nosotros es decidir qué necesita realmente el negocio y asumir la responsabilidad de esa decisión.

SDD parte de ahí: antes de construir, dejamos por escrito qué queremos, por qué y qué condiciones debe cumplir. Después usamos el asistente para acelerar el resto.

No elimina errores ni convierte una mala idea en una buena. Lo que sí hace es reducir el número de decisiones que terminan escondidas en una conversación o en una línea de código.

Si prefieres verlo dibujado, el [diagrama 01](../diagramas/01-vibe-coding-vs-sdd.md) compara ambos caminos.

## En tres frases

1. El *vibe coding* es muy útil para explorar y prototipar; el problema aparece cuando las conversaciones se convierten en el único registro de las decisiones.
2. Cuando el software crece, necesitamos distinguir qué comportamiento fue decidido, cuál fue supuesto y cuál es simplemente un error.
3. SDD propone dejar esas decisiones en una especificación antes de construir.

## Siguiente paso

Continúa con [Qué es SDD](02-que-es-sdd.md).

---

🏠 [Índice de documentación](README.md) · ➡️ [Siguiente: Qué es SDD](02-que-es-sdd.md)
