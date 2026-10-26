# Solución del ejercicio 05: la especificación arreglada

> **Para quién:** cualquier persona que haya hecho el ejercicio 05 · **Tiempo de lectura:** ~15 min · **Nivel:** 🟡 intermedio

Esta es la revisión resuelta de la especificación (`spec.md`) que Luis escribió con prisas en el [ejercicio 05](../05-arreglar-una-especificacion-mala.md). Tiene dos partes: la lista numerada de problemas, cada uno con su línea, su tipo y su arreglo, y la versión corregida de lo que pide reescribir el ejercicio: los requisitos funcionales, en EARS (*Easy Approach to Requirements Syntax*, una forma sencilla y estructurada de redactar requisitos), y los criterios de éxito.

En SDD (*Spec-Driven Development*, desarrollo guiado por especificaciones) esta revisión se hace antes del plan técnico (`plan.md`), cuando arreglar una línea cuesta minutos. Todo lo que verás es coherente con la [especificación canónica de ReservaSalas](03-reserva-salas/spec.md) y con su [constitución](03-reserva-salas/constitution.md) (`constitution.md`).

> [!NOTE]
> Esto es un ejemplo resuelto, no la única respuesta correcta. Tu tabla puede agrupar los problemas de otra forma o darles otro tipo, y tus requisitos pueden usar otras palabras y otra numeración: si dicen lo mismo y pasan la lista de verificación (*checklist*), están bien.

**Qué vas a encontrar**

- [Cómo usar esta solución](#cómo-usar-esta-solución)
- [Los problemas principales](#los-problemas-principales)
- [Para nota](#para-nota)
- [La especificación corregida](#la-especificación-corregida)
  - [Requisitos funcionales (paso 3)](#requisitos-funcionales-paso-3)
  - [Criterios de éxito (paso 4)](#criterios-de-éxito-paso-4)
  - [El resto de la especificación](#el-resto-de-la-especificación)
- [La lista de verificación pasada](#la-lista-de-verificación-pasada)
- [En tres frases](#en-tres-frases)
- [Siguiente paso](#siguiente-paso)


## Mínimo esperado

No hace falta encontrar todos los defectos de esta auditoría. El ejercicio se considera conseguido con **12 problemas relevantes**: 2 de alcance, 2 de requisitos, 2 de criterios de éxito, 2 choques con la constitución y 4 adicionales que puedan cambiar lo construido. Corrige las secciones afectadas y explica por qué.

Lo que sigue es una **auditoría ampliada** para practicar una revisión mucho más fina.
## Cómo usar esta solución

- Los números de línea son los del bloque numerado del paso 1 del ejercicio.
- Hay 46 problemas: 39 principales, que se pueden encontrar con las pistas del paso 2, y 7 matices «para nota». Lo normal es encontrar entre 10 y 15 a la primera.
- Cuenta como acierto cualquier fila tuya que señale el mismo fallo, aunque lo hayas juntado con otro o le hayas puesto otro tipo: muchos problemas son de dos o tres tipos a la vez.
- Las respuestas que dio Ana en el paso 3 se dan por conocidas en toda la solución.

## Los problemas principales

Van en el orden del documento, agrupados por sección. Los tipos son los de la lista del paso 2; cuando hay varios, el primero es el que más pesa.

### Cabecera y resumen (líneas 01-11)

| N.º | Línea(s) | Qué falla | Tipo | Cómo se arregla |
|---|---|---|---|---|
| 1 | 03 | «Creada: el viernes»: no es una fecha; dentro de un mes nadie sabrá qué viernes era. | Laguna | Una fecha `AAAA-MM-DD` (en el canon, 2026-10-06). |
| 2 | 03 | «Estado: lista para implementar», con una pregunta sin resolver en las líneas 61-62 y sin haber pasado por aclarar ni por el plan técnico. Además, la constitución pide que Ana revise y apruebe la especificación. | Contradicción, contra la constitución | «Borrador» mientras quede algún marcador; «lista para planificar» cuando no quede ninguno y Ana la haya aprobado. |
| 3 | 09-10 | «Se hará con React en la parte visual, una API REST en Node.js y PostgreSQL, todo en la nube»: decide la tecnología en la especificación. Y «todo en la nube» choca con las restricciones de la constitución: un único servidor modesto, accesible solo desde la red de la empresa. | Tecnología, contra la constitución | Quitarlo. Si hay preferencias, van al plan técnico, justificadas contra la constitución. |
| 4 | 10-11 | «la hoja de cálculo, que da muchos problemas»: no dice cuáles, y son justo los que la aplicación tiene que resolver. | Vago, laguna | Nombrarlos: dos equipos en la misma sala, salas reservadas que se quedan vacías y reservas «fantasma» sin responsable. |
| 5 | 11 | «Más adelante servirá también para reservar parking y catering»: funciones que nadie ha pedido (el principio 1 prohíbe las funciones «por si acaso»), y choca con la línea 87, según la cual no queda nada fuera. | Alcance, contradicción | Llevarlo a «Fuera de alcance». |

### Historias de usuario y casos límite (líneas 13-37)

| N.º | Línea(s) | Qué falla | Tipo | Cómo se arregla |
|---|---|---|---|---|
| 6 | 15, 23 y 31 | Ninguna historia tiene prioridad (P1, P2, P3), «Por qué esta prioridad» ni «Prueba independiente». | Prioridad, laguna | «Reservar una sala» es la P1 y «Cancelar o modificar mi reserva», la P2. Falta la P3, «Ver mis reservas y las de hoy». |
| 7 | 15-18 | «Ver estadísticas de uso» va la primera y nadie la ha pedido: no resuelve choques, salas vacías ni reservas fantasma. | Prioridad, alcance, contra la constitución | Bajarla de prioridad o dejarla fuera de la primera versión (en el canon no existe). Va contra el principio 1 y, si las gráficas dejan ver quién usa cada sala, contra el 4: «no se hacen informes sobre personas concretas». |
| 8 | 20-21 | «se comprueba abriendo la pantalla de estadísticas y viendo que funciona bien»: no se puede contestar con un sí o un no. | Vago | Criterios Dado/Cuando/Entonces con datos concretos: sala, día, franja y resultado esperado. |
| 9 | 25-26 | «y de paso reservar también el proyector y pedir café»: mete otras dos funcionalidades en la historia principal. | Dos cosas en una, alcance | Sacarlas a «Fuera de alcance» (en el canon, «reserva de equipamiento»). Si algún día se quieren, tendrán su propia especificación. |
| 10 | 28-29 | «el usuario pulsa el botón verde grande de arriba a la derecha que pone “Reservar”»: describe la pantalla, no lo que hace el sistema. | Interfaz | «cuando confirma la reserva». Botones y colores se deciden en el diseño. |
| 11 | 29 | «la reserva se guarda correctamente»: ¿qué es «correctamente»? | Vago | Decir qué se ve: el sistema la guarda y muestra «Reserva confirmada: Mediterráneo, jueves 22 de octubre, de 10:00 a 11:00», con Marta como responsable. |
| 12 | 33 | «Como usuario quiero cancelar.»: no dice qué se cancela, quién puede hacerlo, qué pasa con la franja ni para qué; no tiene criterios, y falta «modificar». | Laguna | Historia «Cancelar o modificar mi reserva»: la franja vuelve a quedar libre, y solo pueden hacerlo la persona responsable o administración. |
| 13 | 37 | «Ninguno destacable. Si aparece alguno, ya lo veremos al programar.»: no hay casos límite, y la constitución dice que las dudas se resuelven por escrito antes de planificar. | Laguna, contra la constitución | Escribirlos: solapamiento parcial, fuera del horario 08:00-20:00, sala en mantenimiento, más de 4 horas, «para ya mismo» con la sala ocupada, más de 30 días de antelación, fin anterior al inicio y dos personas a la vez. |

### Requisitos funcionales (líneas 39-62)

| N.º | Línea(s) | Qué falla | Tipo | Cómo se arregla |
|---|---|---|---|---|
| 14 | 43 | RF-1, «rápido, intuitivo y fácil de usar»: adjetivos sin cifra; ni siquiera es un requisito funcional. | Vago | Convertirlo en criterios de éxito con cifra: CE-001, CE-003 y CE-004. |
| 15 | 44-45 | RF-2, «reservar salas y gestionar los usuarios (alta, baja y cambio de contraseña)»: dos cosas en una, y la constitución dice que se entra con el acceso corporativo existente y que la aplicación «no gestiona contraseñas propias». | Dos cosas en una, contra la constitución | La gestión de usuarios desaparece y el acceso corporativo se anota como supuesto. Reservar queda en RF-002 y RF-003. |
| 16 | 46 | Otro «RF-2» (y no hay RF-3): «Avisar si hay choque de reservas.» No tiene sujeto ni patrón EARS, y «avisar» no dice si la reserva se rechaza ni qué se le dice a la persona. | Duplicado, sin disparador o sin sujeto, vago | RF-005: «SI la franja solicitada se solapa con otra reserva de la misma sala, ENTONCES el sistema deberá rechazar la reserva e indicar qué franja está ocupada». |
| 17 | 47-48 | RF-4, «guardarla en la tabla `reservas` de PostgreSQL y enviar el correo por la API de un proveedor externo»: tecnología; dos cosas que pueden fallar por separado; y un proveedor externo, cuando la constitución solo permite usar dos sistemas que ya existen en la empresa: el acceso y el correo corporativos. | Tecnología, dos cosas en una, contra la constitución | Dos requisitos sin tecnología: RF-003 (guardar y mostrar la confirmación) y RF-011 (el correo). |
| 18 | 49-50 | RF-5, «El usuario deberá hacer las reservas dentro del horario de oficina»: el sujeto es la persona, no el sistema; es una norma, no un requisito. | Sin disparador o sin sujeto | Darle la vuelta: SI la franja queda fuera de 08:00-20:00, ENTONCES el sistema deberá rechazar la reserva e indicar qué límite se incumple (parte de RF-006). |
| 19 | 50 | «(o hasta las 22:00 si es un evento)»: «evento» no está definido en ningún sitio, y estira el horario que la misma frase acaba de fijar. | Contradicción, vago | Quitar la excepción: Ana fijó 08:00-20:00 sin excepciones. |
| 20 | 51 | RF-6, «podría enviar un correo de confirmación, si da tiempo a hacerlo»: «podría» no obliga a nada y «si da tiempo» es una condición del proyecto, no del sistema. Además repite el correo de RF-4. | Verbo blando, duplicado | RF-011, con «deberá»: Ana dijo que el correo es obligatorio. |
| 21 | 52-53 | RF-7, «Las reservas pueden ser anónimas»: el principio 5 dice «No existen reservas anónimas». Tampoco dice qué hace el sistema. | Contra la constitución, verbo blando | Su contrario, RF-004: «El sistema deberá mostrar, junto a cada reserva, el nombre de la persona responsable». |
| 22 | 54-55 | RF-8, «no pueden durar más de 4 horas, salvo las reuniones de todo el día, que se reservan sin problema»: se contradice en la misma frase, no tiene sujeto ni patrón, y «sin problema» no se puede comprobar. | Contradicción, sin disparador o sin sujeto | SI la franja dura más de 4 horas, ENTONCES el sistema deberá rechazar la reserva e indicar que el máximo son 4 horas (parte de RF-006; Ana: sin excepciones). |
| 23 | 56-57 | RF-9, «la disponibilidad de todos los espacios y las rooms»: tres nombres para lo mismo (espacios, rooms, salas), y no dice para qué fecha ni franja. | Terminología, sin disparador o sin sujeto | RF-002: «CUANDO una persona indica una fecha y una franja horaria, el sistema deberá mostrar qué salas están libres en esa franja». |
| 24 | 58-59 | RF-10, «guardar la reserva (ver también RF-4)»: repite RF-4, y la referencia cruzada lo confiesa. | Duplicado | Se funde con RF-4 en RF-003. |
| 25 | 60-62 | RF-11 lleva un `[NECESITA ACLARACIÓN: …]` sin resolver en un documento «lista para implementar», y con dos preguntas en un solo marcador, cuando lo normal es una por marcador. | Laguna, contradicción | Preguntar a Ana y aplicar sus respuestas: RF-009 (mantenimiento) y RF-010 (reservas ajenas). Y, como el mantenimiento es un estado que dura, RF-007 con MIENTRAS. |
| 26 | 43-62 | No hay ningún requisito para listar las salas, cancelar o modificar la propia reserva, los permisos, la antelación máxima de 30 días ni ver mis reservas y las de hoy. | Laguna | Añadirlos: RF-001, RF-008, RF-009, RF-010, el límite de 30 días de RF-006 y RF-012. |

### Entidades clave (líneas 64-69)

| N.º | Línea(s) | Qué falla | Tipo | Cómo se arregla |
|---|---|---|---|---|
| 27 | 66 | «Sala: nombre, planta, aforo.»: falta el estado (disponible o en mantenimiento), que RF-11 necesita. | Laguna | Añadir el estado. |
| 28 | 67 | «Reserva: sala, inicio, fin.»: falta la persona responsable, que exige el principio 5, y faltan el estado (activa o cancelada) y quién la canceló o la modificó, que también pide el principio 5. | Laguna, contra la constitución | Reserva: sala, persona responsable, inicio, fin, estado y quién la canceló o la modificó por última vez. |
| 29 | 68-69 | «Usuario: nombre, correo, teléfono móvil, foto, DNI, departamento, cargo y fecha de nacimiento (por si hace falta más adelante)»: el principio 4 prohíbe guardar teléfonos, fotos, cargos, departamentos o cualquier dato que no haga falta para reservar, y «por si hace falta» es justo lo que el principio 1 no permite. Y falta el único dato nuevo que sí hace falta: el rol. | Contra la constitución, laguna | Persona: nombre, correo corporativo y rol (empleado o administración). Sin rol no hay permisos. |

### Criterios de éxito (líneas 71-78)

| N.º | Línea(s) | Qué falla | Tipo | Cómo se arregla |
|---|---|---|---|---|
| 30 | 75 | CE-1, «La gente estará más contenta con las salas.»: ¿cuánto más?, ¿cómo se mide? | No medible | Medir algo que se note: CE-003, el 90 % completa una reserva sin ayuda la primera vez (o una encuesta con una cifra objetivo). |
| 31 | 76 | CE-2, «Habrá menos choques que ahora.»: sin cifra, y nadie sabe cuántos hay ahora. | No medible | CE-002: cero reservas solapadas. La idea era buena; le faltaba el número. |
| 32 | 77 | CE-3, «La consulta a la base de datos tardará menos de 50 milisegundos.»: tiene cifra, pero habla de tecnología y mide algo que la persona no ve. | Tecnología | CE-004: el listado de disponibilidad se muestra en menos de 2 segundos. Se mantiene la idea de medir un tiempo; cambian lo medido y la cifra. |
| 33 | 78 | CE-4, «La app será un éxito y todo el mundo la usará.» | No medible | Quitarlo o cambiarlo por una cifra de uso que fije Ana. El «que vaya rápido» de la petición ya lo cubre CE-001 (menos de 1 minuto). |

### Supuestos, fuera de alcance y notas (líneas 80-93)

| N.º | Línea(s) | Qué falla | Tipo | Cómo se arregla |
|---|---|---|---|---|
| 34 | 82 | «Todo el mundo usará Chrome en un portátil de la empresa.»: es una decisión técnica, y choca con el principio 2 porque exige un navegador y un dispositivo concretos para poder usar la aplicación. | Tecnología, contra la constitución | Quitarlo. El canon va en la dirección contraria: basta con que se pueda usar desde el móvil. |
| 35 | 83 | «las pasará alguien a mano la primera semana»: decide sin preguntar que hay que cargar las reservas de la hoja de cálculo, y sin responsable («alguien»). | Laguna, alcance | Preguntarlo a Ana. Si no se cargan, a «Fuera de alcance» (el canon no prevé cargarlas). |
| 36 | 87 | «De momento nada: lo haremos todo en la primera versión.»: alcance sin acotar; contradice la línea 11 y va contra el principio 1 (sencillez). | Alcance, contradicción, contra la constitución | Escribir qué queda fuera: reservas recurrentes, control de asistencia, integración con el calendario, equipamiento, catering y parking, y aplicación móvil nativa. |
| 37 | 91 | «el plan técnico se puede saltar»: la constitución pide comprobar el plan, punto por punto, contra ella antes de trocearlo en tareas. | Contra la constitución | Quitarlo. La tecnología se decide y se justifica en el plan. |
| 38 | 92 | «Se probará a mano al final; no hay tiempo para pruebas automáticas.»: el principio 3 dice que nada está terminado sin al menos una prueba automática, escrita antes que el código. | Contra la constitución | Quitarlo. |
| 39 | 93 | «Si Ana tiene dudas, que las pregunte cuando la app esté hecha.»: es al revés; Ana revisa y aprueba la especificación, y las dudas se resuelven al aclarar, antes de planificar. | Contra la constitución | Quitarlo y abrir la sección «Aclaraciones» con las respuestas de Ana. |

## Para nota

Matices que no hace falta encontrar para dar el ejercicio por bueno, pero que una revisión fina también señalaría. Siguen la numeración de la tabla.

40. **Línea 04, la petición original.** «que vaya rápido y sin líos» son palabras de Ana y se copian tal cual: no es un fallo de Luis. Lo que falla es que la especificación no las traduce a problemas concretos ni a cifras (filas 4 y 14).
41. **Línea 08, «una app web».** Una decisión técnica pequeña: basta con «una aplicación interna»; si es web o no lo decide el plan. Tipo: tecnología.
42. **Línea 18, «con exportación a Excel».** Un producto concreto. Si la historia se quedara, diría «descargar el listado»; como sale de la primera versión, se va con ella. Tipo: tecnología, interfaz.
43. **Líneas 17, 25, 28, 33, 47, 49, 68 y 75, cómo se llama a las personas.** «empleado», «usuario», «una persona», «la gente» y la entidad «Usuario» nombran a las mismas personas de cuatro formas, y «responsable de Oficina» es un rol que el documento no define. Se elige un término, «persona», y se llama «administración» al rol con permisos. Tipo: terminología.
44. **Líneas 43-62, la numeración.** «RF-1» en lugar de «RF-001», con un hueco (no hay RF-3) y un número repetido (dos RF-2). Se numera RF-001, RF-002… sin huecos ni repeticiones, y un número retirado no se reutiliza. Tipo: duplicado.
45. **Líneas 80-83, los supuestos que faltan.** Todas las personas tienen correo corporativo y entran con el acceso corporativo existente; hay un servidor de correo corporativo para los avisos; no hay integración con el calendario en la primera versión; y el volumen es pequeño, unas 200 personas. Tipo: laguna.
46. **Línea 89, «Notas de Luis».** Esa sección no existe en la [plantilla de especificación](../plantillas/especificacion.md), y en cambio falta «Aclaraciones», que es donde debían quedar las respuestas a las preguntas de la línea 61. Las notas se quitan y se añade «Aclaraciones» (más abajo tienes cómo queda). Tipo: laguna.

## La especificación corregida

Estas son las dos secciones que pide reescribir el ejercicio, con las respuestas de Ana del paso 3 ya aplicadas. Coinciden con la especificación canónica para que puedas comparar una a una; tu numeración y tu redacción pueden ser otras. Al final tienes qué pasa con el resto de secciones.

### Requisitos funcionales (paso 3)

Doce requisitos que cubren los diez puntos del paso 3. RF-012 (ver mis reservas y las de hoy) es opcional: no estaba entre esos diez puntos.

```markdown
### Requisitos funcionales

- **RF-001**: El sistema deberá mostrar la lista de salas con su planta y aforo.
- **RF-002**: CUANDO una persona indica una fecha y una franja horaria, el sistema deberá mostrar qué salas están libres en esa franja.
- **RF-003**: CUANDO una persona confirma una reserva, el sistema deberá guardarla y mostrar un mensaje de confirmación con sala, fecha y hora.
- **RF-004**: El sistema deberá mostrar, junto a cada reserva, el nombre de la persona responsable.
- **RF-005**: SI la franja solicitada se solapa con otra reserva de la misma sala, ENTONCES el sistema deberá rechazar la reserva e indicar qué franja está ocupada.
- **RF-006**: SI la franja solicitada queda fuera del horario de oficina (08:00-20:00), dura más de 4 horas, termina en el pasado o empieza más de 30 días después de hoy, ENTONCES el sistema deberá rechazar la reserva e indicar qué límite se incumple.
- **RF-007**: MIENTRAS una sala esté marcada en mantenimiento, el sistema deberá impedir nuevas reservas en ella.
- **RF-008**: CUANDO la persona responsable de una reserva la cancela o la modifica, el sistema deberá aplicar el cambio, liberar la franja anterior y mostrar un mensaje de confirmación.
- **RF-009**: DONDE la persona tenga permisos de administración, el sistema deberá permitir marcar una sala en mantenimiento.
- **RF-010**: SI una persona sin permisos de administración intenta cancelar o modificar una reserva de la que no es responsable, ENTONCES el sistema deberá rechazar la operación e indicar quién puede hacerlo.
- **RF-011**: CUANDO una reserva se confirma, se modifica o se cancela, el sistema deberá enviar un correo a la persona responsable con la sala, la fecha, la franja y el tipo de cambio.
- **RF-012**: El sistema deberá permitir a cada persona ver sus reservas futuras ordenadas por fecha y, para cada sala, las reservas del día en curso con el nombre de su responsable.
```

Dos decisiones que podías haber tomado de otra forma. RF-006 agrupa cuatro límites en un solo SI porque la respuesta del sistema es la misma para todos (rechazar e indicar qué límite se incumple); separarlos en varios requisitos también es correcto. RF-012 reúne dos vistas de la misma información: mis reservas y las de hoy en cada sala.

Para comprobar que no te falta ninguno de los diez puntos del paso 3:

| Punto del paso 3 | Requisito |
|---|---|
| Listar las salas | RF-001 |
| Ver disponibilidad | RF-002 |
| Confirmar una reserva | RF-003 |
| Rechazar solapamientos | RF-005 |
| Rechazar franjas fuera de horario o demasiado largas | RF-006 |
| Salas en mantenimiento | RF-007 |
| Cancelar o modificar | RF-008 |
| Permisos (mantenimiento y reservas ajenas) | RF-009 y RF-010 |
| Aviso por correo | RF-011 |
| Responsable visible | RF-004 |

Patrones usados: ubicuo, «El sistema deberá…» (RF-001, RF-004, RF-012); por evento, CUANDO (RF-002, RF-003, RF-008, RF-011); por estado, MIENTRAS (RF-007); comportamiento no deseado, SI… ENTONCES (RF-005, RF-006, RF-010); y opcional, DONDE (RF-009). Si dudas de alguno, repasa [los cinco patrones](../../docs/05-escribir-requisitos-claros-ears.md#los-cinco-patrones-y-el-sexto).

### Criterios de éxito (paso 4)

```markdown
### Resultados medibles

- **CE-001**: Reservar una sala, desde que se abre la aplicación hasta que aparece la confirmación, lleva menos de 1 minuto.
- **CE-002**: Cero reservas solapadas: en ningún momento existen dos reservas activas de la misma sala con franjas que se crucen.
- **CE-003**: El 90 % de las personas completan una reserva sin ayuda la primera vez que usan la aplicación.
- **CE-004**: El listado de disponibilidad se muestra en menos de 2 segundos.

Cómo se medirán: CE-001 y CE-003 con una prueba con 10 personas de distintos equipos antes de la puesta en marcha; CE-002 con pruebas automáticas y una comprobación semanal de los datos; CE-004 cronometrado con las 12 salas y un mes de reservas cargadas.
```

De qué criterio de Luis sale cada uno lo tienes en las filas 30 a 33 de la tabla; el RF-1 de Luis («rápido, intuitivo y fácil de usar») queda repartido entre CE-001, CE-003 y CE-004.

> [!IMPORTANT]
> Estas cifras las fijó Ana. Tú no podías preguntarle, así que lo correcto era escribir las tuyas a la vista como supuesto («cifra provisional, confirmar con Ana») y no dar la especificación por aprobada hasta que Ana las confirmara. Un CE-001 que diga «menos de 2 minutos, provisional» está bien; uno que diga «rápido», no.

### El resto de la especificación

El ejercicio no pide reescribir estas secciones, pero sí saber qué les pasa. Casi todas están resueltas en la especificación canónica; esto es lo que cambia en cada una:

| Sección | Qué cambia |
|---|---|
| Cabecera (línea 03) | Fecha `AAAA-MM-DD` y estado «Borrador» mientras queden marcadores o falte la aprobación de Ana; después, «lista para planificar». |
| Resumen (líneas 08-11) | Sin tecnología, sin parking ni catering, y con los tres problemas concretos de la hoja de cálculo (en el canon los cuenta la petición de Ana). |
| Historias (líneas 13-33) | Tres, con prioridad, «por qué» y prueba independiente: reservar una sala (P1), cancelar o modificar mi reserva (P2) y ver mis reservas y las de hoy (P3), cada una con criterios Dado/Cuando/Entonces. Las estadísticas, el proyector y el café salen. |
| Casos límite (línea 37) | Los ocho de la fila 13, cada uno con lo que hace el sistema. |
| Aclaraciones (no existe) | Sección nueva con las respuestas de Ana (bloque de abajo). |
| Entidades (líneas 66-69) | Sala con estado; Reserva con persona responsable, estado y quién la canceló o la modificó por última vez; Persona con nombre, correo corporativo y rol. Nada más. |
| Supuestos (líneas 82-83) | Fuera Chrome y la carga a mano; dentro los cuatro de la nota 45. |
| Fuera de alcance (línea 87) | La lista de la fila 36. |
| Notas de Luis (líneas 89-93) | Desaparecen. |

Así quedaría la sección «Aclaraciones» con las respuestas del paso 3. Tiene más preguntas que la del canon porque allí la petición de Ana ya fijaba el horario, las 4 horas y quién marca el mantenimiento. La última respuesta del paso 3, que toda reserva lleva el nombre de quien la hace, no hace falta preguntarla: la exige el principio 5.

```markdown
## Aclaraciones

### Sesión [AAAA-MM-DD]

- P: ¿Quién marca una sala en mantenimiento? → R: Solo administración.
- P: ¿Quién puede cancelar o modificar una reserva ajena? → R: Solo administración.
- P: ¿Hay excepciones al horario de 08:00 a 20:00 o al máximo de 4 horas (eventos, reuniones de todo el día)? → R: No, ninguna.
- P: ¿Hay que avisar por correo? → R: Sí: un correo al confirmar, al modificar y al cancelar, para que sirva de comprobante.
- P: ¿Con cuánta antelación máxima se puede reservar? → R: 30 días.
- P: ¿Se pueden hacer reservas recurrentes (por ejemplo, todos los lunes)? → R: No en la primera versión.
- P: ¿Qué pasa si nadie aparece a la reserva? → R: Fuera de alcance: no se controla la asistencia.
```

## La lista de verificación pasada

Esta es la [lista de verificación](../plantillas/lista-de-verificacion.md) de la plantilla, de CHK001 a CHK019, pasada sobre lo reescrito: los requisitos y los criterios de éxito de arriba. Lo que no se ha reescrito queda sin marcar y con una nota de qué falta, como pide el paso 5; las CHK020 a CHK022 se dejan en blanco.

| Ítem | Qué comprueba | Marca | Nota |
|---|---|---|---|
| CHK001 | Sin tecnología | `[x]` | Ni PostgreSQL, ni «tabla», ni API, ni nube. |
| CHK002 | Centrada en lo que necesitan las personas | `[x]` | Habla de reservar, consultar y cancelar, no de cómo se construye. |
| CHK003 | La entiende alguien que no programa | `[x]` | Sin jerga técnica. |
| CHK004 | Secciones obligatorias rellenas | `[ ]` | Requisitos y criterios de éxito, sí; la historia «Cancelar» está vacía (fila 12). |
| CHK005 | Sin marcadores de aclaración pendientes | `[x]` | El de las líneas 61-62 se resuelve con RF-009 y RF-010; las respuestas van a «Aclaraciones». |
| CHK006 | Cada requisito sigue una plantilla EARS | `[x]` | Los cinco patrones, uno por requisito. |
| CHK007 | Una sola cosa, comprobable con un sí o un no | `[x]` | RF-006 y RF-012 agrupan a propósito; está explicado debajo de los requisitos. |
| CHK008 | Ningún adjetivo sin cifra | `[x]` | «rápido», «intuitivo» y «fácil» pasan a CE-001, CE-003 y CE-004. |
| CHK009 | Numerados y sin repetir | `[x]` | RF-001 a RF-012, sin huecos; RF-4 y RF-10 se han fundido. |
| CHK010 | Casos límite escritos | `[ ]` | Siguen en «Ninguno destacable»: faltan los ocho de la fila 13. |
| CHK011 | Alcance acotado | `[ ]` | «Fuera de alcance» dice «nada»: fila 36. |
| CHK012 | Supuestos y dependencias escritos | `[ ]` | Quitar Chrome y la carga a mano; añadir los de la nota 45. |
| CHK013 | Historias con prioridad, «por qué» y prueba independiente | `[ ]` | Ninguna los tiene: fila 6. |
| CHK014 | La P1, ella sola, resuelve el problema principal | `[ ]` | No hay P1; debería serlo «Reservar una sala». |
| CHK015 | Dos criterios Dado/Cuando/Entonces por historia | `[ ]` | Ninguna historia los tiene: filas 8, 10, 11 y 12. |
| CHK016 | Cada requisito aparece en algún criterio de aceptación | `[ ]` | Depende de rehacer las historias; en el canon lo muestra su tabla de historias y requisitos. |
| CHK017 | Criterios de éxito con número y sin tecnología | `[x]` | CE-001 a CE-004; ninguno habla de la base de datos. |
| CHK018 | Historias para empleado y administración | `[ ]` | Administración no tiene recorrido; en el canon lo cubren RF-009, el criterio 5 de la historia 2 y un caso límite. |
| CHK019 | Compatibles entre sí y con la constitución | `[x]` | Sin reservas anónimas, contraseñas ni más sistemas que el acceso y el correo corporativos. Las entidades de Luis siguen chocando con «Datos mínimos» hasta que se corrijan (fila 29). |

Con nueve casillas sin marcar, esta especificación todavía no está lista para planificar. Se termina de arreglar rehaciendo las historias, los casos límite, los supuestos y el alcance como en la especificación canónica; con eso se marcan las que faltan.

## En tres frases

1. La especificación de Luis tiene 46 problemas, 39 principales y 7 para nota, y los más repetidos no son los que más saltan a la vista: son los choques con la constitución y las lagunas.
2. Un requisito se arregla dándole un sujeto (el sistema), un patrón EARS y una sola cosa comprobable; un criterio de éxito, poniéndole una cifra sobre algo que la persona ve.
3. Lo que no sabes no se inventa: se pregunta a quien encarga el sistema, se apunta en «Aclaraciones» y entonces se corrige el requisito; ni quien revisa ni el asistente de IA tienen la última palabra.

## Siguiente paso

Vuelve al [ejercicio 05](../05-arreglar-una-especificacion-mala.md), apunta en tu tabla los problemas que se te escaparon y termina el paso 7 comparando con la [especificación canónica](03-reserva-salas/spec.md). Después continúa con el [reto final: tu propio proyecto](../06-reto-final-tu-propio-proyecto.md), donde escribirás y revisarás tu propia especificación con esta misma lista.

---

⬅️ [Ejercicio 05](../05-arreglar-una-especificacion-mala.md) · 🏠 [Índice de soluciones](README.md)
