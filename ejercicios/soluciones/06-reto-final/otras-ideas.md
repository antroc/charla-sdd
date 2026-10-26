# Ejercicio 06: esqueletos de partida para seis ideas

> **Para quién:** cualquier persona que haya empezado el ejercicio 06 y quiera un punto de partida · **Tiempo de lectura:** ~20 min · **Nivel:** 🟡 intermedio

El [ejercicio 06](../../06-reto-final-tu-propio-proyecto.md#ocho-ideas-de-proyecto) propone ocho ideas de proyecto y no resuelve ninguna. Dos ya tienen solución: el préstamo de portátiles (idea 1) se resuelve entero en [su propia carpeta](prestamo-de-portatiles/README.md) y las vacaciones (idea 4) son la [especificación del ejercicio 01](../01-solicitud-de-vacaciones/especificacion.md).

Aquí están las otras seis, cada una con el esqueleto de una especificación de SDD (*Spec-Driven Development*, desarrollo guiado por especificaciones): la petición tal como la diría quien la pide, el recorte que hace que la primera versión valga sola, las historias, un principio de constitución, cinco requisitos, las preguntas que hay que hacer y lo que se queda fuera.

> [!NOTE]
> Son esqueletos, no el proyecto entero: cada uno trae cinco de los entre 6 y 12 requisitos que pide el ejercicio, tres de las aclaraciones que saldrán al preguntar y un solo principio de constitución. Faltan a propósito los casos límite, los criterios de éxito con cifra, el plan y las tareas: son lo que escribes tú. Sirven para compararte, no para copiarlos: haz primero tu petición, tus historias y tus requisitos y mira después en qué te has desviado. Si tu P1 (la historia de prioridad 1) es distinta de la de aquí y vale sola, es igual de buena.

**Qué vas a encontrar**

- [Las ocho ideas y dónde está cada solución](#las-ocho-ideas-y-dónde-está-cada-solución)
- [Cómo leer cada esqueleto](#cómo-leer-cada-esqueleto)
- [Buzón de sugerencias con votos (idea 2)](#buzón-de-sugerencias-con-votos)
- [Días en la oficina (idea 3)](#días-en-la-oficina)
- [Incidencias de oficina (idea 5)](#incidencias-de-oficina)
- [Inscripción a cursos internos (idea 6)](#inscripción-a-cursos-internos)
- [Turnos de guardia del equipo de soporte (idea 7)](#turnos-de-guardia-del-equipo-de-soporte)
- [Horas por proyecto con cierre mensual (idea 8)](#horas-por-proyecto-con-cierre-mensual)
- [En tres frases](#en-tres-frases)
- [Siguiente paso](#siguiente-paso)

## Las ocho ideas y dónde está cada solución

La tabla repite las ocho ideas del ejercicio, con su nivel, y dice dónde está la solución de cada una.

| # | Idea | Nivel | Su solución |
|---|---|---|---|
| 1 | Préstamo de portátiles y proyectores | 🟢 | [Ejemplo completo](prestamo-de-portatiles/README.md) |
| 2 | Buzón de sugerencias con votos | 🟢 | [Esqueleto, más abajo](#buzón-de-sugerencias-con-votos) |
| 3 | Días en la oficina | 🟢 | [Esqueleto, más abajo](#días-en-la-oficina) |
| 4 | Solicitud de vacaciones | 🟡 | [Especificación completa](../01-solicitud-de-vacaciones/especificacion.md) |
| 5 | Incidencias de oficina | 🟡 | [Esqueleto, más abajo](#incidencias-de-oficina) |
| 6 | Inscripción a cursos internos | 🟡 | [Esqueleto, más abajo](#inscripción-a-cursos-internos) |
| 7 | Turnos de guardia del equipo de soporte | 🔴 | [Esqueleto, más abajo](#turnos-de-guardia-del-equipo-de-soporte) |
| 8 | Horas por proyecto con cierre mensual | 🔴 | [Esqueleto, más abajo](#horas-por-proyecto-con-cierre-mensual) |

Para ver cómo se recorta una petición sin estropearte la tuya, empieza por el recorte de una idea que no vayas a hacer: es lo que más cuesta y lo que más se aprende viéndolo hecho.

## Cómo leer cada esqueleto

Todas las ideas siguen el mismo orden, para que puedas saltar a la pieza que te interese:

1. **La petición**: lo que diría quien la pide, en dos o tres frases vagas, como las [tarjetas del ejercicio 04](../../04-dinamica-de-equipo-20-minutos.md#tarjetas-de-peticiones-vagas).
2. **El recorte**: qué entra en la P1 (la historia de prioridad 1, la que por sí sola ya resuelve algo), por qué vale sola y qué pasa a la P2, a la P3 o a «Fuera de alcance».
3. **Las tres historias**, con la forma «Como [quién], quiero [qué], para [por qué]».
4. **El principio propio**: el de la constitución que sale de este problema y no de cualquier otro. Los demás (sencillez primero, datos mínimos, pruebas antes de dar algo por hecho) son los de la plantilla del [paso 3 del ejercicio](../../06-reto-final-tu-propio-proyecto.md#pasos) y no se repiten.
5. **Cinco requisitos en EARS** (*Easy Approach to Requirements Syntax*, una forma sencilla y estructurada de redactar requisitos): sujeto «el sistema», verbo «deberá», una sola cosa comprobable y ninguna tecnología. La tabla dice qué [patrón](../../../docs/05-escribir-requisitos-claros-ears.md#los-cinco-patrones-y-el-sexto) usa cada uno.
6. **Tres aclaraciones** para quien decide, como las que haría `/speckit.clarify` (que pregunta hasta cinco veces, de una en una), cada una con lo que cambia en la especificación según la respuesta.
7. **Fuera de alcance**, con la razón de cada cosa.
8. **El error típico**: la trampa más probable de esa idea.

Tres convenciones:

- Los requisitos van numerados desde RF-001 (requisito funcional) dentro de cada idea, porque cada una es una especificación aparte.
- Cuando un requisito necesita una cifra que nadie ha dado, lleva el marcador `[NECESITA ACLARACIÓN: …]` en lugar de un número inventado. Si necesitas una cifra provisional para seguir, escríbela a la vista como supuesto y no des la especificación por aprobada hasta que quien encarga la confirme.
- Ana, Marta y Jorge son los personajes ficticios de todo el repositorio.

## Buzón de sugerencias con votos

**Idea 2** · Nivel 🟢 básico

### La petición

> «Queremos un buzón de sugerencias para la oficina: que cualquiera proponga una mejora, que los demás puedan votarla y que Oficina conteste algo. Ahora las ideas llegan por el pasillo y por correo, y se pierden.»
>
> Lo pide: Ana, responsable de Oficina.

### El recorte

La petición junta tres cosas: proponer, votar y que Oficina conteste. Con las dos primeras ya se acaba lo de las ideas perdidas, porque Oficina abre una lista y ve qué quiere más gente; mientras llega la respuesta dentro de la aplicación, puede contestar a su manera. Esa es la P1.

Contestar en la aplicación es la P2 y ver lo ya respondido, la P3. Comentarios, categorías y avisos se quedan fuera. Dos entidades (la sugerencia y el voto) y una regla (un voto por persona y sugerencia) caben en los uno o dos días que pide el ejercicio.

### Las tres historias

- **P1**: Como empleado, quiero proponer una mejora para la oficina y votar las de mis compañeros, para que Oficina vea qué interesa a más gente.
- **P2**: Como responsable de Oficina, quiero responder a cada sugerencia con un texto, para que quien la propuso y quien la votó sepan qué se va a hacer.
- **P3**: Como empleado, quiero ver las sugerencias que ya tienen respuesta, para no proponer lo que ya se decidió.

### El principio propio

**Se vota en secreto.** El sistema enseña cuántos votos tiene cada sugerencia, nunca quién los ha dado: nadie, tampoco Oficina, puede ver quién ha votado cada una. **Por qué:** si el voto lleva nombre, la gente vota lo que conviene y no lo que piensa, y el buzón deja de medir lo que interesa.

### Cinco requisitos en EARS

| N.º | Patrón | Requisito |
|---|---|---|
| RF-001 | Ubicuo | El sistema deberá mostrar las sugerencias ordenadas de más a menos votos, cada una con su número de votos. |
| RF-002 | CUANDO | CUANDO una persona vota una sugerencia, el sistema deberá sumar un voto al total de esa sugerencia. |
| RF-003 | SI…, ENTONCES | SI una persona intenta votar una sugerencia que ya ha votado, ENTONCES el sistema deberá rechazar el voto e indicar que ya votó. |
| RF-004 | MIENTRAS | MIENTRAS una sugerencia no tenga respuesta de Oficina, el sistema deberá mostrarla en la lista de pendientes de Oficina. |
| RF-005 | DONDE | DONDE la persona tenga rol de Oficina, el sistema deberá permitir responder a una sugerencia con un texto visible para todos. |

Te faltan, entre otros, el requisito de proponer una sugerencia y el de qué ve cada persona de las suyas.

### Tres aclaraciones para quien decide

1. **¿Se muestra quién propone cada sugerencia?**
   - Sí: la sugerencia lleva autor y hace falta un requisito que lo muestre y otro para que la persona pueda retirar la suya.
   - No: la sugerencia queda sin autor, nadie puede retirar una sugerencia y Oficina solo puede responder en público; se anota como supuesto.
2. **¿Se puede votar en contra o solo a favor?**
   - Solo a favor: el voto no lleva signo y RF-001 ordena contando votos, sin más.
   - También en contra: el voto lleva signo, hay que decidir cómo se ordena (¿por saldo?) y si se puede cambiar de opinión, y cambian RF-001 y RF-003.
3. **¿Hay que contestar a todas las sugerencias o solo a las más votadas?**
   - A todas: aparece un requisito nuevo que avisa a Oficina cuando una sugerencia lleva más de `[NECESITA ACLARACIÓN: ¿cuántos días?]` días sin respuesta, y un criterio de éxito con ese plazo.
   - Solo a las más votadas: hace falta un umbral (`[NECESITA ACLARACIÓN: ¿cuántos votos?]`) y cambia RF-004: solo las que lo superen entran en la lista de pendientes.

### Fuera de alcance

- Comentarios y debates dentro de cada sugerencia: convertirían el buzón en un foro y traerían reglas de moderación que nadie ha pedido.
- Retirar o cambiar un voto: en la primera versión el voto es definitivo; si Ana lo echa en falta, es una especificación nueva.
- Categorías y avisos de novedades: con una lista ordenada por votos, la P1 ya sirve.

### El error típico

Dejar que el buzón crezca hasta ser un foro (comentarios, categorías, moderación) antes de que funcione un solo voto, con lo que la P1 deja de caber en dos días y la lista votada que Oficina necesitaba no llega.

## Días en la oficina

**Idea 3** · Nivel 🟢 básico

### La petición

> «Necesito saber qué días viene cada persona a la oficina, que su equipo lo vea y que no coincidamos más de los que caben en cada planta. Ahora cada equipo se organiza como puede y hay días en que no hay sitio.»
>
> Lo pide: Ana, responsable de Oficina.

### El recorte

La petición pide tres cosas: marcar días, que el equipo los vea y respetar el aforo. La P1 se queda con lo que acaba con lo de «hoy no hay sitio»: marcar los días que voy, con el aforo de mi planta como límite.

Ver al equipo es la P2 y que Oficina vea la ocupación, la P3. Fuera quedan los puestos concretos, las listas de espera y cualquier control de quién ha venido de verdad. Una entidad (el día marcado) y una regla (el aforo) caben en los uno o dos días del ejercicio.

### Las tres historias

- **P1**: Como empleado, quiero marcar los días que voy a ir a la oficina y quitarlos si cambio de planes, para que no coincidamos más personas de las que caben en mi planta.
- **P2**: Como empleado, quiero ver qué días viene cada persona de mi equipo, para coincidir con quien trabajo.
- **P3**: Como responsable de Oficina, quiero ver cuánta gente viene cada día a cada planta, para anticiparme cuando se acerque al aforo.

### El principio propio

**No se controla la asistencia.** El sistema guarda los días que cada persona dice que vendrá, nunca si ha venido: ni registros de entrada y salida ni informes sobre personas concretas. **Por qué:** si sirve para saber quién fue de verdad, la gente dejará de marcar con sinceridad y el aforo dejará de servir.

### Cinco requisitos en EARS

| N.º | Patrón | Requisito |
|---|---|---|
| RF-001 | Ubicuo | El sistema deberá mostrar a cada persona qué días viene cada miembro de su equipo. |
| RF-002 | CUANDO | CUANDO una persona marca un día, el sistema deberá contarlo entre las personas que vienen ese día a su planta. |
| RF-003 | SI…, ENTONCES | SI el aforo de la planta de una persona está completo el día que quiere marcar, ENTONCES el sistema deberá rechazar la marca e indicar que ese día no quedan sitios. |
| RF-004 | MIENTRAS | MIENTRAS el aforo de una planta esté completo un día, el sistema deberá indicar que ese día está completo a quien consulte esa planta. |
| RF-005 | DONDE | DONDE la persona tenga rol de Oficina, el sistema deberá mostrar cuántas personas vienen cada día a cada planta. |

Te faltan, entre otros, el requisito de quitar un día marcado y el de qué planta cuenta para cada persona (depende de la aclaración 1).

### Tres aclaraciones para quien decide

1. **¿La planta es fija para cada persona o se elige al marcar cada día?**
   - Fija: Oficina asigna una planta a cada persona (dato nuevo) y RF-002 y RF-003 usan esa; aparece un caso límite nuevo: alguien cambia de planta con días ya marcados.
   - Se elige: cada día marcado lleva su planta y RF-003 se evalúa sobre la elegida; el aforo se cuenta por día marcado, no por persona.
2. **Si una planta se completa, ¿la persona se queda sin día o entra en una lista de espera?**
   - Se queda sin día: RF-003 no cambia y la lista de espera pasa a «Fuera de alcance».
   - Lista de espera: aparecen una entidad y un requisito nuevos (cuando alguien quita su día, avisar a la primera persona que espera) y una historia propia, y la P1 deja de caber en dos días.
3. **¿Hasta cuándo se puede quitar un día marcado?**
   - Hasta el mismo día: el sitio siempre se puede liberar y no hace falta ningún requisito más.
   - Con un límite (`[NECESITA ACLARACIÓN: ¿cuántos días antes?]`): hace falta un requisito que rechace quitar un día fuera de plazo y un caso límite («hoy por la mañana»).

### Fuera de alcance

- Reservar una mesa o un puesto concreto: la petición habla de días y de plantas, no de sitios; reservar puestos es otra especificación, como ReservaSalas.
- Controlar quién ha venido de verdad: lo prohíbe el principio de arriba.
- Lista de espera para una planta completa: depende de la aclaración 2 y, si Ana la quiere, es la versión 2.

### El error típico

Confundir marcar un día con reservar un puesto: en cuanto aparecen mesas, mapas de la planta y asignaciones, la P1 deja de caber en dos días y se parece más a otra aplicación que a la que pidió Ana.

## Incidencias de oficina

**Idea 5** · Nivel 🟡 intermedio

### La petición

> «Cuando algo no funciona en la oficina, como la impresora de la 2.ª, la gente avisa por correo o por el pasillo y luego nadie sabe si se ha arreglado. Quiero que se avise en un solo sitio, que Oficina lo coja y que quien avisó se entere cuando esté.»
>
> Lo pide: Ana, responsable de Oficina.

### El recorte

La petición describe un flujo entero: se reporta, Oficina asigna, Oficina cierra y quien reportó se entera. La P1 se queda con lo que cierra el círculo: reportar, que Oficina cierre y que quien reportó reciba el aviso. Con dos estados, abierta y cerrada, ya no hay incidencias de las que nadie sabe nada.

Asignar a una persona concreta es la P2 y ver el estado de lo que he reportado, la P3. Prioridades, categorías y plazos se quedan fuera.

### Las tres historias

- **P1**: Como empleado, quiero reportar que algo no funciona y recibir un aviso cuando Oficina lo cierre, para no tener que preguntar si ya lo han visto.
- **P2**: Como responsable de Oficina, quiero asignar cada incidencia a una persona, para que ninguna se quede sin alguien al cargo.
- **P3**: Como empleado, quiero ver el estado de las incidencias que he reportado, para saber si alguien las ha cogido.

### El principio propio

**Ninguna incidencia se cierra en silencio.** Una persona de Oficina no puede cerrar una incidencia sin escribir qué se ha hecho, y quien la reportó recibe esa nota con el aviso del cierre. **Por qué:** el problema de hoy no es solo que las cosas tarden en arreglarse, sino que nadie se entera; un cierre sin explicación vuelve a dejar a la gente sin saber.

### Cinco requisitos en EARS

| N.º | Patrón | Requisito |
|---|---|---|
| RF-001 | Ubicuo | El sistema deberá permitir a cualquier persona reportar una incidencia con la descripción de lo que no funciona. |
| RF-002 | MIENTRAS | MIENTRAS una incidencia reportada no esté cerrada, el sistema deberá mostrarla en la lista de pendientes de Oficina. |
| RF-003 | DONDE | DONDE la persona tenga rol de Oficina, el sistema deberá permitir cerrar una incidencia. |
| RF-004 | SI…, ENTONCES | SI una persona de Oficina intenta cerrar una incidencia sin escribir qué se ha hecho, ENTONCES el sistema deberá impedir el cierre y pedir la nota. |
| RF-005 | CUANDO | CUANDO una persona de Oficina cierra una incidencia, el sistema deberá avisar a quien la reportó con la nota de cierre. |

Te faltan, entre otros, el requisito de mostrar a cada persona sus incidencias con su estado (la P3) y el de asignar una incidencia a una persona (la P2).

### Tres aclaraciones para quien decide

1. **¿Quién puede cerrar una incidencia: solo Oficina, o también quien la reportó cuando ya está arreglada?**
   - Solo Oficina: RF-003 y RF-004 se quedan como están.
   - También quien la reportó: hace falta un requisito para que confirme el arreglo, un estado nuevo («pendiente de confirmar») y un caso límite para cuando no contesta.
2. **¿Se puede reabrir una incidencia cerrada?**
   - No: aparece un requisito MIENTRAS (una incidencia cerrada no admite cambios) y quien vuelva a tener el problema reporta una nueva.
   - Sí: hace falta un evento nuevo (al reabrir, avisar a Oficina) y cada cierre lleva su propia nota, porque el principio de no cerrar en silencio se aplica a todos.
3. **¿Pueden dos personas reportar la misma avería, y hay que juntarlas?**
   - No se juntan: cada incidencia se cierra y se avisa por separado; se anota como supuesto y las duplicadas pasan a «Fuera de alcance».
   - Se juntan: una incidencia pasa a tener varias personas que la reportaron, RF-005 avisa a todas y la P1 crece, así que juntar pasa a la P2.

### Fuera de alcance

- Prioridades, categorías y plazos de resolución: nadie las ha pedido y cada una trae reglas nuevas.
- Estados intermedios (en curso, esperando una pieza): con abierta y cerrada la P1 ya funciona; los demás llegan con la P2.
- Incidencias de informática o de las instalaciones del edificio: la primera versión es solo para lo que atiende Oficina; ampliarlo sería una especificación nueva.

### El error típico

Diseñar un sistema completo de gestión de incidencias (prioridades, categorías, plazos, reaperturas) antes de que Oficina pueda cerrar la primera.

## Inscripción a cursos internos

**Idea 6** · Nivel 🟡 intermedio

### La petición

> «Quiero que la gente se apunte a los cursos internos sin pasar por mí: que cada curso tenga sus plazas y que, si se llena, haya una lista de espera. Y que yo vea quién va a cada uno.»
>
> Lo pide: Jorge, de RRHH.

### El recorte

La petición pide publicar cursos, apuntarse, una lista de espera y ver quién va. La P1 se queda con lo que acaba con el problema de hoy, los cursos con más inscritos que plazas: publicar un curso con sus plazas, que la gente se apunte hasta que se llene y que RRHH vea quién está dentro.

La lista de espera depende de las bajas, así que va detrás: la P2 es darse de baja y la P3, la lista de espera. Fuera quedan las notas, los certificados y los cursos de varias sesiones. Una regla (nunca más inscritos que plazas) y dos entidades (el curso y la inscripción) caben en los uno o dos días del ejercicio.

### Las tres historias

- **P1**: Como responsable de RRHH, quiero publicar un curso con sus plazas, que la gente se apunte hasta que se llene y ver quién se ha apuntado, para dejar de llevar las inscripciones en una hoja de cálculo.
- **P2**: Como empleado, quiero darme de baja de un curso, para dejar mi plaza a otra persona.
- **P3**: Como empleado, quiero apuntarme a la lista de espera de un curso lleno y recibir la plaza si alguien se da de baja, para no perder la oportunidad.

### El principio propio

**Nunca hay más inscritos que plazas.** El sistema no admite a una persona más, ni siquiera si lo pide RRHH; quien no cabe espera su turno. **Por qué:** hoy hay cursos con más inscritos que plazas, y si el límite admite excepciones el problema vuelve.

### Cinco requisitos en EARS

| N.º | Patrón | Requisito |
|---|---|---|
| RF-001 | Ubicuo | El sistema deberá mostrar cada curso con su fecha, su número de plazas y cuántas quedan libres. |
| RF-002 | CUANDO | CUANDO una persona se apunta a un curso con plazas libres, el sistema deberá inscribirla en el curso. |
| RF-003 | SI…, ENTONCES | SI una persona se apunta a un curso sin plazas libres, ENTONCES el sistema deberá rechazar la inscripción e indicar que el curso está completo. |
| RF-004 | MIENTRAS | MIENTRAS la inscripción de un curso esté cerrada, el sistema deberá impedir apuntarse a él. |
| RF-005 | DONDE | DONDE la persona tenga rol de RRHH, el sistema deberá mostrar quién está inscrito en cada curso. |

Te faltan, entre otros, el requisito de publicar un curso con sus plazas y el de cerrar la inscripción en su fecha.

### Tres aclaraciones para quien decide

1. **Cuando se libera una plaza y hay lista de espera, ¿pasa sola a la primera persona o se le ofrece y puede rechazarla?**
   - Pasa sola: aparece un requisito nuevo (cuando alguien se da de baja, inscribir a la primera persona de la lista y avisarla) y un caso límite: esa persona ya no puede ir.
   - Se ofrece: hace falta un estado nuevo («plaza ofrecida») con un plazo (`[NECESITA ACLARACIÓN: ¿cuánto tiempo tiene para aceptarla?]`) y un requisito que pase la oferta a la siguiente persona si no responde; la P3 deja de caber en dos días.
2. **¿Cuándo se cierra la inscripción: al empezar el curso o unos días antes?**
   - Al empezar: RF-004 se queda como está y la inscripción se cierra en la fecha de inicio.
   - Antes: se cierra con un margen (`[NECESITA ACLARACIÓN: ¿cuántos días antes del curso?]`), hace falta un requisito para esa fecha y un criterio de éxito que garantice que RRHH recibe la lista con ese margen.
3. **¿La lista de espera respeta el orden de llegada, o RRHH puede dar prioridad a alguien?**
   - Orden de llegada: la lista solo guarda el momento en que cada persona se apuntó.
   - Con prioridad de RRHH: aparece un requisito DONDE que permite mover a una persona en la lista, y hay que decidir si el resto ve el orden.

### Fuera de alcance

- Notas, certificados o valoración de los cursos: la petición habla de plazas, no de lo que se aprende, y guardarlos sería más datos de los que hacen falta.
- Cursos con varias sesiones: en la primera versión un curso es una sola fecha; cada edición se publica como un curso nuevo con sus plazas.
- Que el manager apruebe quién va a cada curso: nadie lo ha pedido y añadiría un rol y un estado.

### El error típico

Olvidar la última plaza: dos personas se apuntan a la vez, entran las dos y el curso se pasa de plazas, que es justo el problema de hoy, así que hay que escribirlo como caso límite y como prueba antes de planificar.

## Turnos de guardia del equipo de soporte

**Idea 7** · Nivel 🔴 avanzado

### La petición

> «Cada mes montamos a mano el calendario de guardias del equipo de soporte en una hoja de cálculo. Quiero que la rotación salga sola, que se puedan cambiar guardias entre compañeros, que cuenten los festivos y las vacaciones y que todo el mundo se entere cuando algo cambie.»
>
> Lo pide: Marta, manager del equipo de soporte.

### El recorte

La petición lo mezcla todo (rotación, intercambios, festivos, vacaciones y avisos) y esas reglas se cruzan entre sí: con todo dentro, la P1 no cabe en los uno o dos días del ejercicio. Se recorta por lo que menos reglas cruza.

La P1 es publicar el calendario de guardias del mes a partir de una rotación fija, y vale sola: con ella desaparece lo que hoy se hace a mano, cada mes, en una hoja de cálculo. La P2 es el intercambio con aprobación y la P3, el aviso de los cambios.

Como el equipo tiene dos niveles (el nivel 1 atiende primero y el nivel 2 recibe lo que el primero no resuelve), la rotación es una por nivel; la aclaración 1 lo confirma con quien decide.

### Las tres historias

- **P1**: Como responsable del equipo de soporte, quiero publicar el calendario de guardias del mes a partir de una rotación fija, para dejar de montarlo a mano cada mes.
- **P2**: Como persona del equipo, quiero intercambiar una guardia con aprobación del responsable, para cubrir un imprevisto sin rehacer el calendario.
- **P3**: Como persona del equipo, quiero que me avisen cuando cambie una guardia mía, para enterarme sin mirar el calendario a diario.

### El principio propio

Es el que propone el ejercicio en el paso 3: «nadie hace dos guardias seguidas; el sistema lo impide, no lo avisa». **Por qué:** una excepción con aviso acaba siendo la norma: cuando falta alguien, el aviso se ignora y carga con todo la persona de siempre. Si el plan técnico propone «permitir excepciones con un aviso», este principio lo frena y la alternativa queda anotada en `research.md` como descartada.

### Cinco requisitos en EARS

| N.º | Patrón | Requisito |
|---|---|---|
| RF-001 | CUANDO | CUANDO el responsable del equipo publica un mes, el sistema deberá asignar sus guardias siguiendo la rotación de cada nivel como continuación del mes anterior. |
| RF-002 | MIENTRAS | MIENTRAS el calendario de un mes esté publicado, el sistema deberá mostrarlo a todo el equipo con quién está de guardia en cada fecha. |
| RF-003 | SI…, ENTONCES | SI un intercambio dejaría a una de las dos personas con dos guardias seguidas, ENTONCES el sistema deberá rechazarlo e indicar qué guardias coinciden. |
| RF-004 | Ubicuo | El sistema deberá exigir la aprobación del responsable del equipo para aplicar un intercambio de guardias. |
| RF-005 | DONDE | DONDE la persona tenga rol de responsable del equipo, el sistema deberá permitir aprobar o rechazar un intercambio pendiente. |

Te faltan, entre otros, el requisito de proponer un intercambio y el del aviso de los cambios (la P3).

### Tres aclaraciones para quien decide

1. **¿Hay una sola rotación para todo el equipo o una por nivel?**
   - Una sola: la persona no tiene nivel, la rotación es una lista y el calendario muestra una guardia por fecha; el cambio de más abajo ya no tendría sentido.
   - Una por nivel: la persona lleva su nivel, hay una lista por nivel y el calendario muestra una guardia de cada nivel, como recoge RF-001. Hay que definir «nivel» en la especificación en lugar de dar por hecho que todo el mundo lo entiende.
2. **¿Qué cuenta como «dos guardias seguidas»: dos consecutivas, o también dos con un hueco corto entre medias?**
   - Consecutivas: RF-003 se queda como está.
   - Con hueco: RF-003 exige un descanso mínimo entre dos guardias de la misma persona (`[NECESITA ACLARACIÓN: ¿cuántas guardias de descanso?]`) y aparece un caso límite: un equipo con pocas personas, donde el principio no se puede cumplir y hay que decidir qué hace el sistema.
3. **¿Qué pasa con un intercambio que nadie aprueba?**
   - Queda pendiente sin límite: RF-004 no cambia y se anota como supuesto, con el riesgo de pendientes eternos.
   - Caduca: hace falta un requisito nuevo que descarte el intercambio sin respuesta y avise a las dos personas, y un plazo (`[NECESITA ACLARACIÓN: ¿cuántos días antes de la guardia?]`).

### Fuera de alcance

- Festivos: una guardia en festivo puede tener reglas propias (por ejemplo, rotar aparte) que cambian la rotación entera; con ellas dentro, la P1 deja de caber en dos días.
- Vacaciones: cruzar la rotación con las ausencias obliga a conocerlas, y eso es otra especificación, la de [vacaciones](../01-solicitud-de-vacaciones/especificacion.md); mientras tanto, quien se va de vacaciones cambia su guardia con el intercambio de la P2.
- Compensaciones por hacer guardia (descansos o pagos): son otra decisión y otro cálculo, y no cambian quién está de guardia.

### El cambio que llega después

Al ver funcionar la P1 y la P2, Marta pide un cambio: los intercambios entre personas del mismo nivel no necesitan aprobación. Se hace como en el [paso 10 del ejercicio](../../06-reto-final-tu-propio-proyecto.md#pasos): Marta lo decide y lo pide; quien construye lo escribe en `spec.md` (y en `plan.md`, si recogía el dato); Marta lee el texto nuevo y lo aprueba.

Después, `/speckit.converge` añade a `tasks.md` las tareas que faltan y `/speckit.implement solo la fase de convergencia` las ejecuta (no se relanza `/speckit.tasks`, que rehace la lista entera). Este es el requisito antes y después:

```markdown
Antes:
- **RF-004**: El sistema deberá exigir la aprobación del responsable del equipo para aplicar un intercambio de guardias.

Después:
- **RF-004**: El sistema deberá exigir la aprobación del responsable del equipo para aplicar un intercambio entre personas de niveles distintos.
- **RF-006** (nuevo): CUANDO dos personas del mismo nivel acuerdan intercambiar una guardia, el sistema deberá aplicar el intercambio sin pedir aprobación.
```

RF-004 conserva su número y lo nuevo toma el siguiente libre. RF-003 no cambia y sigue mandando: un intercambio entre iguales que dejase a alguien con dos guardias seguidas también se rechaza, porque lo exige el principio.

Anota la decisión en las aclaraciones y haz *commit* de `spec.md` (guarda esa versión) antes de regenerar, para que el historial muestre que el cambio empezó por la especificación. Y dos cuidados que el ejemplo del ejercicio ya aprendió: define «nivel» y usa siempre la misma palabra, «guardia», no «turno».

### El error típico

Empezar por los festivos y las vacaciones, que cruzan todas las demás reglas, y acabar con una especificación que nadie termina de aprobar y ningún calendario publicado.

## Horas por proyecto con cierre mensual

**Idea 8** · Nivel 🔴 avanzado

### La petición

> «Cada persona de mi equipo apunta sus horas por proyecto en una hoja de cálculo y a final de mes tengo que perseguirlas una a una. Quiero que cada uno meta sus horas, que yo pueda darlas por buenas y que luego el mes quede cerrado.»
>
> Lo pide: Marta, manager.

### El recorte

La petición encadena tres pasos, imputar (apuntar las horas a un proyecto), validar y cerrar, cada uno con su rol y su estado. La P1 es solo imputar: cada persona apunta sus horas por proyecto y día y ve su total del mes, que ya sustituye a la hoja de cálculo.

Validar es la P2 y cerrar el mes, la P3. Informes, exportaciones y cualquier dato que no sea persona, proyecto, día y horas se quedan fuera. Dos entidades (el proyecto y la imputación) y una regla (el máximo por día) caben en los uno o dos días del ejercicio.

### Las tres historias

- **P1**: Como persona del equipo, quiero imputar mis horas a cada proyecto cada día y ver mi total del mes, para dejar de rellenar la hoja de cálculo.
- **P2**: Como manager, quiero validar las horas de mi equipo de un mes, para darlas por buenas sin perseguir a cada persona.
- **P3**: Como manager, quiero cerrar el mes, para que las horas ya no se puedan tocar.

### El principio propio

**Un mes cerrado no se modifica.** Después del cierre no se añade, no se cambia y no se borra ninguna hora de ese mes; lo que haya que corregir se corrige en el mes abierto, con el motivo escrito. **Por qué:** un cierre al que se puede volver deja de ser cierre: las cifras que otras personas ya han usado cambian sin que nadie se entere.

Además, el principio de datos mínimos de la plantilla pide aquí una lista cerrada de lo que se guarda: persona, proyecto, día y horas, y en cada ajuste el motivo y el mes que corrige. Nada más.

### Cinco requisitos en EARS

| N.º | Patrón | Requisito |
|---|---|---|
| RF-001 | Ubicuo | El sistema deberá mostrar a cada persona sus horas del mes por proyecto, con el total de cada proyecto. |
| RF-002 | CUANDO | CUANDO una persona imputa horas a un proyecto en un día, el sistema deberá sumarlas a su total de ese proyecto en el mes. |
| RF-003 | SI…, ENTONCES | SI una persona imputa en un mismo día más de `[NECESITA ACLARACIÓN: ¿cuántas horas como máximo por persona y día?]` horas en total, ENTONCES el sistema deberá rechazar la imputación e indicar el máximo. |
| RF-004 | MIENTRAS | MIENTRAS un mes esté cerrado, el sistema deberá impedir cualquier cambio en las horas de ese mes. |
| RF-005 | DONDE | DONDE la persona tenga rol de manager, el sistema deberá permitir validar las horas de su equipo en un mes. |

Te faltan, entre otros, el requisito de cerrar el mes (la P3) y el de qué ve el manager de las horas de su equipo antes de validarlas.

### Tres aclaraciones para quien decide

1. **¿Quién cierra el mes: cada manager el de su equipo o una persona de administración para toda la empresa?**
   - Cada manager: el cierre llega en fechas distintas y la P3 usa el mismo rol que la P2 (DONDE rol de manager).
   - Administración: aparece un rol nuevo, el cierre es uno para todos y hace falta una fecha (`[NECESITA ACLARACIÓN: ¿qué día del mes siguiente se cierra?]`); RF-004 se aplica a todos a la vez y la P3 la protagoniza ese rol, no el manager.
2. **¿Qué pasa si alguien descubre un error en un mes ya cerrado?**
   - Se corrige en el mes abierto, con un ajuste y su motivo: el principio se queda como está y hace falta un requisito para imputar un ajuste indicando qué mes corrige.
   - Se reabre el mes: el principio cambia, y cambiarlo se hace con la gobernanza de la constitución (por escrito, aprobado por quien encarga y con versión mayor, porque se redefine un principio); además aparece un estado nuevo, «reabierto», y un requisito sobre quién puede reabrir.
3. **¿Se pueden imputar horas a cualquier proyecto o solo a los que tiene asignados cada persona?**
   - A cualquiera: hay una lista común de proyectos y no hace falta nada más.
   - Solo a los suyos: aparece una relación entre personas y proyectos, alguien que la mantenga (un requisito DONDE) y un requisito que rechace imputar a un proyecto ajeno; la P1 crece.

### Fuera de alcance

- Facturación, coste por hora y nómina: lo que se haga con las horas cerradas es otra aplicación.
- Registro de entrada y salida de la jornada: es otro problema, con otras reglas, y la petición habla de horas por proyecto, no de horarios.
- Informes y exportaciones: los pedirá quien use las horas cerradas, cuando exista el cierre; hoy nadie los ha pedido.

### El error típico

Guardar datos de más «por si el informe los necesita» (qué se hizo en cada hora, a qué hora se empezó, desde dónde se imputa), con lo que la aplicación deja de repartir horas entre proyectos y pasa a vigilar a las personas.

## En tres frases

1. Cada esqueleto recorta una petición vaga hasta una P1 que vale sola, y lo recortado no desaparece: va a la P2, a la P3 o a «Fuera de alcance», con la razón escrita.
2. El principio propio sale del problema y prohíbe algo concreto (votar con nombre, controlar la asistencia, cerrar en silencio, pasarse de plazas, hacer dos guardias seguidas, tocar un mes cerrado); sin él, la constitución se parecería a la de cualquier otro proyecto.
3. Las aclaraciones no se contestan solas: cada respuesta cambia un requisito, un caso límite o el alcance, y por eso se preguntan a quien decide antes de planificar, no se resuelven sobre la marcha en el chat del asistente de IA.

## Siguiente paso

Vuelve al [ejercicio 06](../../06-reto-final-tu-propio-proyecto.md) y sigue con tu proyecto; cuando llegues al [paso 11](../../06-reto-final-tu-propio-proyecto.md#pasos), compara tu especificación con el esqueleto de tu idea y puntúate con la [rúbrica](../../06-reto-final-tu-propio-proyecto.md#rúbrica-de-autoevaluación). Si tu idea es la 1, el ejemplo completo está en el [préstamo de portátiles](prestamo-de-portatiles/README.md), y el [índice del reto final](README.md) explica cómo usar todos estos materiales sin estropearte el ejercicio.

---

⬅️ [Ejercicio 06](../../06-reto-final-tu-propio-proyecto.md) · 🏠 [Índice del reto final](README.md)
