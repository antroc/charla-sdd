# Ejercicio 04 resuelto: dinámica de equipo de 20 minutos

> **Para quién:** cualquier persona que haya hecho el ejercicio 04 · **Tiempo de lectura:** ~15 min · **Nivel:** 🟢 básico

> [!NOTE]
> Es un ejemplo, no la única respuesta correcta. Si tu hoja usa el mismo patrón, el mismo disparador o condición y una respuesta que se comprueba con un sí o un no, es igual de buena aunque no coincida palabra por palabra. Dos decisiones nuestras son discutibles: la P1 de la tarjeta 3, escrita desde quien apunta el estado y no desde quien lo mira, y la de la tarjeta 6, que resuelve el aviso y deja «quién está dentro» para la P3.

**Qué vas a encontrar**

- [Tarjeta 1: plazas de parking](#tarjeta-1-plazas-de-parking)
- [Tarjeta 2: dudas de nóminas](#tarjeta-2-dudas-de-nóminas)
- [Tarjeta 3: estado de los proyectos](#tarjeta-3-estado-de-los-proyectos)
- [Tarjeta 4: material de oficina](#tarjeta-4-material-de-oficina)
- [Tarjeta 5: cursos internos](#tarjeta-5-cursos-internos)
- [Tarjeta 6: visitas en recepción](#tarjeta-6-visitas-en-recepción)
- [Qué tienen en común las seis hojas](#qué-tienen-en-común-las-seis-hojas)
- [En tres frases](#en-tres-frases)
- [Siguiente paso](#siguiente-paso)

Estas son las seis tarjetas del [ejercicio 04](../04-dinamica-de-equipo-20-minutos.md) con su hoja rellena, en el mismo diseño que la plantilla de una página.
Compara tu hoja con la de tu tarjeta después de la dinámica, no antes: si la lees antes, pierdes justo lo que enseña, decidir qué preguntar y qué dejar fuera.
Busca el mismo [patrón EARS](../../docs/05-escribir-requisitos-claros-ears.md#los-cinco-patrones-y-el-sexto), el mismo disparador y una respuesta que se pueda comprobar; no hace falta que las palabras coincidan.
El apartado 4 queda en blanco porque lo rellena la sala, y donde faltaba una cifra la hoja no la inventa (ver [«Si te falta un dato»](../../docs/05-escribir-requisitos-claros-ears.md#si-te-falta-un-dato)).

## Tarjeta 1: plazas de parking

- **La petición:** «Una app para que la gente reserve plazas de parking.»
- **El problema real:** 30 plazas se reparten por correo cada lunes y siempre hay quejas; hace falta un reparto que se pueda consultar y ajustar sin esperar al lunes.

**La hoja resuelta** (la misma que el ejercicio da como referencia, con los textos idénticos y las líneas ajustadas al ancho de la plantilla)
```text
HOJA DE TRABAJO · Dinámica SDD de 20 minutos  Grupo: ___  Tarjeta: 1
======================================================================
LA PETICIÓN (copia la frase entre comillas de la tarjeta)
«Una app para que la gente reserve plazas de parking.»

1. HISTORIAS (0-5 min) · Como [quién], quiero [qué], para [por qué]
P1 (imprescindible): Como empleado que viene en coche, quiero ver qué
                     plazas están libres un día y reservar una, para
                     no depender del correo del lunes.
P2: Como empleado, quiero liberar mi plaza si no voy a venir, para que
    otra persona la use.
P3: Como responsable de Oficina, quiero ver quién tiene cada plaza
    hoy, para resolver quejas.

2. REQUISITOS EARS (5-10 min) · sujeto: el sistema · verbo: «deberá»
   Plantillas: «El sistema deberá…» · «CUANDO…, el sistema deberá…» ·
   «SI…, ENTONCES el sistema deberá…» ·
   «MIENTRAS…, el sistema deberá…» · «DONDE…, el sistema deberá…»
RF-1 El sistema deberá mostrar las plazas libres de cada día con su
     número y su planta.
RF-2 CUANDO una persona confirma una reserva, el sistema deberá
     guardarla y mostrar la plaza, el día y el nombre de la persona
     responsable.
RF-3 SI la plaza elegida ya está reservada ese día, ENTONCES el
     sistema deberá rechazar la reserva e indicar quién la tiene.
RF-4 MIENTRAS una plaza esté marcada como no disponible, el sistema
     deberá impedir reservarla.
RF-5 DONDE la persona tenga permisos de Oficina, el sistema deberá
     permitir marcar una plaza como no disponible.

3. PREGUNTAS DE ACLARACIÓN (10-13 min) · para quien lo pide, antes
   de construir nada · afecta a: historia, requisito o alcance
A1: ¿Con cuánta antelación como máximo se puede reservar?
    → afecta a: RF-2, casos límite
A2: ¿Hay plazas fijas asignadas a alguien?    → afecta a: P1, RF-1
A3: ¿Se puede reservar más de un día seguido? → afecta a: alcance

4. VAGUEDADES CAZADAS (13-18 min) · las vuestras y las de otros grupos
   Tipos: adjetivo sin cifra · dos cosas en una · sin disparador ·
   tecnología · el sujeto es la persona, no el sistema
Grupo ___: «______________________________» → tipo: __________________
Grupo ___: «______________________________» → tipo: __________________

FUERA DE ALCANCE (lo que decidís NO hacer en la primera versión):
plazas de visitas; abonos mensuales; aviso por correo.
```

**Vaguedades que suelen aparecer**

| Frase vaga típica | Tipo | Cómo queda bien |
|---|---|---|
| «El sistema deberá ser fácil de usar para reservar la plaza» | adjetivo sin cifra | Se cambia por lo que hace el sistema, como RF-1 (mostrar las plazas libres de cada día), y la facilidad pasa a un criterio de éxito con cifra que da Ana. |
| «El sistema deberá permitir reservar y liberar plazas» | dos cosas en una | Un requisito por disparador: RF-2 para confirmar la reserva y, aparte, «CUANDO una persona libera su plaza, el sistema deberá marcarla como libre ese día». |
| «El sistema deberá rechazar la reserva» | sin disparador | Falta el cuándo. RF-3 pone la condición delante: «SI la plaza elegida ya está reservada ese día, ENTONCES…». Sin ella, obligaría a rechazar todas las reservas. |

## Tarjeta 2: dudas de nóminas

- **La petición:** «Un bot que responda dudas de nóminas.»
- **El problema real:** RRHH contesta por correo las mismas 20 preguntas cada mes; hay que quitarle esa repetición sin que el sistema llegue a enseñar la nómina de nadie.
- **Lo delicado:** una nómina es un dato personal. RF-3 impide mostrar los datos de una nómina concreta y remite al canal de RRHH; A1 y A2 preguntan qué hace el sistema si no sabe responder y si podrá ver las nóminas.

**La hoja resuelta**
```text
HOJA DE TRABAJO · Dinámica SDD de 20 minutos  Grupo: ___  Tarjeta: 2
======================================================================
LA PETICIÓN (copia la frase entre comillas de la tarjeta)
«Un bot que responda dudas de nóminas.»

1. HISTORIAS (0-5 min) · Como [quién], quiero [qué], para [por qué]
P1 (imprescindible): Como empleado, quiero consultar mis dudas
                     habituales de nómina y recibir una respuesta
                     aprobada, para no depender del correo de RRHH.
P2: Como persona de RRHH, quiero retirar una respuesta que ya no es
    válida, para que nadie reciba información antigua.
P3: Como persona de RRHH, quiero ver las dudas que no han tenido
    respuesta, para saber qué respuestas hay que añadir.

2. REQUISITOS EARS (5-10 min) · sujeto: el sistema · verbo: «deberá»
   Plantillas: «El sistema deberá…» · «CUANDO…, el sistema deberá…» ·
   «SI…, ENTONCES el sistema deberá…» ·
   «MIENTRAS…, el sistema deberá…» · «DONDE…, el sistema deberá…»
RF-1 El sistema deberá dar solo respuestas aprobadas por RRHH.
RF-2 CUANDO una persona formula una duda que tiene respuesta aprobada,
     el sistema deberá mostrarle esa respuesta.
RF-3 SI una persona pide datos de una nómina concreta, ENTONCES el
     sistema deberá rechazar la consulta, sin mostrar ningún dato, y
     remitir a la persona al canal de RRHH.
RF-4 MIENTRAS una respuesta esté marcada como retirada, el sistema
     deberá dejar de mostrarla.
RF-5 DONDE la persona tenga permisos de RRHH, el sistema deberá
     permitir marcar una respuesta como retirada.

3. PREGUNTAS DE ACLARACIÓN (10-13 min) · para quien lo pide, antes
   de construir nada · afecta a: historia, requisito o alcance
A1: Si no sabe responder, ¿pasa la duda a RRHH o solo avisa?
    → afecta a: P3, RF-2
A2: ¿Podrá ver la nómina de quien pregunta?  → afecta a: RF-3, alcance
A3: ¿Quién escribe y aprueba respuestas nuevas? → afecta a: P2, RF-1

4. VAGUEDADES CAZADAS (13-18 min) · las vuestras y las de otros grupos
   Tipos: adjetivo sin cifra · dos cosas en una · sin disparador ·
   tecnología · el sujeto es la persona, no el sistema
Grupo ___: «______________________________» → tipo: __________________
Grupo ___: «______________________________» → tipo: __________________

FUERA DE ALCANCE (lo que decidís NO hacer en la primera versión):
nóminas concretas; reclamaciones; historial de conversaciones.
```

**Vaguedades que suelen aparecer**

| Frase vaga típica | Tipo | Cómo queda bien |
|---|---|---|
| «El bot consultará la base de conocimiento de RRHH» | tecnología | RF-1: «El sistema deberá dar solo respuestas aprobadas por RRHH». Se dice qué se garantiza, no dónde se guardan las respuestas. |
| «RRHH deberá mantener las respuestas al día» | el sujeto es la persona | Lo que hace el sistema para que RRHH lo consiga: RF-5, «DONDE la persona tenga permisos de RRHH, el sistema deberá permitir marcar una respuesta como retirada». |
| «El bot deberá responder bien y rápido» | adjetivo sin cifra | «Bien» se comprueba con RF-1 y RF-2 (la respuesta está aprobada); «rápido» pasa a un criterio de éxito con cifra: `[NECESITA ACLARACIÓN: ¿en cuántos segundos?]`. |

## Tarjeta 3: estado de los proyectos

- **La petición:** «Un panel con el estado de los proyectos.»
- **El problema real:** Marta recopila a mano, cada semana, el estado de 8 proyectos en una presentación; el dato lo tiene cada responsable, y juntarlo recae en una sola persona.

**La hoja resuelta**
```text
HOJA DE TRABAJO · Dinámica SDD de 20 minutos  Grupo: ___  Tarjeta: 3
======================================================================
LA PETICIÓN (copia la frase entre comillas de la tarjeta)
«Un panel con el estado de los proyectos.»

1. HISTORIAS (0-5 min) · Como [quién], quiero [qué], para [por qué]
P1 (imprescindible): Como responsable de proyecto, quiero apuntar el
                     estado del mío en un solo sitio, para que
                     dirección y managers lo vean sin recopilar nada.
P2: Como manager, quiero ver qué proyectos no se han actualizado esta
    semana, para reclamar el dato a su responsable.
P3: Como miembro de dirección, quiero ver solo los proyectos que
    necesitan atención, para centrar mi tiempo en ellos.

2. REQUISITOS EARS (5-10 min) · sujeto: el sistema · verbo: «deberá»
   Plantillas: «El sistema deberá…» · «CUANDO…, el sistema deberá…» ·
   «SI…, ENTONCES el sistema deberá…» ·
   «MIENTRAS…, el sistema deberá…» · «DONDE…, el sistema deberá…»
RF-1 El sistema deberá mostrar en una sola vista el estado de cada
     proyecto, su responsable y la fecha de su última actualización.
RF-2 CUANDO el responsable de un proyecto guarda su estado, el sistema
     deberá mostrarlo en la vista común con la fecha del cambio.
RF-3 SI alguien que no es responsable de un proyecto intenta cambiar
     su estado, ENTONCES el sistema deberá rechazar el cambio.
RF-4 MIENTRAS un proyecto lleve [NECESITA ACLARACIÓN: ¿cuántos días?]
     sin actualizarse, el sistema deberá marcarlo «sin actualizar».
RF-5 DONDE la persona sea responsable de un proyecto, el sistema
     deberá permitirle cambiar el estado de ese proyecto.

3. PREGUNTAS DE ACLARACIÓN (10-13 min) · para quien lo pide, antes
   de construir nada · afecta a: historia, requisito o alcance
A1: ¿Qué estados puede tener un proyecto?       → afecta a: P3, RF-1
A2: ¿Cuántos días sin cambios son demasiados?   → afecta a: RF-4, P2
A3: ¿Puede un manager cambiar proyectos ajenos? → afecta a: RF-3, RF-5

4. VAGUEDADES CAZADAS (13-18 min) · las vuestras y las de otros grupos
   Tipos: adjetivo sin cifra · dos cosas en una · sin disparador ·
   tecnología · el sujeto es la persona, no el sistema
Grupo ___: «______________________________» → tipo: __________________
Grupo ___: «______________________________» → tipo: __________________

FUERA DE ALCANCE (lo que decidís NO hacer en la primera versión):
histórico de semanas anteriores; avisos automáticos a dirección.
```

**Vaguedades que suelen aparecer**

| Frase vaga típica | Tipo | Cómo queda bien |
|---|---|---|
| «El panel deberá mostrar el estado actualizado de los proyectos» | adjetivo sin cifra | «Actualizado» se mide en días: RF-4, «MIENTRAS un proyecto lleve `[NECESITA ACLARACIÓN: ¿cuántos días?]` sin actualizarse…». |
| «El sistema deberá mostrar el estado y avisar a dirección de los retrasos» | dos cosas en una | Mostrar es RF-1; avisar es otro requisito que espera a A1, porque «retraso» no significa nada hasta saber qué estados hay. |
| «Un cuadro de mando conectado a la herramienta de gestión, con gráficos de colores» | tecnología | RF-1: «El sistema deberá mostrar en una sola vista el estado de cada proyecto…». La conexión con otras herramientas y los gráficos son decisiones del plan técnico. |

## Tarjeta 4: material de oficina

- **La petición:** «Algo para pedir material de oficina sin mandar correos.»
- **El problema real:** los pedidos por correo a Oficina se pierden, se duplican y nadie sabe si han llegado; hace falta que cada pedido tenga un estado que todos puedan ver.

**La hoja resuelta**
```text
HOJA DE TRABAJO · Dinámica SDD de 20 minutos  Grupo: ___  Tarjeta: 4
======================================================================
LA PETICIÓN (copia la frase entre comillas de la tarjeta)
«Algo para pedir material de oficina sin mandar correos.»

1. HISTORIAS (0-5 min) · Como [quién], quiero [qué], para [por qué]
P1 (imprescindible): Como empleado, quiero pedir material de oficina y
                     ver en qué estado está mi pedido, para no tener
                     que preguntar a Oficina si ha llegado.
P2: Como persona de Oficina, quiero ver en una lista los pedidos
    pendientes, para comprar y entregar sin que se pierda ninguno.
P3: Como empleado, quiero que me avisen si ya tengo un pedido igual
    pendiente, para no pedir lo mismo dos veces.

2. REQUISITOS EARS (5-10 min) · sujeto: el sistema · verbo: «deberá»
   Plantillas: «El sistema deberá…» · «CUANDO…, el sistema deberá…» ·
   «SI…, ENTONCES el sistema deberá…» ·
   «MIENTRAS…, el sistema deberá…» · «DONDE…, el sistema deberá…»
RF-1 El sistema deberá mostrar a cada persona sus pedidos con el
     estado de cada uno.
RF-2 CUANDO una persona envía un pedido, el sistema deberá registrarlo
     y mostrar una confirmación con artículo, cantidad y fecha.
RF-3 SI una persona pide un artículo que ya tiene pendiente, ENTONCES
     el sistema deberá avisarla e indicar el pedido anterior.
RF-4 MIENTRAS un pedido no esté marcado como entregado, el sistema
     deberá mantenerlo en la lista de pendientes de Oficina.
RF-5 DONDE la persona tenga permisos de Oficina, el sistema deberá
     permitir marcar un pedido como entregado.

3. PREGUNTAS DE ACLARACIÓN (10-13 min) · para quien lo pide, antes
   de construir nada · afecta a: historia, requisito o alcance
A1: ¿Se bloquea un pedido repetido o solo se avisa? → afecta a: RF-3
A2: ¿Hay una lista cerrada de artículos?     → afecta a: RF-2, RF-3
A3: ¿Hay que avisar cuando llega el pedido?  → afecta a: RF-5, alcance

4. VAGUEDADES CAZADAS (13-18 min) · las vuestras y las de otros grupos
   Tipos: adjetivo sin cifra · dos cosas en una · sin disparador ·
   tecnología · el sujeto es la persona, no el sistema
Grupo ___: «______________________________» → tipo: __________________
Grupo ___: «______________________________» → tipo: __________________

FUERA DE ALCANCE (lo que decidís NO hacer en la primera versión):
control del stock; proveedores y compras; otro tipo de material.
```

**Vaguedades que suelen aparecer**

| Frase vaga típica | Tipo | Cómo queda bien |
|---|---|---|
| «El sistema deberá evitar los pedidos duplicados» | sin disparador | Hay que decir cuándo hay un duplicado: RF-3, «SI una persona pide un artículo que ya tiene pendiente, ENTONCES…». Si se bloquea o solo se avisa, lo decide Ana (A1). |
| «Oficina deberá actualizar el estado de los pedidos» | el sujeto es la persona | Lo que hace el sistema: RF-5, «DONDE la persona tenga permisos de Oficina, el sistema deberá permitir marcar un pedido como entregado». |
| «El sistema deberá permitir pedir material y consultar su estado» | dos cosas en una | Dos requisitos con distinto disparador: RF-2, «CUANDO una persona envía un pedido…», y RF-1, mostrar cada pedido con su estado. |

## Tarjeta 5: cursos internos

- **La petición:** «Una forma de apuntarse a los cursos de formación.»
- **El problema real:** la hoja de cálculo no impide que haya cursos con más inscritos que plazas ni deja ver los que están vacíos; hace falta que el número de plazas mande.

**La hoja resuelta**
```text
HOJA DE TRABAJO · Dinámica SDD de 20 minutos  Grupo: ___  Tarjeta: 5
======================================================================
LA PETICIÓN (copia la frase entre comillas de la tarjeta)
«Una forma de apuntarse a los cursos de formación.»

1. HISTORIAS (0-5 min) · Como [quién], quiero [qué], para [por qué]
P1 (imprescindible): Como empleado, quiero ver los cursos con sus
                     plazas libres y apuntarme a uno que tenga hueco,
                     para no apuntarme a un curso lleno.
P2: Como persona de RRHH, quiero publicar un curso con su número de
    plazas, para que no se inscriban más personas de las que caben.
P3: Como persona de RRHH, quiero ver cuántas personas se han inscrito
    en cada curso, para decidir qué hacer con los que están vacíos.

2. REQUISITOS EARS (5-10 min) · sujeto: el sistema · verbo: «deberá»
   Plantillas: «El sistema deberá…» · «CUANDO…, el sistema deberá…» ·
   «SI…, ENTONCES el sistema deberá…» ·
   «MIENTRAS…, el sistema deberá…» · «DONDE…, el sistema deberá…»
RF-1 El sistema deberá mostrar, de cada curso, sus plazas totales y
     las que quedan libres.
RF-2 CUANDO una persona se apunta a un curso con plazas libres, el
     sistema deberá inscribirla y mostrarle la confirmación.
RF-3 SI un curso no tiene plazas libres, ENTONCES el sistema deberá
     rechazar la inscripción e indicar que el curso está completo.
RF-4 MIENTRAS un curso tenga menos inscripciones que el mínimo
     [NECESITA ACLARACIÓN: ¿cuántas?], el sistema deberá mostrarlo a
     RRHH como «por debajo del mínimo».
RF-5 DONDE la persona tenga permisos de RRHH, el sistema deberá
     permitir publicar un curso con su número de plazas.

3. PREGUNTAS DE ACLARACIÓN (10-13 min) · para quien lo pide, antes
   de construir nada · afecta a: historia, requisito o alcance
A1: ¿Hay lista de espera cuando se llena?    → afecta a: RF-3, alcance
A2: ¿Hay un mínimo de inscritos por curso?   → afecta a: RF-4, P3
A3: ¿Se puede cancelar la inscripción?       → afecta a: P1, RF-1

4. VAGUEDADES CAZADAS (13-18 min) · las vuestras y las de otros grupos
   Tipos: adjetivo sin cifra · dos cosas en una · sin disparador ·
   tecnología · el sujeto es la persona, no el sistema
Grupo ___: «______________________________» → tipo: __________________
Grupo ___: «______________________________» → tipo: __________________

FUERA DE ALCANCE (lo que decidís NO hacer en la primera versión):
evaluación de los cursos; certificados; visto bueno del manager.
```

**Vaguedades que suelen aparecer**

| Frase vaga típica | Tipo | Cómo queda bien |
|---|---|---|
| «Que no haya cursos vacíos» | adjetivo sin cifra | «Vacío» necesita un número: RF-4, con el mínimo que dé RRHH (A2). Y el sistema solo lo muestra; llenar los cursos sigue siendo cosa de personas. |
| «El sistema deberá guardar las inscripciones en una hoja de cálculo compartida» | tecnología | RF-2: «CUANDO una persona se apunta…, el sistema deberá inscribirla…». Dónde se guardan las inscripciones es una decisión del plan técnico. |
| «El sistema deberá controlar las plazas» | sin disparador | «Controlar» no dice cuándo ni qué pasa. RF-3: «SI un curso no tiene plazas libres, ENTONCES el sistema deberá rechazar la inscripción…». |

## Tarjeta 6: visitas en recepción

- **La petición:** «Un registro de visitas para recepción, que ahora es un cuaderno.»
- **El problema real:** el cuaderno no avisa a la persona visitada y no dice quién está en el edificio; son dos problemas, y la P1 resuelve primero el aviso.
- **Lo delicado:** una visita deja datos personales. RF-1 limita lo que se pide, RF-3 pone un tope a cuánto se guarda (la cifra la decide quien manda: A1) y A2 pregunta si hace falta algo más.

**La hoja resuelta**
```text
HOJA DE TRABAJO · Dinámica SDD de 20 minutos  Grupo: ___  Tarjeta: 6
======================================================================
LA PETICIÓN (copia la frase entre comillas de la tarjeta)
«Un registro de visitas para recepción, que ahora es un cuaderno.»

1. HISTORIAS (0-5 min) · Como [quién], quiero [qué], para [por qué]
P1 (imprescindible): Como persona de recepción, quiero registrar la
                     llegada de una visita y que se avise a quien la
                     espera, para que nadie espere sin que lo sepan.
P2: Como persona de recepción, quiero registrar la salida de cada
    visita, para que la lista de quién está dentro sea cierta.
P3: Como persona de seguridad, quiero ver quién hay ahora en el
    edificio, para saber a quién localizar si hace falta.

2. REQUISITOS EARS (5-10 min) · sujeto: el sistema · verbo: «deberá»
   Plantillas: «El sistema deberá…» · «CUANDO…, el sistema deberá…» ·
   «SI…, ENTONCES el sistema deberá…» ·
   «MIENTRAS…, el sistema deberá…» · «DONDE…, el sistema deberá…»
RF-1 El sistema deberá registrar de cada visita solo su nombre, la
     persona visitada y la hora de llegada.
RF-2 CUANDO recepción registra la llegada de una visita, el sistema
     deberá avisar a la persona visitada con el nombre de la visita.
RF-3 SI el registro de una visita lleva guardado más de
     [NECESITA ACLARACIÓN: ¿cuánto tiempo?], ENTONCES el sistema
     deberá borrarlo.
RF-4 MIENTRAS una visita no tenga registrada su salida, el sistema
     deberá mostrarla como «dentro del edificio».
RF-5 DONDE la persona tenga permisos de seguridad, el sistema deberá
     permitir ver la lista de visitas que están dentro del edificio.

3. PREGUNTAS DE ACLARACIÓN (10-13 min) · para quien lo pide, antes
   de construir nada · afecta a: historia, requisito o alcance
A1: ¿Cuánto tiempo se guardan los datos de la visita? → afecta a: RF-3
A2: ¿Se pide también el documento de identidad?       → afecta a: RF-1
A3: ¿Por qué medio se avisa a la persona visitada?    → afecta a: RF-2

4. VAGUEDADES CAZADAS (13-18 min) · las vuestras y las de otros grupos
   Tipos: adjetivo sin cifra · dos cosas en una · sin disparador ·
   tecnología · el sujeto es la persona, no el sistema
Grupo ___: «______________________________» → tipo: __________________
Grupo ___: «______________________________» → tipo: __________________

FUERA DE ALCANCE (lo que decidís NO hacer en la primera versión):
citas previas; escanear documentos; control de acceso al edificio.
```

**Vaguedades que suelen aparecer**

| Frase vaga típica | Tipo | Cómo queda bien |
|---|---|---|
| «El sistema deberá avisar a la persona visitada» | sin disparador | Falta el cuándo: RF-2, «CUANDO recepción registra la llegada de una visita…». Por qué medio se avisa es otra pregunta (A3). |
| «Recepción deberá apuntar los datos de la visita» | el sujeto es la persona | Lo que hace el sistema: RF-1, «El sistema deberá registrar de cada visita solo su nombre, la persona visitada y la hora de llegada». Si hace falta algo más, se pregunta (A2). |
| «Los datos se guardarán el tiempo necesario» | adjetivo sin cifra | «Necesario» no se puede comprobar. RF-3 lleva la cifra que dé quien decide; mientras tanto queda `[NECESITA ACLARACIÓN: ¿cuánto tiempo?]` (A1). |

## Qué tienen en común las seis hojas

- **La P1 vale sola.** Si solo se construyera la P1 (aunque al principio alguien cargara a mano las plazas, las respuestas o los cursos), el problema de la tarjeta ya mejoraría de verdad.
- **Quien pide no es quien usa.** Ana, Jorge y Marta piden, pero las historias se escriben desde quien usa el sistema: quien viene en coche, quien tiene una duda, quien apunta el estado de su proyecto, recepción.
- **Las preguntas tienen efecto.** Cada A dice a qué historia o requisito afecta y se responde con un dato o con un sí o un no; ninguna es «¿qué queréis exactamente?».
- **Lo que no se hace, por escrito.** Cada hoja deja al menos dos cosas fuera de alcance, y lo que nadie sabía queda como pregunta o como `[NECESITA ACLARACIÓN: …]`, no como una cifra inventada.
- **Las mismas cinco plantillas.** Cada hoja usa las cinco plantillas EARS, una vez cada una: de una tarjeta a otra cambia el tema, no la forma.

## En tres frases

1. En veinte minutos y sin ordenador, una petición vaga se convierte en una página con tres historias (la primera, imprescindible), cinco requisitos EARS, tres preguntas con efecto y lo que se deja fuera.
2. Las mismas cinco plantillas valen para parking, nóminas, proyectos, material, cursos y visitas; lo que cambia es el dato que falta, y ese dato se pregunta o queda como `[NECESITA ACLARACIÓN: …]`, no se inventa.
3. Donde hay datos de personas (nóminas y visitas), la hoja decide antes de construir qué no se muestra, qué se guarda y durante cuánto tiempo, o lo deja preguntado.

## Siguiente paso

Vuelve al [ejercicio 04](../04-dinamica-de-equipo-20-minutos.md) y apunta en qué se parece y en qué se aleja tu hoja de la de tu tarjeta. Después sigue con el [ejercicio 05: arreglar una especificación mala](../05-arreglar-una-especificacion-mala.md), donde harás la misma caza de vaguedades sobre una especificación completa de ReservaSalas.

---

⬅️ [Ejercicio 04](../04-dinamica-de-equipo-20-minutos.md) · 🏠 [Índice de soluciones](README.md)
