# Ejercicio 02 resuelto: requisitos EARS

> **Para quién:** RRHH, perfiles de negocio, managers y programadores junior · **Tiempo de lectura:** ~10 min · **Nivel:** 🟢 básico

Esta es la solución comentada del [ejercicio 02: practicar requisitos EARS](../02-practicar-requisitos-ears.md), con su misma numeración y agrupación: las doce reescrituras (F01 a F12, en los bloques A, B y C), la clasificación «al revés» (R1 a R4) y el «caza el error» (E1 a E4). Todos los requisitos están escritos con EARS (*Easy Approach to Requirements Syntax*): una forma sencilla y estructurada de redactar requisitos.

> [!NOTE]
> Es un ejemplo, no la única respuesta correcta. Si tu requisito tiene el mismo patrón, el mismo disparador o condición y una respuesta que se comprueba con un sí o un no, es igual de bueno aunque no coincida palabra por palabra. Tres decisiones nuestras son discutibles: el patrón de F03 (también vale MIENTRAS), las cifras supuestas del torno (F04 y F11) y el aviso de «falta agua» que hemos añadido en F03.

**Qué vas a encontrar**

- [Cómo leer esta solución](#cómo-leer-esta-solución)
- [Las doce frases de un vistazo](#las-doce-frases-de-un-vistazo)
- [Bloque A: una frase vaga, un patrón claro](#bloque-a-una-frase-vaga-un-patrón-claro)
- [Bloque B: elegir bien entre patrones parecidos](#bloque-b-elegir-bien-entre-patrones-parecidos)
- [Bloque C: frases que esconden más de un requisito](#bloque-c-frases-que-esconden-más-de-un-requisito)
- [Al revés: clasifica cuatro requisitos](#al-revés-clasifica-cuatro-requisitos)
- [Caza el error](#caza-el-error)
- [Supuestos y aclaraciones pendientes](#supuestos-y-aclaraciones-pendientes)
- [En tres frases](#en-tres-frases)
- [Siguiente paso](#siguiente-paso)

## Cómo leer esta solución

Cada frase sigue el mismo orden: la frase original, el requisito EARS, el patrón, por qué ese patrón y, si hay otra respuesta válida, la alternativa. Cuatro convenciones:

- Las plantillas son las de la [tabla de patrones del documento de EARS](../../docs/05-escribir-requisitos-claros-ears.md#los-cinco-patrones-y-el-sexto), y el patrón se elige con su [orden de decisión](../../docs/05-escribir-requisitos-claros-ears.md#qué-patrón-elijo): SI…, ENTONCES → CUANDO → MIENTRAS → DONDE → ubicuo. La primera pregunta que respondes con un «sí» da el patrón.
- Si la frase es de ReservaSalas o de vacaciones y su requisito ya existe en la [especificación canónica de ReservaSalas](03-reserva-salas/spec.md) (`spec.md`) o en la [especificación de vacaciones](01-solicitud-de-vacaciones/especificacion.md), lo citamos palabra por palabra, con su número (RF quiere decir requisito funcional).
- En las frases de la cafetera y del torno, el sistema se llama «la cafetera» o «el torno», como permite el ejercicio.
- Los datos que la frase no da se resuelven con un supuesto anotado o con el marcador `[NECESITA ACLARACIÓN: …]`. Están todos juntos en [Supuestos y aclaraciones pendientes](#supuestos-y-aclaraciones-pendientes).

## Las doce frases de un vistazo

Si solo quieres comprobar el patrón, te basta esta tabla. Donde te hayas desviado, baja a la frase para ver por qué.

| Frase | Patrón | Requisito |
|---|---|---|
| F01 · ReservaSalas | Ubicuo | RF-001 de ReservaSalas (literal) |
| F02 · Vacaciones | Por evento (CUANDO) | RF-003 de vacaciones (literal) |
| F03 · Cafetera | Comportamiento no deseado (SI…, ENTONCES) | Nuevo |
| F04 · Torno | Por evento (CUANDO) | Nuevo, con dos supuestos |
| F05 · ReservaSalas | Por estado (MIENTRAS) | RF-007 de ReservaSalas (literal) |
| F06 · Vacaciones | Opcional (DONDE) | RF-013 de vacaciones (literal) |
| F07 · Cafetera | Por estado (MIENTRAS) | Nuevo |
| F08 · ReservaSalas | Comportamiento no deseado (SI…, ENTONCES) | RF-005 de ReservaSalas (literal) |
| F09 · ReservaSalas | Comportamiento no deseado (SI…, ENTONCES), dos veces | Dos nuevos (a y b), o RF-006 de ReservaSalas |
| F10 · Vacaciones | Comportamiento no deseado (SI…, ENTONCES) | RF-004 de vacaciones (literal) |
| F11 · Torno | Complejo (MIENTRAS…, CUANDO…) | Nuevo, con un supuesto |
| F12 · Cafetera | Por evento (CUANDO), más un criterio de éxito | Nuevo, con marcadores de aclaración |

## Bloque A: una frase vaga, un patrón claro

Resultado esperado: un requisito por frase, que empieza por «El sistema deberá», «CUANDO» o «SI».

### F01 · ReservaSalas

- **Frase original:** «La app tiene que enseñar las salas.»
- **Requisito (RF-001 de ReservaSalas, literal):** El sistema deberá mostrar la lista de salas con su planta y aforo.
- **Patrón:** ubicuo (sin palabra clave).
- **Por qué:** no es un error que evitar, no ocurre en un momento concreto y no depende de un estado ni de un perfil. Las cuatro primeras preguntas del orden de decisión dicen «no», así que es ubicuo. «Enseñar las salas» se concreta en los dos datos que hacen falta para elegir una: dónde está (planta) y cuánta gente cabe (aforo).
- **Alternativa:** «CUANDO una persona abre la aplicación, el sistema deberá mostrar la lista de salas…» también se comprueba, pero añade un disparador que la frase no pide y decide algo de diseño (qué se ve al entrar). Si no hace falta, mejor ubicuo.

### F02 · Vacaciones

- **Frase original:** «Cuando alguien pida vacaciones, que se entere su jefe.»
- **Requisito (RF-003 de vacaciones, literal):** CUANDO una persona envía una solicitud, el sistema deberá registrarla en estado «pendiente» y avisar a su manager con las fechas y los días laborables que consume.
- **Patrón:** por evento (CUANDO).
- **Por qué:** es el camino normal, no algo que queramos cortar, y ocurre en un instante: al enviar la solicitud. «Que se entere» no se puede comprobar; «avisar a su manager con las fechas y los días laborables» sí: miras el aviso y ves si trae esos dos datos.
- **Alternativa:** RF-003 además deja la solicitud «pendiente», porque ocurre en el mismo instante que el aviso. Si solo reescribes lo que pide la frase, «CUANDO una persona envía una solicitud, el sistema deberá avisar a su manager con las fechas y los días laborables que consume» es igual de bueno.

### F03 · Cafetera

- **Frase original:** «La cafetera no debería dejar que se haga café si no hay agua.»
- **Requisito:** SI se pide un café con el depósito de agua vacío, ENTONCES la cafetera deberá impedir la preparación e indicar que falta agua.
- **Patrón:** comportamiento no deseado (SI…, ENTONCES).
- **Por qué:** hacer café sin agua es justo lo que queremos evitar, y la primera pregunta del orden de decisión ya da el patrón. «No debería» pasa a «deberá». Hemos añadido «indicar que falta agua» porque un rechazo sin explicación deja a la persona pulsando el botón; si quien encarga la cafetera no lo quiere, se quita.
- **Alternativa:** «MIENTRAS el depósito de agua esté vacío, la cafetera deberá impedir la preparación de café» también vale, porque el depósito vacío es un estado que dura hasta que alguien lo llena. Es la misma duda que separa RF-005 (un intento que se rechaza) de RF-007 (un estado que dura) en ReservaSalas.

### F04 · Torno

- **Frase original:** «El torno tiene que abrirse con la tarjeta.»
- **Requisito:** CUANDO una persona acerca al lector una tarjeta de acceso válida, el torno deberá desbloquearse durante 5 segundos.
- **Patrón:** por evento (CUANDO).
- **Por qué:** pasar la tarjeta ocurre en un instante y es el funcionamiento normal, no un error. La frase no dice con qué tarjeta ni durante cuánto tiempo. Sin esos datos, lo primero es preguntar (la alternativa de abajo); aquí hemos seguido con dos supuestos escritos a la vista: «válida» quiere decir dada de alta y no bloqueada, y «se asume 5 segundos; confirmar con Seguridad». Son provisionales: el requisito no se da por cerrado hasta que Seguridad los confirme.
- **Alternativa:** sin suponer nada, «…el torno deberá desbloquearse durante `[NECESITA ACLARACIÓN: ¿cuántos segundos permanece desbloqueado el torno?]`», y se pregunta a Seguridad. Y si quieres cubrir la tarjeta que no vale, es otro requisito con otro patrón: «SI una persona acerca una tarjeta que no es válida, ENTONCES el torno deberá permanecer bloqueado».

## Bloque B: elegir bien entre patrones parecidos

Resultado esperado: dos requisitos con MIENTRAS (F05 y F07), uno con DONDE (F06) y uno con SI…, ENTONCES (F08).

### F05 · ReservaSalas

- **Frase original:** «Si una sala está en obras, que no se pueda reservar.»
- **Requisito (RF-007 de ReservaSalas, literal):** MIENTRAS una sala esté marcada en mantenimiento, el sistema deberá impedir nuevas reservas en ella.
- **Patrón:** por estado (MIENTRAS).
- **Por qué:** el «si» de la frase despista. Unas obras duran días, y el documento de EARS lo resuelve así: si lo que impide la acción es un estado que dura, es MIENTRAS aunque la respuesta sea impedir; SI se reserva para un intento concreto que se rechaza en el momento. «En obras» pasa a «marcada en mantenimiento», el nombre del estado en ReservaSalas, que activa administración (RF-009).
- **Alternativa:** con SI («SI una persona intenta reservar una sala marcada en mantenimiento, ENTONCES el sistema deberá rechazar la reserva e indicar que la sala está en mantenimiento») también se comprueba, pero describe el intento y no el estado. El ejemplo canónico usa MIENTRAS.

### F06 · Vacaciones

- **Frase original:** «Los de RRHH pueden ver las vacaciones de todo el mundo.»
- **Requisito (RF-013 de vacaciones, literal):** DONDE la persona tenga rol de RRHH, el sistema deberá permitir ver las solicitudes aprobadas de toda la empresa y el saldo de cada persona.
- **Patrón:** opcional (DONDE).
- **Por qué:** es un permiso que solo tiene un perfil. El sujeto deja de ser «los de RRHH» y pasa a ser el sistema, que «deberá permitir»; y «las vacaciones de todo el mundo» se concreta en las solicitudes aprobadas de toda la empresa.
- **Alternativa:** RF-013 añade el saldo de cada persona, que la frase no pide; sin esa parte es la versión de la tabla del documento de EARS, e igual de buena. Lo que no conviene es el ubicuo «El sistema deberá permitir a RRHH ver…»: se entiende, pero esconde el perfil en mitad de la frase.

### F07 · Cafetera

- **Frase original:** «Mientras se calienta, que se vea.»
- **Requisito:** MIENTRAS la cafetera esté calentando el agua, la cafetera deberá mantener encendido el indicador de «calentando».
- **Patrón:** por estado (MIENTRAS).
- **Por qué:** calentar no es un instante: dura un rato, y el indicador tiene que estar encendido todo ese rato. «Que se vea» no dice qué se ve; «mantener encendido el indicador» sí, y se comprueba mirando la cafetera mientras calienta.
- **Alternativa:** un mensaje «Calentando…» en la pantalla en lugar del indicador también vale: cambia la respuesta, no el patrón. En cambio, con CUANDO («CUANDO empiece a calentar, la cafetera deberá encender el indicador») solo dirías cuándo se enciende, no que siga encendido mientras calienta.

### F08 · ReservaSalas

- **Frase original:** «Que avise si la reserva choca con otra.»
- **Requisito (RF-005 de ReservaSalas, literal):** SI la franja solicitada se solapa con otra reserva de la misma sala, ENTONCES el sistema deberá rechazar la reserva e indicar qué franja está ocupada.
- **Patrón:** comportamiento no deseado (SI…, ENTONCES).
- **Por qué:** un choque es lo que queremos impedir; aquí el «si» de la frase sí acierta. «Avisar» se queda corto: si el sistema avisa pero deja reservar, los choques siguen ahí, y CE-002 pide cero reservas solapadas (es un criterio de éxito: un resultado medible que dice, con cifras, si el sistema ha funcionado). Por eso rechaza e indica qué franja está ocupada, que es lo que la persona necesita para elegir otra.
- **Alternativa:** si quien encarga el sistema prefiriera avisar sin bloquear, seguiría siendo un SI…, ENTONCES con otra respuesta, como RF-007 de vacaciones con las fechas que coinciden. El patrón no cambia; la decisión de negocio, sí.

## Bloque C: frases que esconden más de un requisito

Resultado esperado: cinco requisitos para cuatro frases (cuatro si juntas los dos límites de F09), un criterio de éxito, un supuesto anotado y dos marcadores de aclaración.

### F09 · ReservaSalas

- **Frase original:** «Las reservas deben ser razonables: ni muy largas ni a deshoras.»
- **Requisito a:** SI la franja solicitada dura más de 4 horas, ENTONCES el sistema deberá rechazar la reserva e indicar que el máximo son 4 horas.
- **Requisito b:** SI la franja solicitada queda fuera del horario de oficina (08:00-20:00), ENTONCES el sistema deberá rechazar la reserva e indicar que solo se puede reservar de 08:00 a 20:00.
- **Patrón:** comportamiento no deseado (SI…, ENTONCES), dos veces.
- **Por qué:** «razonable» no se puede comprobar; «más de 4 horas» y «fuera de 08:00-20:00» sí, y son las cifras de ReservaSalas, no inventadas. Los dos son límites que queremos impedir, así que SI; y como cada uno se puede incumplir sin el otro, salen dos requisitos.
- **Alternativa:** un solo SI con los dos límites, porque la respuesta es la misma. Es lo que hace el ejemplo canónico en RF-006, que además añade dos límites que no salen de esta frase: «SI la franja solicitada queda fuera del horario de oficina (08:00-20:00), dura más de 4 horas, termina en el pasado o empieza más de 30 días después de hoy, ENTONCES el sistema deberá rechazar la reserva e indicar qué límite se incumple.»

### F10 · Vacaciones

- **Frase original:** «Que no se puedan pedir más días de los que te quedan y, si se intenta, que lo diga claramente.»
- **Requisito (RF-004 de vacaciones, literal):** SI una persona pide más días de los que tiene disponibles, ENTONCES el sistema deberá rechazar la solicitud e indicar cuántos días le quedan.
- **Patrón:** comportamiento no deseado (SI…, ENTONCES).
- **Por qué:** parecen dos cosas, pero «que no se pueda» y «que lo diga» son una sola respuesta (rechazar e indicar) a una sola condición, en el mismo momento. «Claramente» no tiene medida; lo sustituye el dato que hace clara la respuesta: cuántos días quedan. Y «te quedan» pasa a «tiene disponibles», que tiene una sola lectura porque es uno de los cuatro datos del saldo (RF-001 de vacaciones).
- **Alternativa:** partirla en dos (impedir por un lado, el mensaje por otro) no es un error grave, pero no aporta nada: las dos mitades tienen la misma condición y se comprueban en la misma prueba.

### F11 · Torno

- **Frase original:** «Fuera de horario, solo entra la gente de seguridad.»
- **Requisito:** MIENTRAS el edificio esté fuera del horario de apertura (de 20:00 a 08:00), CUANDO una persona acerca su tarjeta al lector, el torno deberá desbloquearse solo si la tarjeta es del personal de seguridad.
- **Patrón:** complejo (MIENTRAS…, CUANDO…).
- **Por qué:** hay un estado que dura horas (fuera de horario) y un evento de un instante (alguien pasa la tarjeta): dos condiciones a la vez, con el estado delante. «Solo si» es lo que hace comprobable el «solo entra»: a las 22:00, una tarjeta de seguridad abre y cualquier otra no. El horario es un supuesto: de 20:00 a 08:00, todos los días (lo contrario del horario de oficina de ReservaSalas), y hay que confirmarlo con Seguridad.
- **Alternativa:** si no quieres suponer, deja `[NECESITA ACLARACIÓN: ¿qué horario es «fuera de horario», también en fines de semana y festivos?]`. Y si prefieres una comprobación por requisito, pártelo en dos: uno para el personal de seguridad (se desbloquea) y otro para el resto (sigue bloqueado).
- **Ojo con F04:** F04 dice que cualquier tarjeta válida desbloquea el torno. Si los dos acaban en la misma especificación, acota F04 al horario de apertura («MIENTRAS el edificio esté dentro del horario de apertura, CUANDO…») para que no se contradigan a las 22:00.

### F12 · Cafetera

- **Frase original:** «Que sea fácil de limpiar y avise cuando toque.»
- **«Fácil de limpiar»:** no es un requisito funcional, porque nadie puede comprobarlo con un sí o un no. Se pide una cifra y se pasa a los criterios de éxito, por ejemplo: «La limpieza completa de la cafetera lleva menos de `[NECESITA ACLARACIÓN: ¿cuántos minutos?]`».
- **Requisito («avise cuando toque»):** CUANDO la cafetera lleve `[NECESITA ACLARACIÓN: ¿cuántos cafés o cuántos días?]` sin limpiarse, la cafetera deberá encender el aviso de limpieza.
- **Patrón:** por evento (CUANDO).
- **Por qué:** «cuando toque» es un momento concreto, pero la frase no dice cuál, y solo lo sabe quien conoce la cafetera. Inventarlo a escondidas sería peor que dejar la pregunta a la vista; para eso está el marcador, el mismo que usa el asistente de IA cuando le falta un dato.
- **Alternativa:** con un supuesto anotado, «CUANDO la cafetera lleve 100 cafés sin limpiarse, la cafetera deberá encender el aviso de limpieza» (100 es una cifra provisional, escrita a la vista como supuesto, que hay que confirmar antes de dar el requisito por cerrado).

## Al revés: clasifica cuatro requisitos

La palabra clave va en negrita (en papel, la habrías subrayado). Salen cuatro etiquetas distintas, como pedía el ejercicio.

| Requisito | Cómo empieza | Patrón | Por qué |
|---|---|---|---|
| R1 | «**CUANDO** una persona cancela su reserva…» | Por evento | Cancelar ocurre en un instante. Liberar la franja y mostrar el mensaje son dos efectos del mismo evento, como en RF-008 de ReservaSalas: sigue siendo un solo requisito. |
| R2 | «El sistema deberá mostrar…» (sin palabra clave) | Ubicuo | Se cumple siempre, no depende de nada. Es, palabra por palabra, RF-004 de ReservaSalas. |
| R3 | «**DONDE** la empresa tenga activado el registro de visitas…» | Opcional | Solo se aplica en las instalaciones que tienen activada esa función; en las demás, este requisito no cuenta. |
| R4 | «**MIENTRAS** una solicitud de vacaciones esté pendiente…, **CUANDO** la persona cambia las fechas…» | Complejo | Dos palabras clave: un estado (pendiente de aprobación) y un evento (cambiar las fechas), con el estado delante, igual que RF-014 de vacaciones. |

Si dudabas entre «por evento» y «complejo» en R1, fíjate en que no hay ningún estado: un solo disparador con dos efectos sigue siendo CUANDO.

## Caza el error

Cada requisito tenía un fallo distinto. En los cuatro arreglos no desaparece nada: cada cosa se muda a su sitio.

### E1: mezcla tecnología

- **Requisito con fallo:** «CUANDO una persona confirma una reserva, el sistema deberá guardarla en la tabla reservas de PostgreSQL y mostrar un mensaje de confirmación con sala, fecha y hora.»
- **Qué falla:** «la tabla reservas de PostgreSQL» dice dónde y cómo se guarda, y eso es una decisión del plan técnico (`plan.md`), no de la especificación. Si mañana cambia la base de datos, el requisito dejaría de ser cierto aunque el sistema hiciera exactamente lo mismo.
- **Cómo queda (RF-003 de ReservaSalas, literal):** CUANDO una persona confirma una reserva, el sistema deberá guardarla y mostrar un mensaje de confirmación con sala, fecha y hora.
- **Ojo:** «guardarla y mostrar un mensaje» no es el fallo de «dos cosas»: son dos efectos del mismo evento que van siempre juntos, como en R1.

### E2: dice dos cosas

- **Requisito con fallo:** «El sistema deberá permitir reservar una sala y marcar salas en mantenimiento.»
- **Qué falla:** son dos capacidades para perfiles distintos: reservar puede hacerlo cualquier persona; marcar una sala en mantenimiento, solo administración. Una mitad podría cumplirse y la otra no.
- **Cómo queda, en dos requisitos (de ReservaSalas, literales):**
  - **RF-003**: CUANDO una persona confirma una reserva, el sistema deberá guardarla y mostrar un mensaje de confirmación con sala, fecha y hora.
  - **RF-009**: DONDE la persona tenga permisos de administración, el sistema deberá permitir marcar una sala en mantenimiento.
- **Señal de que eran dos:** al separarlas, cada mitad pide un patrón distinto (CUANDO y DONDE).

### E3: es vago

- **Requisito con fallo:** «El sistema deberá ser rápido y fácil de usar al mostrar la disponibilidad.»
- **Qué falla:** «rápido» y «fácil de usar» son adjetivos sin cifra; nadie puede comprobarlos con un sí o un no.
- **Cómo queda:** los adjetivos se convierten en cifras y pasan a los criterios de éxito (CE), y lo que hace el sistema se queda en un requisito. Los tres son de ReservaSalas, literales:
  - **CE-004** (el «rápido»): El listado de disponibilidad se muestra en menos de 2 segundos.
  - **CE-003** (el «fácil de usar»): El 90 % de las personas completan una reserva sin ayuda la primera vez que usan la aplicación.
  - **RF-002** (el «mostrar la disponibilidad»): CUANDO una persona indica una fecha y una franja horaria, el sistema deberá mostrar qué salas están libres en esa franja.

### E4: le falta el disparador

- **Requisito con fallo:** «El sistema deberá rechazar la solicitud de vacaciones.»
- **Qué falla:** no dice cuándo ni bajo qué condición. Tal como está, es un requisito ubicuo: obligaría a rechazar todas las solicitudes, siempre.
- **Cómo queda (RF-004 de vacaciones, literal):** SI una persona pide más días de los que tiene disponibles, ENTONCES el sistema deberá rechazar la solicitud e indicar cuántos días le quedan.
- **Otras condiciones válidas:** la fecha de inicio ya ha pasado (RF-005) o es anterior al quinto día laborable después del envío (RF-006). Si no sabes qué casos son, no los inventes: `[NECESITA ACLARACIÓN: ¿en qué casos rechaza el sistema una solicitud?]`. Y si quien rechaza es la manager, el disparador es su decisión, así que es un CUANDO (RF-009).

## Supuestos y aclaraciones pendientes

Lo que las frases no decían y cómo lo hemos resuelto. En una especificación de verdad, los supuestos van a su sección «Supuestos» y los marcadores se resuelven en la fase de aclarar, preguntando a quien encarga el sistema, no adivinando; y la especificación no se da por aprobada hasta que quien encarga confirma las cifras provisionales.

| Frase | Qué no decía | Cómo queda |
|---|---|---|
| F03 | Si la cafetera explica el rechazo | Decisión nuestra: indica que falta agua. Se puede quitar. |
| F04 | Cuánto tiempo queda desbloqueado el torno | Supuesto: 5 segundos, a confirmar con Seguridad. |
| F04 | Qué tarjeta vale | Supuesto: «válida» quiere decir dada de alta y no bloqueada. |
| F11 | Qué es «fuera de horario» | Supuesto: de 20:00 a 08:00, todos los días (lo contrario del horario de oficina de ReservaSalas). A confirmar con Seguridad. |
| F12 | Cada cuánto toca limpiar | `[NECESITA ACLARACIÓN: ¿cuántos cafés o cuántos días?]` |
| F12 | Cuánto es «fácil de limpiar» | `[NECESITA ACLARACIÓN: ¿cuántos minutos?]`, dentro de un criterio de éxito |

## En tres frases

1. Las doce frases vagas se convierten en requisitos con una sola lectura: el sistema (o la cafetera, o el torno) como sujeto, el verbo «deberá» y la palabra clave que toca, elegida en el orden SI…, ENTONCES → CUANDO → MIENTRAS → DONDE → ubicuo.
2. Lo que no se puede comprobar se arregla con datos, no con mejores palabras: «razonable», «que se entere» o «claramente» pasan a ser 4 horas, «las fechas y los días laborables» o «cuántos días le quedan», y lo que no sabes queda a la vista como supuesto o con `[NECESITA ACLARACIÓN: …]`.
3. Los cuatro fallos del «caza el error» se corrigen mudando cada cosa a su sitio: la tecnología al plan técnico, cada capacidad a su propio requisito, los adjetivos a los criterios de éxito y la condición delante de la respuesta.

## Siguiente paso

Vuelve al [ejercicio 02](../02-practicar-requisitos-ears.md) y termina el paso 7: apunta en qué te has desviado y por qué. Después sigue con el [ejercicio 03: ReservaSalas paso a paso](../03-reserva-salas-paso-a-paso.md), donde el asistente de IA genera requisitos como estos a partir de una descripción y tú los revisas con lo que acabas de practicar.

---

⬅️ [Ejercicio 02](../02-practicar-requisitos-ears.md) · 🏠 [Índice de soluciones](README.md)
