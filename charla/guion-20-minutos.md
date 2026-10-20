# Guion de la charla de 20 minutos

> **Para quién:** quien presenta la charla (no hace falta programar) y, como público, toda la empresa · **Tiempo de lectura:** ~15 min (la charla dura 20) · **Nivel:** 🟢 básico

Este es el guion de la charla «Pizza Day»: veinte minutos para presentar a toda la empresa SDD (*Spec-Driven Development*, desarrollo guiado por especificaciones) y explicar qué problema resuelve frente al *vibe coding* (programar a golpe de instrucciones sueltas, improvisando con el asistente de IA). Cada bloque trae lo que dirías en voz alta, qué enseñar en pantalla y cómo pasar al siguiente; los textos son sugerencias, así que dilos con tus palabras.

**Qué vas a encontrar**

- [Objetivo, público y materiales](#objetivo-público-y-materiales)
- [Minutaje](#minutaje)
- [Minutos 0-2: el gancho](#minutos-0-2-el-gancho)
- [Minutos 2-5: el problema del *vibe coding*](#minutos-2-5-el-problema-del-vibe-coding)
- [Minutos 5-9: qué es SDD y los siete pasos](#minutos-5-9-qué-es-sdd-y-los-siete-pasos)
- [Minutos 9-12: los artefactos de ReservaSalas](#minutos-9-12-los-artefactos-de-reservasalas)
- [Minutos 12-16: mini-ejercicio con el público](#minutos-12-16-mini-ejercicio-con-el-público)
- [Minutos 16-18: qué cambia para cada rol](#minutos-16-18-qué-cambia-para-cada-rol)
- [Minutos 18-20: cierre y preguntas](#minutos-18-20-cierre-y-preguntas)
- [Preguntas probables del público](#preguntas-probables-del-público)
- [Consejos de ritmo](#consejos-de-ritmo)
- [Qué recortar si vas tarde](#qué-recortar-si-vas-tarde)

## Objetivo, público y materiales

**Objetivo.** Que al salir cualquier persona sepa explicar en una frase qué es SDD, por qué evita los problemas de pedirle código a un asistente de IA sin nada escrito, y qué puede hacer ella desde mañana según su rol. Nadie tiene que salir sabiendo usar una herramienta: eso es cosa de los talleres.

**Público.** Toda la empresa a la vez, en una sala o en línea: managers, RRHH, perfiles de negocio y quien programa. La charla está pensada para quien no ha escrito nunca una línea de código; quien programa encontrará los detalles en el repositorio.

**Quién presenta.** Una persona que haya leído [El problema del *vibe coding*](../docs/01-el-problema-del-vibe-coding.md), [Qué es SDD](../docs/02-que-es-sdd.md) y [Escribir requisitos claros (EARS)](../docs/05-escribir-requisitos-claros-ears.md), y que haya hecho al menos una vez la [dinámica de equipo de 20 minutos](../ejercicios/04-dinamica-de-equipo-20-minutos.md). No hace falta que programe. Si puedes, busca una segunda persona que lleve el tiempo y escriba en la pizarra durante el mini-ejercicio.

**Materiales.** No hace falta preparar una presentación: la charla se da desde el propio repositorio, abierto en el navegador. Solo necesitas:

- Un proyector o la pantalla compartida, con el navegador al 125-150 % de zoom para que se lea desde el fondo, y, como plan B por si falla la conexión, capturas de las pestañas de abajo.
- Una pizarra, un rotafolio o un documento en blanco proyectado, para escribir lo que dicte la sala, y un cronómetro que veas tú (el móvil vale).
- Dos diapositivas (o dos documentos proyectados): las frases vagas del mini-ejercicio y el cierre. Su texto está en los bloques correspondientes.

Abre estas pestañas, en este orden, antes de empezar:

| Pestaña | Qué es (ruta desde `charla/`) | Bloque |
|---|---|---|
| 1 | [`../diagramas/01-vibe-coding-vs-sdd.md`](../diagramas/01-vibe-coding-vs-sdd.md#los-dos-caminos-cara-a-cara) | Minutos 2-5 |
| 2 | [`../diagramas/02-flujo-completo-sdd.md`](../diagramas/02-flujo-completo-sdd.md#los-siete-pasos-y-sus-artefactos) | Minutos 5-9 |
| 3 | [`../ejercicios/soluciones/03-reserva-salas/spec.md`](../ejercicios/soluciones/03-reserva-salas/spec.md) | Minutos 9-12 |
| 4 | [`../ejercicios/soluciones/03-reserva-salas/tasks.md`](../ejercicios/soluciones/03-reserva-salas/tasks.md#fase-3-historia-de-usuario-1--reservar-una-sala-prioridad-p1--mvp) | Minutos 9-12 |
| 5 | Diapositiva con las tres frases vagas | Minutos 12-16 |
| 6 | [`../diagramas/04-roles-y-participacion.md`](../diagramas/04-roles-y-participacion.md#matriz-de-roles-y-pasos) | Minutos 16-18 |
| 7 | Diapositiva de cierre, con enlaces y fechas | Minutos 18-20 |

## Minutaje

| Minuto | Bloque | Idea que tiene que quedar | Qué muestras |
|---|---|---|---|
| 0-2 | El gancho | Sin plano, cada arreglo crea el problema siguiente. | Nada: mira a la sala |
| 2-5 | El problema del *vibe coding* | La demo de una tarde no aguanta al lunes siguiente. | Pestaña 1 |
| 5-9 | Qué es SDD y los siete pasos | Primero el qué y el porqué, por escrito; el código, lo último. | Pestaña 2 |
| 9-12 | Los artefactos de ReservaSalas | Son textos que cualquiera puede leer y corregir. | Pestañas 3 y 4 |
| 12-16 | Mini-ejercicio | Una frase vaga se convierte en un requisito comprobable. | Pestaña 5 y pizarra |
| 16-18 | Qué cambia para cada rol | Negocio entra desde el principio; el asistente no aprueba nada. | Pestaña 6 |
| 18-20 | Cierre y preguntas | Cada persona sabe por dónde empezar mañana. | Pestaña 7 |

## Minutos 0-2: el gancho

Elige una de las dos versiones. La reforma funciona mejor si la mayoría del público no es técnico; la demo que se rompe, si hay mucha gente que programa. Ninguna necesita pantalla.

**Qué dices (versión A, la reforma sin plano):**

> Levantad la mano quienes hayáis hecho alguna vez una reforma en casa. *[Pausa de tres segundos.]* Ahora imaginad que contratáis al albañil más rápido del mundo, voluntarioso como nadie, y le decís solo esto: «quiero la cocina más grande». Sin plano y sin presupuesto.
>
> El lunes ya ha tirado un tabique. El martes le decís que la nevera no cabe donde la ha puesto; la mueve, y para eso desvía una tubería. El jueves el baño se queda sin agua. Cada día arregla lo del anterior, y cada arreglo crea el problema del siguiente.
>
> ¿El albañil es malo? No: es rapidísimo y hace exactamente lo que le pedís. Lo que falta es el plano. Hoy, los asistentes de IA que escriben código son ese albañil. Y esta charla va del plano.

**Qué dices (versión B, la demo que se rompe):**

> Un viernes, Luis, programador junior, enseña una aplicación para reservar salas que ha hecho en una tarde con un asistente de IA. Ana, la responsable de Oficina, está encantada. El lunes, Marta reserva la sala Mediterráneo de 10:00 a 11:00, y Jorge, de RRHH, de 10:30 a 11:30. A las 10:30 hay dos equipos en la puerta.
>
> El asistente nunca supo que dos reservas de la misma sala no pueden cruzarse. No porque se equivocara, sino porque nadie se lo dijo. Esta charla va de cómo decírselo antes.

**Qué muestras:** nada; apaga la pantalla o deja solo el título. Las dos historias están en [`../docs/01-el-problema-del-vibe-coding.md`](../docs/01-el-problema-del-vibe-coding.md#la-reforma-sin-plano): la reforma, en «La reforma sin plano», y la demo, en [«ReservaSalas v0»](../docs/01-el-problema-del-vibe-coding.md#reservasalas-v0-la-historia-de-luis-y-ana).

**Transición:** «Eso que le pasó a la cocina tiene nombre cuando pasa con el software.» Con la versión B: «Y lo del lunes fue solo el principio.»

## Minutos 2-5: el problema del *vibe coding*

**Qué dices:**

> Se llama *vibe coding*: programar a golpe de instrucciones sueltas, improvisando con el asistente de IA. Le escribes «hazme una app de reservas de salas» y en una tarde tienes algo que funciona. Engancha, y es normal: es rapidísimo y la demo queda muy bien.
>
> El problema llega después. *[Si usaste la versión A, cuenta aquí lo del lunes: dos equipos en la puerta de la sala Mediterráneo.]* La segunda semana, Luis le pide al asistente que impida los choques. Lo hace, pero de paso fija las reservas a bloques de una hora exacta, porque Luis escribió «bloques de una hora» en una instrucción pensando en otra cosa. Las reuniones de hora y media ya no caben.
>
> La cuarta semana, Ana pregunta por qué no se puede reservar antes de las 09:00, si la oficina abre a las 08:00. Nadie lo decidió: el asistente supuso un horario «normal», y la conversación de aquella tarde ya no existe. Luis cambia de equipo, nadie se atreve a tocar la aplicación y Ana vuelve a la hoja de cálculo.
>
> Fijaos en que nada de esto es culpa de Luis ni del asistente. Faltaba un texto que dijera qué tenía que hacer la aplicación, y un sitio donde quedaran las decisiones. *[Señala la tabla.]* El primer día, el *vibe coding* gana: hay demo en una tarde. A los tres meses pierde, porque cada cambio obliga a releer código que nadie entiende. Para una prueba que se va a tirar no es malo; el problema es cuando esa prueba se convierte en la aplicación que usa todo el mundo.

**Qué muestras:** pestaña 1, [`../diagramas/01-vibe-coding-vs-sdd.md`](../diagramas/01-vibe-coding-vs-sdd.md#los-dos-caminos-cara-a-cara), tabla «Los dos caminos, cara a cara». Señala solo dos filas: «Velocidad el primer día» y «Velocidad a los 3 meses».

**Transición:** «Si el problema es que no hay plano, la solución parece obvia: escribir el plano primero. Eso es SDD.»

## Minutos 5-9: qué es SDD y los siete pasos

Aquí presentas el método y sus cuatro documentos principales: la constitución (`constitution.md`), la especificación (`spec.md`), el plan técnico (`plan.md`) y la lista de tareas (`tasks.md`). No hace falta que la sala retenga los nombres de los ficheros; sí, el orden.

**Qué dices:**

> SDD son las siglas de *Spec-Driven Development*, desarrollo guiado por especificaciones. En una frase: primero se escribe, en castellano corriente, qué queremos y por qué; y a partir de ese texto el asistente de IA genera el plan, las tareas y el código, con una persona revisando cada paso.
>
> Son siete pasos, del 0 al 6. *[Recorre el diagrama de arriba abajo.]* El 0 es la constitución: las reglas del juego del proyecto, como «guardamos solo los datos imprescindibles» o «nada está hecho sin una prueba». El 1 es especificar: qué tiene que hacer el sistema y por qué, sin hablar de tecnología. El 2 es aclarar: el asistente pregunta lo que no sabe, en vez de inventárselo, y negocio responde.
>
> Del 3 al 5 viene la parte técnica: planificar, que es decidir la tecnología y justificarla; trocear el plan en tareas pequeñas, y analizar, que es comprobar que todo cuadra con todo. El código solo aparece en el paso 6, implementar, y llega con cuatro documentos que explican qué debe hacer y por qué.
>
> Lo más importante son las flechas que vuelven hacia arriba. Si algo está mal, no se parchea el código: se corrige la especificación y se regenera lo afectado. Si mañana Ana decide que se puede reservar con 60 días de antelación en vez de 30, se cambia una frase del texto; nadie rebusca en el código. ¿Y es muy lento? Menos de lo que parece: en nuestra experiencia, una funcionalidad pequeña como esta recorre los siete pasos en uno o dos días.

**Qué muestras:** pestaña 2, [`../diagramas/02-flujo-completo-sdd.md`](../diagramas/02-flujo-completo-sdd.md#los-siete-pasos-y-sus-artefactos). Recorre los pasos (nodos azules) de arriba abajo, señala los ficheros (nodos amarillos) sin leerlos y termina en las flechas de vuelta. Los iconos dicen quién participa: 👤 negocio, 👩‍💻 quien programa, 🤖 el asistente de IA. Si alguien pregunta por las flechas, la tabla [«Los tres bucles de vuelta»](../diagramas/02-flujo-completo-sdd.md#los-tres-bucles-de-vuelta) las explica una a una.

**Transición:** «Hasta ahora os he hablado de ficheros. Vamos a abrir dos de verdad.»

## Minutos 9-12: los artefactos de ReservaSalas

Aquí enseñas dos ficheros reales del ejemplo resuelto: la especificación (`spec.md`) y la lista de tareas (`tasks.md`). No se trata de leerlos, sino de que la sala vea que son textos normales y que hay un hilo del choque del lunes a una prueba concreta.

**Qué dices:**

> Esta es la especificación real de ReservaSalas. Arriba está la petición de Ana, con sus palabras. Lo primero que os pido es que os fijéis en lo que no hay: ni una línea de código. Cualquiera de esta sala puede leerla y decir «esto está mal».
>
> Historia de usuario 1, reservar una sala, prioridad P1. Criterio 3: «Dado que Mediterráneo ya está reservada el jueves de 10:30 a 11:30, cuando Marta intenta reservarla de 10:00 a 11:00, entonces el sistema rechaza la reserva e indica que la sala está ocupada». ¿Os suena? Es el choque del lunes, escrito antes de que ocurra.
>
> Un poco más abajo está el mismo caso como requisito, el RF-005. Y los criterios de éxito, con cifras: reservar lleva menos de un minuto; cero reservas solapadas. Son de Ana, no del equipo técnico.
>
> Y esta es la lista de tareas, lo que sale del plan: tareas pequeñas, cada una con el fichero que toca y el requisito que cumple. Fijaos en el orden: primero se escriben las pruebas, que tienen que fallar, y después se programa. La T013 prueba justo el RF-005. Del choque del lunes a una prueba automática hay un hilo que cualquiera puede seguir.

**Qué muestras:**

1. Pestaña 3, [`../ejercicios/soluciones/03-reserva-salas/spec.md`](../ejercicios/soluciones/03-reserva-salas/spec.md): la «Petición original» de arriba; después la [historia de usuario 1](../ejercicios/soluciones/03-reserva-salas/spec.md#historia-de-usuario-1--reservar-una-sala-prioridad-p1), criterio 3; después los [requisitos funcionales](../ejercicios/soluciones/03-reserva-salas/spec.md#requisitos-funcionales-functional-requirements), RF-005, y los [resultados medibles](../ejercicios/soluciones/03-reserva-salas/spec.md#resultados-medibles-measurable-outcomes), CE-001 y CE-002.
2. Pestaña 4, [`../ejercicios/soluciones/03-reserva-salas/tasks.md`](../ejercicios/soluciones/03-reserva-salas/tasks.md#fase-3-historia-de-usuario-1--reservar-una-sala-prioridad-p1--mvp), fase 3: la tarea T013 (pruebas) y la T020 (implementación).

Estos son los fragmentos que tienes que señalar, copiados tal cual, para que los encuentres sin buscar. De `spec.md`:

```markdown
3. **Dado** que Mediterráneo ya está reservada el jueves de 10:30 a 11:30, **cuando** Marta intenta reservarla de 10:00 a 11:00, **entonces** el sistema rechaza la reserva e indica que la sala está ocupada de 10:30 a 11:30.

- **RF-005**: SI la franja solicitada se solapa con otra reserva de la misma sala, ENTONCES el sistema deberá rechazar la reserva e indicar qué franja está ocupada.

- **CE-001**: Reservar una sala, desde que se abre la aplicación hasta que aparece la confirmación, lleva menos de 1 minuto.
- **CE-002**: Cero reservas solapadas: en ningún momento existen dos reservas activas de la misma sala con franjas que se crucen.
```

De `tasks.md` (la T020 está recortada):

```markdown
- [ ] T013 [P] [HU1] Pruebas unitarias de solapamiento en `tests/unitarias/test_solapamiento.py`: solapamiento parcial, total, franjas consecutivas que no chocan y sala distinta que no choca (RF-005, CE-002)
- [ ] T020 [HU1] Implementar en `src/reservasalas/servicios/reservas.py` la creación de reserva: comprobación de solapamiento e inserción […] (RF-003, RF-005, RF-007, CE-002)
```

> [!TIP]
> No expliques las rutas de ficheros ni las etiquetas `[P]` y `[HU1]`. Basta con que la sala vea `RF-005` y `CE-002` al final de la línea: el requisito de Ana viaja hasta la prueba.

**Transición:** «Habéis visto requisitos bien escritos. Ahora os toca escribirlos a vosotros.»

## Minutos 12-16: mini-ejercicio con el público

La sala convierte tres frases vagas en requisitos EARS (*Easy Approach to Requirements Syntax*, una forma sencilla y estructurada de redactar requisitos). Es la versión de 4 minutos de la [dinámica de equipo](../ejercicios/04-dinamica-de-equipo-20-minutos.md#variantes): la tarjeta 1 (plazas de parking), un minuto por frase y un minuto de cierre. Sin hojas ni grupos: la sala dicta a mano alzada y tú escribes en la pizarra, tal cual, sin corregir.

Lo que proyectas en la pestaña 5 sale de la [tarjeta 1](../ejercicios/04-dinamica-de-equipo-20-minutos.md#tarjetas-de-peticiones-vagas) y de la [tabla de patrones EARS](../docs/05-escribir-requisitos-claros-ears.md#los-cinco-patrones-y-el-sexto):

```text
«Una app para que la gente reserve plazas de parking.»
Lo pide: Ana, responsable de Oficina. Hoy hay 30 plazas que se reparten
por correo cada lunes y siempre hay quejas.

Tres frases tal como llegaron por correo:
  1. «que se vea qué plazas hay»
  2. «que no se pueda coger una plaza ocupada»
  3. «que Oficina pueda bloquear plazas»

Plantillas EARS (el sujeto es siempre el sistema; el verbo, «deberá»):
  El sistema deberá…               MIENTRAS…, el sistema deberá…
  CUANDO…, el sistema deberá…      SI…, ENTONCES el sistema deberá…
  DONDE…, el sistema deberá…
```

**Qué dices (al empezar, en 20 segundos):**

> Esta es una petición como las que llegan de verdad: «una app para reservar plazas de parking». Debajo, tres frases tal como vinieron en un correo. Vamos a convertirlas en requisitos con EARS, una forma sencilla y estructurada de redactar requisitos: cinco plantillas de frase.
>
> Para cada frase, que alguien me dicte un requisito con una de las plantillas; lo escribo tal cual. El resto tiene veinte segundos para cazarle una vaguedad: un adjetivo sin cifra, dos cosas en una frase, una tecnología colada o un sujeto que es la persona y no el sistema.

Para cada frase tienes la respuesta típica de la sala (que también es tu plan B: si en cinco segundos nadie se anima, díctala tú y pide que la cacen), las vaguedades que deberían salir y la versión de referencia, con el patrón de la tabla de [Escribir requisitos claros](../docs/05-escribir-requisitos-claros-ears.md#los-cinco-patrones-y-el-sexto).

**Minuto 12-13. Frase 1: «que se vea qué plazas hay».**
- Respuesta típica: «El usuario deberá poder ver las plazas de forma rápida».
- Vaguedades: el sujeto es la persona, no el sistema; «de forma rápida» es un adjetivo sin cifra; no dice qué plazas (¿las libres?, ¿de qué día?).
- Referencia (ubicuo): «El sistema deberá mostrar las plazas libres de cada día con su número y su planta».

**Minuto 13-14. Frase 2: «que no se pueda coger una plaza ocupada».**
- Respuesta típica: «SI la plaza está ocupada, ENTONCES el usuario no podrá cogerla».
- Vaguedades: otra vez el sujeto es la persona; no dice qué hace el sistema (¿rechaza?, ¿avisa?, ¿de quién es la plaza?), ni ocupada cuándo.
- Referencia (comportamiento no deseado): «SI la plaza elegida ya está reservada ese día, ENTONCES el sistema deberá rechazar la reserva e indicar quién la tiene». Si la respuesta del sistema es rechazar, casi siempre es un SI.

**Minuto 14-15. Frase 3: «que Oficina pueda bloquear plazas».**
- Respuesta típica: «DONDE la persona sea de Oficina, el sistema deberá permitir bloquear plazas para que nadie pueda reservarlas».
- Vaguedades: dos cosas en una frase (quién puede bloquear y qué le pasa a una plaza bloqueada); «bloquear», ¿para siempre o un tiempo?
- Referencia: dos requisitos. Opcional: «DONDE la persona tenga permisos de Oficina, el sistema deberá permitir marcar una plaza como no disponible». Por estado: «MIENTRAS una plaza esté marcada como no disponible, el sistema deberá impedir reservarla».

**Minuto 15-16. Cierre del ejercicio.** Proyecta las versiones de referencia (o escríbelas debajo de las de la sala) y cierra con la idea de la dinámica:

```text
1   El sistema deberá mostrar las plazas libres de cada día con su número
    y su planta.                                          → ubicuo
2   SI la plaza elegida ya está reservada ese día, ENTONCES el sistema
    deberá rechazar la reserva e indicar quién la tiene.  → comportamiento no deseado
3a  DONDE la persona tenga permisos de Oficina, el sistema deberá
    permitir marcar una plaza como no disponible.         → opcional
3b  MIENTRAS una plaza esté marcada como no disponible, el sistema
    deberá impedir reservarla.                            → por estado
```

> Fijaos en la tercera: una frase vaga eran dos requisitos. Y las vaguedades que habéis cazado en veinte segundos son las que un asistente de IA suele resolver inventando. Cada una es un error que se evita antes de que exista, y lo habéis hecho sin tocar un ordenador.

**Transición:** «Esto que acabáis de hacer no es cosa de programadores. Veamos quién hace qué.»

## Minutos 16-18: qué cambia para cada rol

**Qué dices:**

> Lo que más cambia con SDD es cuándo entra cada persona. Negocio ya no aparece al final para decir «esto no es lo que pedí»: entra desde el primer paso. En esta tabla, cada fila es un rol y cada columna, un paso.
>
> Si encargas algo, como Ana, lideras los tres primeros pasos: dictas los principios, describes qué quieres y por qué, y respondes a las aclaraciones; en ReservaSalas fue una reunión de quince minutos. Al final pruebas la aplicación con la especificación en la mano. Sin leer código ni instalar nada.
>
> Si diriges un equipo que la va a usar, como Marta, aportas el uso real: qué es «rápido» para ti y qué te molesta hoy. Si eres de RRHH o de negocio, como Jorge, sabes qué datos de las personas se pueden guardar y cuáles no, y puedes escribir tú la especificación de un proceso de tu área, como una solicitud de vacaciones.
>
> Si programas, como Luis, vas a teclear menos y a decidir y revisar más: eliges la tecnología y la justificas, compruebas que cada requisito tiene su tarea y, cuando algo falla, corriges la especificación, no el código. Y el asistente de IA redacta, pregunta y ejecuta, pero no lidera ningún paso ni aprueba nada.

**Qué muestras:** pestaña 6, [`../diagramas/04-roles-y-participacion.md`](../diagramas/04-roles-y-participacion.md#matriz-de-roles-y-pasos), «Matriz de roles y pasos». Señala tres cosas: las L (lidera) de Ana en los pasos 0 a 2, las L de Luis en los pasos 3 a 6 y la fila del asistente, que no tiene ninguna.

**Transición:** «Y ahora, lo práctico: qué podéis hacer mañana.»

## Minutos 18-20: cierre y preguntas

**Qué dices:**

> Si os quedáis con una sola frase, que sea esta: primero el qué y el porqué, por escrito; el código, lo último. *[Con la versión A del gancho: «El asistente de IA es el albañil más rápido del mundo; el plano lo ponemos nosotros».]*
>
> Mañana, una cosa cada uno. Si no programas, haz el ejercicio de la solicitud de vacaciones: media hora y sin instalar nada. Si diriges un equipo, lleva la dinámica de veinte minutos a tu próxima reunión. Si programas, prepara el entorno y recorre ReservaSalas de principio a fin.
>
> Todo está en el repositorio, con una ruta de lectura para cada perfil. Y hay talleres: *[fecha y lugar del próximo taller de dos horas]* y *[fecha de la sesión práctica para quien programa]*. El enlace está en pantalla. ¿Preguntas?

**Qué muestras:** pestaña 7, la diapositiva de cierre. Su texto, con el primer paso y la ruta de lectura de cada perfil:

```text
SDD: primero el qué y el porqué, por escrito. El código, lo último.

Empieza mañana:
  Si no programas       → ejercicio 01: Solicitud de vacaciones (30 min)
  Si diriges un equipo  → ejercicio 04: la dinámica de 20 minutos
  Si programas          → ejercicios 00 (entorno) y 03 (ReservaSalas)

Rutas de lectura (con sus ejercicios):
  Manager o responsable de equipo   docs 01, 02, 06, 08 y 09     unas 2 h
  RRHH y perfiles de negocio        docs 01, 02, 05, 06 y 10     unas 2 h
  Programador junior                todos los docs y diagramas   9-12 h, en varios días
  Programador con experiencia       docs 02, 03, 04, 07 y 08     5-8 h

Repositorio:        [enlace al repositorio]
Próximos talleres:  [fecha, lugar o enlace de inscripción]
```

Los itinerarios completos, dibujados, están en [`../diagramas/06-mapa-del-repositorio.md`](../diagramas/06-mapa-del-repositorio.md#itinerarios-por-perfil), y el índice general, en [`../README.md`](../README.md).

**Para las preguntas:** deja al menos un minuto. Si nadie pregunta, lanza tú la primera de la lista de abajo: «Una que me hacen siempre: ¿esto no es más lento?». Al terminar, deja el enlace en pantalla y quédate un rato: muchas preguntas llegan cuando se apaga el micrófono.

## Preguntas probables del público

Respuestas de treinta segundos como máximo. Si la pregunta merece más, di dónde está la respuesta larga y sigue.

1. **¿Esto no es más lento que pedirle el código directamente al asistente?** El primer día, sí. La diferencia llega con los cambios: se edita un texto y hay una referencia escrita contra la que comprobar. En nuestra experiencia, una funcionalidad pequeña como ReservaSalas recorre los siete pasos en uno o dos días. [Respuesta larga](../docs/09-preguntas-frecuentes.md#esto-es-más-lento-que-pedirle-directamente-al-asistente).
2. **¿No es volver a escribir documentos que nadie lee?** No, porque este documento lo lee el asistente en cada paso, y de él salen el plan y las tareas. Describe una funcionalidad, no un sistema entero: la especificación de ReservaSalas se lee en unos diez minutos. [Respuesta larga](../docs/09-preguntas-frecuentes.md#no-es-volver-a-escribir-documentos-que-nadie-lee).
3. **¿Tengo que saber programar para escribir una especificación?** No. Se escribe en castellano corriente y sin tecnología, y quien mejor escribe un requisito es quien conoce el problema. Las plantillas EARS ayudan a que cada frase tenga una sola lectura. [Respuesta larga](../docs/09-preguntas-frecuentes.md#tengo-que-saber-programar-para-escribir-una-especificación).
4. **Entonces, ¿quien programa ya no escribe código?** Teclea menos y decide y revisa más: elige la tecnología, comprueba que cada requisito tiene su tarea, lee lo que genera el asistente y ejecuta las pruebas. La edición a mano queda para detalles. [Respuesta larga](../docs/09-preguntas-frecuentes.md#entonces-ya-no-voy-a-escribir-código).
5. **¿Hay que recorrer los siete pasos hasta para un cambio pequeño?** No. Se cambia la especificación y se regenera solo lo afectado, como en el ejemplo de la antelación que pasa de 30 a 60 días. [Respuesta larga](../docs/09-preguntas-frecuentes.md#hay-que-recorrer-todo-el-flujo-hasta-para-un-cambio-pequeño).
6. **¿Y con las aplicaciones que ya tenemos?** No hace falta documentarlas enteras. Se empieza por el próximo cambio: se escribe su especificación a partir de lo que la aplicación hace hoy y de lo que debería hacer. [Respuesta larga](../docs/09-preguntas-frecuentes.md#qué-pasa-con-proyectos-que-ya-existen).
7. **¿Qué herramienta hay que usar?** SDD es un método, no un programa. Se puede seguir con GitHub Spec Kit (una herramienta gratuita que añade los pasos del método al asistente de IA), con Kiro, de AWS, o sin herramientas, con las plantillas y un chat de IA autorizado. Qué asistente se usa lo decide la empresa. [Respuesta larga](../docs/09-preguntas-frecuentes.md#es-obligatorio-usar-spec-kit).
8. **¿Puedo meter datos de clientes en el asistente?** No, salvo en un asistente que la empresa haya autorizado expresamente, y lo mismo con cualquier dato real de personas. Para probar, inventa los datos, como hace todo el material. [Respuesta larga](../docs/09-preguntas-frecuentes.md#puedo-meter-datos-de-clientes-en-el-asistente).
9. **Si el código falla, ¿de quién es la responsabilidad?** De las personas, no del asistente: cada paso tiene alguien que lo lidera y alguien distinto que lo revisa. SDD no evita todos los fallos, pero deja rastro de dónde nació cada uno. [Respuesta larga](../docs/09-preguntas-frecuentes.md#quién-es-responsable-si-el-código-falla).
10. **¿Sirve para cosas que no son software?** Sí, sobre todo la parte de pensar: escribir qué quieres, por qué y cómo sabrás que está bien sirve aunque al final sea un formulario o un procedimiento. La solicitud de vacaciones del ejercicio 01 no tiene ni una palabra de tecnología. [Respuesta larga](../docs/09-preguntas-frecuentes.md#sirve-para-cosas-que-no-son-software).

Si te preguntan algo que no está aquí ni en las [preguntas frecuentes](../docs/09-preguntas-frecuentes.md), di «no lo sé; lo consulto y os respondo por escrito», apúntalo y propón añadirlo al material, como explica la [guía del facilitador](guia-del-facilitador.md#recoger-mejoras-al-material).

## Consejos de ritmo

- **Ensaya una vez en voz alta, con cronómetro y con las pestañas abiertas.** Leer el guion en silencio engaña: el tiempo se va en cambiar de pestaña y en esperar a la sala.
- **Vigila los hitos, no cada minuto.** En el minuto 5 tienes que estar abriendo el diagrama de los siete pasos; en el 9, la especificación; en el 12, las frases vagas, y en el 16, la matriz de roles. Si llegas tarde a un hito, recorta el bloque siguiente con la tabla de abajo.
- **Protege el mini-ejercicio.** Es lo único en lo que participa la sala y lo que más se recuerda. Si tienes que recortar, recorta antes.
- **No leas el texto sugerido.** Quédate con la idea de cada bloque (la columna «Idea que tiene que quedar» del minutaje) y cuéntala a tu manera.
- **Las pausas cuentan.** Después de la pregunta del gancho, espera de verdad tres segundos; después de cada frase vaga, cinco, antes de recurrir a tu plan B.
- **Preguntas a mitad de charla:** «Me la apunto para el final». Y apúntala de verdad, a la vista de quien pregunta.
- **En línea,** pide a la segunda persona que lea el chat en voz alta durante el mini-ejercicio: allí, levantar la mano es escribir el requisito en el chat.

## Qué recortar si vas tarde

| Bloque | Qué recortas | Qué ganas (aprox.) |
|---|---|---|
| Minutos 0-2 | Te quedas con la primera y la última frase del gancho. | 1 min |
| Minutos 2-5 | Cuentas solo el lunes y la cuarta semana, y no enseñas la tabla. | 1 min |
| Minutos 5-9 | Los pasos 3 a 5 caben en una frase: «la parte técnica, que lidera quien programa». | 1 min |
| Minutos 9-12 | Solo la especificación (criterio 3 y RF-005); la lista de tareas se nombra, pero no se abre. | 1 min |
| Minutos 12-16 | Dos frases vagas en vez de tres: te saltas la tercera. | 1 min |
| Minutos 16-18 | Una frase por rol y sin la matriz en pantalla. | 1 min |
| Minutos 18-20 | Las preguntas pasan a un canal escrito; la llamada a la acción se queda entera. | 1 min |

> [!IMPORTANT]
> Lo que nunca se recorta: la frase de SDD (primero el qué y el porqué, por escrito; el código, lo último), el mini-ejercicio con al menos dos frases y la llamada a la acción con su enlace.

Si te sobra tiempo, haz la frase 3 con calma, separando sus dos requisitos en la pizarra, o cuenta el bucle de la antelación con la tabla [«Los tres bucles de vuelta»](../diagramas/02-flujo-completo-sdd.md#los-tres-bucles-de-vuelta).

## En tres frases

1. La charla «Pizza Day» presenta SDD a toda la empresa en veinte minutos y siete bloques: gancho, problema, método, artefactos reales, mini-ejercicio, roles y cierre.
2. Su centro es el mini-ejercicio: la sala convierte tres frases vagas en requisitos EARS y caza vaguedades, y así entiende sin ver código por qué la especificación va primero.
3. Cada bloque trae qué decir, qué enseñar y cómo pasar al siguiente; si vas tarde, recorta explicaciones, nunca el ejercicio ni la llamada a la acción.

## Siguiente paso

Continúa con la [Guía del facilitador](guia-del-facilitador.md), que explica cómo convertir esta charla en un taller de dos horas o en un itinerario de dos semanas, cómo adaptarla a cada público y cómo medir si ha funcionado.

---

🏠 [Índice de la charla](README.md) · ➡️ [Siguiente: Guía del facilitador](guia-del-facilitador.md)
