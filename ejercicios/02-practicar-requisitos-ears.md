# Ejercicio 02: practicar requisitos EARS

> **Para quién:** quien vaya a escribir o revisar requisitos, sepa programar o no · **Tiempo de lectura:** ~5 min (hacerlo: 30 min, con la comparación) · **Nivel:** 🟢 básico

Este ejercicio va directo al músculo que más se usa al especificar: coger una frase ambigua y convertirla en algo que se pueda comprobar. Hay doce frases para reescribir, cuatro requisitos para clasificar y cuatro errores que encontrar.

Si no has leído [Escribir requisitos claros con EARS](../docs/05-escribir-requisitos-claros-ears.md), puedes tenerlo abierto al lado. No necesitas instalar nada.

**Qué vas a encontrar**

- [Objetivo](#objetivo)
- [Qué necesitas](#qué-necesitas)
- [Pasos](#pasos)
- [Errores frecuentes](#errores-frecuentes)
- [Comprueba lo que has aprendido](#comprueba-lo-que-has-aprendido)
- [Solución o ejemplo resuelto](#solución-o-ejemplo-resuelto)
- [En tres frases](#en-tres-frases)
- [Siguiente paso](#siguiente-paso)

## Objetivo

Al terminar deberías ser capaz de transformar algo como «que avise si hay choque» en un requisito que diga cuándo ocurre el problema y qué tiene que hacer el sistema. También practicarás cuatro fallos muy comunes: meter tecnología donde no toca, juntar dos cosas en una frase, usar términos vagos y olvidar el disparador.

## Qué necesitas

- Haber leído [Escribir requisitos claros con EARS](../docs/05-escribir-requisitos-claros-ears.md), o al menos tener a mano la tabla de patrones del paso 1.
- Tiempo: unos 30 minutos: 20 para hacerlo (5 por cada bloque de frases y 5 para clasificar y cazar errores) y 10 para comparar con la solución.
- Dónde escribir. Elige una opción:
  - **Opción 1: solo papel o documento.** Papel y bolígrafo, o un documento compartido. Es la opción recomendada, sepas programar o no.
  - **Opción 2: con un chat de IA autorizado.** Lo mismo que en la opción 1 y, además, el chat de IA genérico que tenga autorizado la empresa. Lo usarás solo al final, para que revise lo que tú has escrito (paso 7). No hace falta Spec Kit (la herramienta de línea de comandos que se usa en el ejercicio 03): aquí se entrena tu criterio, y en el [ejercicio 03](03-reserva-salas-paso-a-paso.md) verás cómo la herramienta genera estos requisitos y cómo los revisas tú.
- Opcional, para el paso 7: la [especificación canónica de ReservaSalas](soluciones/03-reserva-salas/spec.md), para comparar al final tus frases de ReservaSalas con las del ejemplo. Las pistas citan sus requisitos funcionales (RF-001, RF-005…; «RF» quiere decir requisito funcional) y sus criterios de éxito (CE-003, CE-004) para que sepas con qué comparar después, no para que los mires antes.

> [!IMPORTANT]
> No mires la solución ni la especificación canónica hasta el paso 7: las dos contienen las respuestas de las frases de ReservaSalas. Escribir un requisito regular y arreglarlo enseña más que leer uno bueno.

## Pasos

1. **Ten las cinco plantillas a la vista.** Copia esta tabla o déjala abierta en otra pestaña. Todos los requisitos de este ejercicio se escriben con una de estas cinco frases, o con una combinación de ellas. Las palabras clave van en mayúsculas y el verbo es siempre «deberá».

   | Patrón | Plantilla | Úsalo cuando… |
   |---|---|---|
   | Ubicuo | «El sistema deberá [respuesta].» | Se cumple siempre, pase lo que pase. |
   | Por evento | «CUANDO [disparador], el sistema deberá [respuesta].» | Algo ocurre en un momento concreto. |
   | Por estado | «MIENTRAS [estado], el sistema deberá [respuesta].» | Algo dura un tiempo. |
   | Comportamiento no deseado | «SI [condición], ENTONCES el sistema deberá [respuesta].» | Un error o una situación que queremos evitar. |
   | Opcional | «DONDE [característica o perfil], el sistema deberá [respuesta].» | Solo en algunas instalaciones o para algunos perfiles. |
   | Complejo | «MIENTRAS [estado], CUANDO [disparador], el sistema deberá [respuesta].» | Hacen falta dos condiciones a la vez. |

   Tres reglas que no cambian: un requisito es **una** frase que dice **una** cosa comprobable; el sujeto es siempre el sistema (la aplicación, la cafetera, el torno), nunca la persona; y no aparece ninguna tecnología. Si te atascas eligiendo patrón, el [diagrama de decisión](../diagramas/05-anatomia-de-un-requisito-ears.md) te lleva al correcto con cuatro preguntas.

   Qué deberías tener: la tabla a la vista y una hoja (o documento) con cinco apartados vacíos: «Bloque A», «Bloque B», «Bloque C», «Clasificar» y «Caza el error».

   - [ ] Tengo la tabla a mano y sé que el sujeto siempre es el sistema.

2. **Bloque A: una frase vaga, un patrón claro.** Reescribe cada una de estas cuatro frases como un requisito EARS. Cada una encaja en un solo patrón; tu trabajo es encontrarlo y completar el hueco con lo que de verdad hace el sistema. La etiqueta entre corchetes dice a qué sistema pertenece la frase. Donde pone «…», escribe tu requisito.

   ```text
   F01 [ReservaSalas]  «La app tiene que enseñar las salas.»
   RF: …

   F02 [Vacaciones]    «Cuando alguien pida vacaciones, que se entere su jefe.»
   RF: …

   F03 [Cafetera]      «La cafetera no debería dejar que se haga café si no hay agua.»
   RF: …

   F04 [Torno]         «El torno tiene que abrirse con la tarjeta.»
   RF: …
   ```

   Pistas. F01: ¿qué datos de cada sala hacen falta para elegir una (dónde está, cuánta gente cabe)? Compara después con RF-001 del ejemplo canónico. F02: «que se entere» no es comprobable; di qué recibe el manager y con qué datos. F03: es una situación que queremos evitar. F04: ¿con cualquier tarjeta? ¿Cuánto tiempo queda desbloqueado? Si no lo sabes, no lo inventes: deja un marcador `[NECESITA ACLARACIÓN: …]`, que es justo lo que hace el asistente de IA cuando le falta un dato. Si necesitas una cifra provisional para seguir, escríbela a la vista como supuesto («se asume 5 segundos; confirmar con Seguridad») y no des el requisito por cerrado hasta que quien decide la confirme.

   Qué deberías ver: cuatro frases que empiezan por «El sistema deberá», «CUANDO» o «SI», cuyo sujeto es el sistema, la cafetera o el torno, y que alguien podría comprobar con un sí o un no.

   - [ ] He reescrito F01 a F04 y cada una usa un solo patrón.

3. **Bloque B: elegir bien entre patrones parecidos.** Igual que antes, pero ahora las frases se prestan a confusión: CUANDO o MIENTRAS, SI o MIENTRAS, DONDE o ubicuo. Decide primero si lo que describe la frase ocurre en un instante, dura un tiempo, es algo que queremos evitar o solo afecta a algunos perfiles.

   ```text
   F05 [ReservaSalas]  «Si una sala está en obras, que no se pueda reservar.»
   RF: …

   F06 [Vacaciones]    «Los de RRHH pueden ver las vacaciones de todo el mundo.»
   RF: …

   F07 [Cafetera]      «Mientras se calienta, que se vea.»
   RF: …

   F08 [ReservaSalas]  «Que avise si la reserva choca con otra.»
   RF: …
   ```

   Pistas. F05: «en obras» dura días; en ReservaSalas ese estado se llama «en mantenimiento» (compara después con RF-007 del ejemplo). F06: un permiso que solo tienen algunos perfiles. F07: ¿qué significa «que se vea»? Di qué muestra la cafetera y mientras qué. F08: «avisar» se queda corto; ¿rechaza la reserva? ¿Qué le dice a la persona? Compara después con RF-005 del ejemplo.

   Qué deberías ver: dos requisitos con MIENTRAS, uno con DONDE y uno con SI… ENTONCES. Si te han salido cuatro CUANDO, vuelve a leer la columna «Úsalo cuando…» de la tabla.

   - [ ] He reescrito F05 a F08 y sé explicar por qué ese patrón y no otro.

4. **Bloque C: frases que esconden más de un requisito.** Estas cuatro frases son las que llegan de verdad en un correo o en una reunión. Cada una esconde dos requisitos, una cifra que falta o una parte que no es un requisito. Puedes escribir dos requisitos para una misma frase (numéralos a y b) y, donde falte un dato, dejar un marcador `[NECESITA ACLARACIÓN: …]` o, si necesitas seguir, una cifra provisional escrita a la vista como supuesto.

   ```text
   F09 [ReservaSalas]  «Las reservas deben ser razonables: ni muy largas ni a deshoras.»
   RF a: …
   RF b: …

   F10 [Vacaciones]    «Que no se puedan pedir más días de los que te quedan y, si se intenta, que lo diga claramente.»
   RF: …

   F11 [Torno]         «Fuera de horario, solo entra la gente de seguridad.»
   RF: …

   F12 [Cafetera]      «Que sea fácil de limpiar y avise cuando toque.»
   RF: …
   ```

   Pistas. F09: «razonable» no se puede comprobar; las cifras de ReservaSalas son 4 horas como máximo y horario de 08:00 a 20:00 (el ejemplo canónico junta los límites en RF-006 porque la respuesta es la misma; dos requisitos separados también valen). F10: parece dos cosas, pero «rechazar e indicar cuántos días quedan» es una sola respuesta a una sola condición. F11: hay un estado (fuera de horario) y un evento (alguien pasa la tarjeta), así que toca el patrón complejo; además tienes que decir qué horario es «fuera de horario». F12: una de las dos partes no es un requisito funcional (nadie puede comprobar «fácil de limpiar» con un sí o un no); la otra necesita saber cuándo «toca».

   Qué deberías ver: entre cinco y siete requisitos para cuatro frases (cuatro si has juntado los dos límites de F09 en un solo SI, como hace RF-006), al menos un marcador de aclaración o una cifra provisional anotada como supuesto, y una nota del estilo «"fácil de limpiar" no es un requisito: pedir una cifra o pasarlo a criterios de éxito».

   - [ ] He reescrito F09 a F12 y he separado lo que eran dos cosas.

5. **Al revés: clasifica cuatro requisitos.** Ahora los requisitos ya están bien escritos. Di qué patrón usa cada uno (ubicuo, por evento, por estado, comportamiento no deseado, opcional o complejo) y subraya la palabra clave que te lo indica.

   ```text
   R1  «CUANDO una persona cancela su reserva, el sistema deberá liberar la franja y mostrar un mensaje de confirmación.»
   Patrón: …

   R2  «El sistema deberá mostrar, junto a cada reserva, el nombre de la persona responsable.»
   Patrón: …

   R3  «DONDE la empresa tenga activado el registro de visitas, el torno deberá pedir el nombre de la persona visitante antes de desbloquearse.»
   Patrón: …

   R4  «MIENTRAS una solicitud de vacaciones esté pendiente de aprobación, CUANDO la persona cambia las fechas, el sistema deberá descartar la solicitud anterior y crear una nueva con las fechas nuevas.»
   Patrón: …
   ```

   Pista. Fíjate solo en cómo empieza la frase; si tiene dos palabras clave, es complejo. En R1, «liberar la franja y mostrar un mensaje» no son dos requisitos: son dos efectos del mismo evento, igual que en RF-008 del ejemplo.

   Qué deberías ver: cuatro etiquetas distintas. Si has puesto la misma dos veces, una está mal.

   - [ ] He clasificado R1 a R4 con cuatro patrones distintos.

6. **Caza el error.** Estos cuatro requisitos tienen forma de requisito, pero cada uno tiene un fallo distinto: uno mezcla tecnología, uno dice dos cosas, uno es vago y a uno le falta el disparador. Averigua cuál es cuál, explica en una línea por qué está mal y reescríbelo (si hace falta, en dos requisitos o como criterio de éxito).

   ```text
   E1  «CUANDO una persona confirma una reserva, el sistema deberá guardarla en la tabla reservas de PostgreSQL y mostrar un mensaje de confirmación con sala, fecha y hora.»
   Fallo: …
   Arreglo: …

   E2  «El sistema deberá permitir reservar una sala y marcar salas en mantenimiento.»
   Fallo: …
   Arreglo: …

   E3  «El sistema deberá ser rápido y fácil de usar al mostrar la disponibilidad.»
   Fallo: …
   Arreglo: …

   E4  «El sistema deberá rechazar la solicitud de vacaciones.»
   Fallo: …
   Arreglo: …
   ```

   Pistas. Pregúntate, para cada uno: ¿nombra una herramienta, un lenguaje o un «dónde se guarda»? ¿Podría cumplirse la mitad y la otra mitad no? ¿Lleva un adjetivo sin cifra? ¿Se sabe en qué momento o bajo qué condición actúa el sistema? Para E3, piensa en los criterios de éxito (la sección de la especificación que dice, con cifras, cómo sabremos que el sistema ha funcionado): los adjetivos no desaparecen, se convierten en cifras y cambian de sitio; compara después con CE-003 y CE-004 del ejemplo canónico. Para E2, piensa quién puede hacer cada una de las dos cosas (compara después con RF-003 y RF-009 del ejemplo).

   Qué deberías ver: cuatro diagnósticos distintos; al menos cuatro requisitos corregidos (E2 se parte en dos) y, para E3, uno o dos criterios de éxito con cifra, con o sin un requisito que diga qué muestra el sistema.

   - [ ] He identificado los cuatro fallos y he reescrito E1 a E4.

7. **Compara y, si quieres, pide una segunda opinión.** Abre la [solución comentada](soluciones/02-requisitos-ears-resueltos.md) y compara frase por frase. No busques coincidencia literal: busca que tu requisito tenga el mismo patrón, el mismo disparador o condición y una respuesta igual de comprobable. Anota en qué te has desviado y por qué.

   Si has elegido la opción 2, pega en tu chat de IA autorizado el siguiente *prompt* (la instrucción que le escribes al asistente), sustituyendo el bloque final por tus requisitos:

   ```text
   Actúa como revisor de requisitos. Te paso una lista de requisitos escritos en EARS (Easy Approach to Requirements Syntax) en castellano. Las únicas plantillas válidas son:
   1. «El sistema deberá <respuesta>.»
   2. «CUANDO <disparador>, el sistema deberá <respuesta>.»
   3. «MIENTRAS <estado>, el sistema deberá <respuesta>.»
   4. «SI <condición>, ENTONCES el sistema deberá <respuesta>.»
   5. «DONDE <característica o perfil>, el sistema deberá <respuesta>.»
   y la combinación «MIENTRAS…, CUANDO…, el sistema deberá…».

   Para cada requisito dime: (a) qué patrón usa; (b) si cumple las reglas: una sola frase, una sola cosa comprobable, el sujeto es el sistema (que puede llamarse «la cafetera» o «el torno» cuando el requisito es de esos aparatos), verbo «deberá», sin tecnología y sin adjetivos sin cifra; (c) si no las cumple, una versión corregida. No cambies el significado y no añadas requisitos nuevos. Si falta un dato, señálalo como [NECESITA ACLARACIÓN: …] en vez de inventarlo.

   Requisitos:
   F01: …
   F02: …
   ```

   Qué deberías ver: una tabla o lista con un veredicto por requisito. Es razonable que el asistente te señale dos o tres cosas que no habías visto (un «deberá» que se te ha escapado como «debería», un adjetivo suelto) y también que proponga cambios discutibles: la última palabra es tuya, y esa es la idea. Cada asistente responde distinto; si el tuyo se pone a proponer tecnología, recuérdale la regla «sin tecnología» y vuelve a pedirlo.

   - [ ] He comparado con la solución y he apuntado al menos una cosa que haría distinto la próxima vez.

## Errores frecuentes

| Síntoma | Causa | Cómo arreglarlo |
|---|---|---|
| Todos tus requisitos empiezan por CUANDO. | Tratas como evento cosas que son estados o reglas permanentes. | Pregunta: ¿dura un tiempo? MIENTRAS. ¿Se cumple siempre? Ubicuo. ¿Es un error? SI… ENTONCES. |
| Has escrito «el usuario deberá…» o «la persona deberá…». | El sujeto es quien usa el sistema, no el sistema. | Da la vuelta a la frase: qué hace el sistema cuando la persona hace algo. |
| La frase ocupa tres líneas y tiene varias «y». | Hay dos o más requisitos mezclados. | Pártela: si una mitad podría cumplirse y la otra no, son dos requisitos. |
| No sabes qué cifra poner (segundos, días, horas). | Falta un dato que solo conoce quien encarga el sistema. | No la inventes: deja `[NECESITA ACLARACIÓN: …]` y pregúntalo a quien decide. Si necesitas una cifra provisional para seguir, escríbela a la vista en «Supuestos» («se asume…; confirmar con…») y no des la especificación por aprobada hasta que la confirme quien encarga. |
| Usas «debería», «podría», «tiene que» o «se espera que». | Los verbos blandos convierten el requisito en un deseo. | Siempre «deberá». Si algo es opcional de verdad, va con DONDE. |
| Dudas entre SI y CUANDO. | Los dos describen algo que pasa. | SI para lo que queremos evitar o rechazar; CUANDO para el funcionamiento normal. |
| Te ha salido «rápido», «intuitivo» o «correctamente». | Adjetivo sin medida. | Ponle cifra (menos de 2 segundos) o conviértelo en un criterio de éxito. |

## Comprueba lo que has aprendido

1. ¿Cuál es la diferencia entre CUANDO y MIENTRAS? Pon un ejemplo de cada uno con la cafetera.
2. ¿Por qué «el sistema deberá ser rápido» no es un requisito, y qué haces con esa frase?
3. Estás reescribiendo F04 (el torno) y no sabes cuántos segundos queda desbloqueado. ¿Qué escribes?
4. ¿Qué patrón usas para algo que solo aplica a algunos perfiles o a algunas oficinas?
5. Un requisito dice «guardar la reserva en PostgreSQL». ¿Está mal aunque el proyecto vaya a usar PostgreSQL?

<details><summary>Ver respuestas</summary>

1. CUANDO describe algo que ocurre en un instante (se pulsa un botón, llega una solicitud); MIENTRAS describe un estado que dura (la cafetera está calentando, la sala está en mantenimiento). «CUANDO la persona pulsa el botón de café, la cafetera deberá empezar a preparar un café» frente a «MIENTRAS la cafetera esté calentando el agua, la cafetera deberá mantener encendido el indicador de "calentando"».
2. Porque no se puede comprobar con un sí o un no: ¿rápido para quién, haciendo qué? Se convierte en una cifra («el listado de disponibilidad se muestra en menos de 2 segundos») y, como habla del resultado global y no de un comportamiento concreto, suele ir en los criterios de éxito (CE-004 del ejemplo).
3. El marcador `[NECESITA ACLARACIÓN: ¿cuántos segundos permanece desbloqueado el torno?]`, y preguntarlo a quien decide (aquí, Seguridad). Si necesitas una cifra provisional para seguir trabajando, la escribes a la vista como supuesto («se asume 5 segundos; confirmar con Seguridad») y no das el requisito por cerrado hasta que Seguridad la confirme. Lo que no se hace es inventarla a escondidas ni dejar la frase sin cifra.
4. DONDE: «DONDE la persona tenga permisos de administración, el sistema deberá permitir marcar una sala en mantenimiento» (RF-009 del ejemplo).
5. Sí, está mal. La especificación dice qué hace el sistema; dónde se guarda es una decisión del plan técnico. Si mañana se cambia la base de datos, el requisito «guardar la reserva» sigue siendo válido; el otro no.

</details>

## Solución o ejemplo resuelto

Las doce reescrituras, la clasificación y el «caza el error», comentados uno a uno, están en [soluciones/02-requisitos-ears-resueltos.md](soluciones/02-requisitos-ears-resueltos.md). Son ejemplos de buena respuesta, no la única correcta: dos requisitos distintos pueden ser igual de buenos si los dos se comprueban con un sí o un no. Los de ReservaSalas puedes contrastarlos además con la [especificación canónica](soluciones/03-reserva-salas/spec.md).

## En tres frases

1. Un requisito EARS es una frase con el sistema como sujeto, el verbo «deberá» y, si hace falta, un disparador (CUANDO), un estado (MIENTRAS), una condición a evitar (SI… ENTONCES) o un perfil (DONDE).
2. Las frases vagas se arreglan preguntando qué hace exactamente el sistema, en qué momento y con qué cifra; lo que no sepas se marca como aclaración, no se inventa a escondidas.
3. Los cuatro fallos que más cuestan después son tecnología en el requisito, dos cosas en una frase, adjetivos sin medida y acciones sin disparador.

## Siguiente paso

Continúa con [ReservaSalas paso a paso](03-reserva-salas-paso-a-paso.md), donde verás cómo el asistente de IA genera estos requisitos a partir de una descripción y cómo los revisas tú. Si vas a hacerlo sin instalar nada, pasa a la [dinámica de equipo de 20 minutos](04-dinamica-de-equipo-20-minutos.md) o directamente a [arreglar una especificación mala](05-arreglar-una-especificacion-mala.md).

---

⬅️ [Anterior: Tu primera especificación sin código](01-tu-primera-especificacion-sin-codigo.md) · 🏠 [Índice de ejercicios](README.md) · ➡️ [Siguiente: ReservaSalas paso a paso](03-reserva-salas-paso-a-paso.md)
