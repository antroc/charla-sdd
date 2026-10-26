# Preguntas frecuentes

> **Para quién:** toda la empresa, sepa programar o no · **Tiempo de lectura:** ~10 min · **Nivel:** 🟢 básico

Aquí están las preguntas que suelen aparecer cuando la idea de SDD pasa de «suena bien» a «vale, ¿y esto cómo encaja en un proyecto de verdad?».

Las respuestas van al grano y enlazan al capítulo donde se desarrolla cada tema. Si te encuentras un término que no conoces, el [glosario](10-glosario.md) está pensado justo para eso.

**Qué vas a encontrar**

- [Para decidir si lo probáis](#para-decidir-si-lo-probáis): si es más lento, quién responde cuando algo falla, cómo encaja con lo que ya hace tu equipo y cómo justificarlo ante dirección.
- [Para escribir y revisar especificaciones](#para-escribir-y-revisar-especificaciones): si hace falta saber programar, qué te va a tocar hacer y si sirve para procesos sin código.
- [Para construir con SDD](#para-construir-con-sdd): proyectos que ya existen, qué cambia en tu trabajo y qué hacer cuando el asistente se equivoca.
- [Sobre herramientas](#sobre-herramientas): si Spec Kit es obligatorio, qué asistente necesitas, cuánto cuesta y qué hacer si un comando no funciona.
- [Sobre cómo empezar en la empresa](#sobre-cómo-empezar-en-la-empresa): por dónde empezar mañana, qué datos no meter en un asistente, cómo montar un piloto y cómo llevarlo a tu equipo.

## Para decidir si lo probáis

### ¿Esto es más lento que pedirle directamente al asistente?

Al principio suele exigir más disciplina que pedir código directamente, porque hay que escribir y revisar antes de implementar. Esa inversión tiene sentido cuando el software va a durar, va a cambiar o lo va a mantener más de una persona.

Para un prototipo desechable, ir directo al código puede ser perfectamente razonable. SDD empieza a aportar valor cuando necesitas conservar las decisiones y comprobar que los cambios siguen respetando lo que se había acordado.

*Para saber más:* [los dos caminos, cara a cara](../diagramas/01-vibe-coding-vs-sdd.md#los-dos-caminos-cara-a-cara) · [el flujo de un vistazo](03-el-flujo-paso-a-paso.md#el-flujo-de-un-vistazo)

### ¿No es volver a escribir documentos que nadie lee?

No debería serlo. Una especificación describe una funcionalidad, no un sistema entero: la de ReservaSalas se lee en unos diez minutos. Y no se escribe para archivarla: el asistente la lee en cada paso, de ella salen el plan técnico (`plan.md`) y la lista de tareas (`tasks.md`), y cuando cambia lo que se quiere, se cambia ella primero.

Tampoco es la «cascada» de antes, con meses de documentos antes de ver nada funcionando: cada funcionalidad recorre el flujo entero en horas o en un par de días. Si una sección no cambia lo que se construye, sobra.

*Para saber más:* [qué no es SDD](02-que-es-sdd.md#qué-no-es-sdd) · [la especificación como referencia viva](02-que-es-sdd.md#qué-cambia-la-especificación-deja-de-ser-documentación-decorativa)

### ¿Sustituye a las historias de usuario que ya tenemos en nuestro gestor de tareas?

No: se complementan. Las historias de usuario de la especificación (lo que cada tipo de persona quiere conseguir, ordenado por prioridad: P1, P2, P3) son las que van al tablero del equipo, y las tareas de cada historia son sus subtareas. En ReservaSalas, la historia 1 se reparte en las tareas T013 a T024.

Lo que cambia es dónde vive el detalle: requisitos, criterios de aceptación y decisiones están en la especificación, dentro del repositorio (la carpeta compartida donde vive el código con su historial). La tarjeta del tablero puede enlazarla en vez de copiarla, y así no hay dos versiones que acaben contradiciéndose.

*Para saber más:* [cómo encaja con las reuniones y los procesos de hoy](06-roles-quien-hace-que.md#cómo-encaja-con-las-reuniones-y-los-procesos-de-hoy)

### ¿Quién es responsable si el código falla?

Las personas, no el asistente de IA. Cada paso tiene una persona que lo lidera (y responde de que salga bien) y otra distinta que lo revisa. El asistente redacta y ejecuta, pero no aprueba: la especificación la aprueba quien encarga, y el plan, las tareas y el código los lidera quien construye, con revisión técnica.

Lo que SDD añade es rastro. Si la especificación no decía lo que se quería, se corrige ella; si el código no hace lo que dicen las tareas, es un fallo de implementación que se corrige y se cubre con una prueba nueva. No evita todos los fallos, pero ayuda a saber dónde nació cada uno.

*Para saber más:* [quién escribe y quién aprueba cada artefacto](../diagramas/03-artefactos-y-relaciones.md#quién-escribe-y-quién-aprueba-cada-artefacto) · [cuando algo falla: qué se corrige](08-buenas-practicas-y-errores-comunes.md#cuando-algo-falla-qué-se-corrige)

### ¿Qué tengo que hacer yo, si dirijo el equipo, para que funcione?

Tres cosas, y ninguna exige saber programar. Proteger el tiempo de los pasos poco vistosos (aclarar dudas y analizar la coherencia), que son los que más tienta saltarse. Asegurarte de que la persona que decide está identificada y disponible cuando se la necesita. Y no premiar la prisa: si quien se salta la especificación es quien entrega «más rápido», el equipo entero aprende a saltársela.

¿Cómo sabes si va bien? Sin auditorías: mira unas pocas señales, como que quien encarga haya leído y corregido la especificación, o que el último cambio del programa empezara por un cambio en ella.

*Para saber más:* [dos riesgos que conviene conocer](06-roles-quien-hace-que.md#dos-riesgos-que-conviene-conocer) · [señales de que lo estás haciendo bien](08-buenas-practicas-y-errores-comunes.md#señales-de-que-lo-estás-haciendo-bien)

### ¿Cómo se lo justifico a dirección?

Con datos de tu piloto, no con promesas. Lleva tres: cuánto tiempo de más costó escribir y aclarar la especificación, cuántos malentendidos se detectaron antes de programar y cuántos cambios posteriores empezaron por un cambio en la especificación, sin tocar el código a ciegas.

Añade los riesgos que reduce (depender de una sola persona, rehacer trabajo, guardar datos que nadie decidió guardar) y di también lo que no promete: SDD reduce riesgos; no los elimina. El método y Spec Kit son gratuitos; el asistente de IA es el que ya pague la empresa.

*Para saber más:* [cómo montar un piloto](#cómo-monto-un-piloto-en-mi-equipo) · [lo que le cuesta a la empresa no tener especificación](01-el-problema-del-vibe-coding.md#lo-que-le-cuesta-a-la-empresa) · [cuánto cuesta](#cuánto-cuesta)

## Para escribir y revisar especificaciones

### ¿Tengo que saber programar para escribir una especificación?

No. La especificación se escribe en castellano corriente y sin tecnología: dice qué se quiere, por qué y cómo sabremos que está bien. De hecho, quien mejor escribe un requisito es quien conoce el problema.

Para que cada frase admita una sola lectura existe EARS (*Easy Approach to Requirements Syntax*, una forma sencilla y estructurada de redactar requisitos): cinco plantillas de frase como «CUANDO una persona envía una solicitud, el sistema deberá avisar a su manager». La «Solicitud de vacaciones» la puede escribir Jorge, de RRHH, sin ayuda de nadie técnico.

*Para saber más:* [qué es EARS](05-escribir-requisitos-claros-ears.md#qué-es-ears) · [ejercicio 01: tu primera especificación sin código](../ejercicios/01-tu-primera-especificacion-sin-codigo.md)

### ¿Qué me va a tocar hacer y cuánto tiempo me llevará?

Si encargas algo, cuatro cosas: describir lo que necesitas (o revisar la especificación que redacte el asistente), responder a las aclaraciones, validar los criterios de éxito (cómo sabremos que ha funcionado, con cifras) y probar el resultado según se va terminando. Ninguna exige instalar nada ni leer código.

Son horas, no semanas: Ana, la responsable de Oficina que encargó ReservaSalas, respondió a las cinco preguntas de aclaración en una reunión de 15 minutos. Eso sí, hay que estar disponible en esos momentos; si desapareces después de escribir, los malentendidos salen en la demo final, que es el peor momento.

*Para saber más:* [si no eres técnico: lo que puedes hacer desde mañana](06-roles-quien-hace-que.md#si-no-eres-técnico-lo-que-puedes-hacer-desde-mañana) · [el papel de quien encarga el proyecto](06-roles-quien-hace-que.md#quien-encarga-el-proyecto-ana)

### No trabajo en tecnología: ¿qué pinto yo en un proyecto de software?

Aportas lo que nadie más sabe de tu área: por ejemplo, qué datos de las personas existen ya, cuáles no deben guardarse y quién tiene qué rol. En ReservaSalas, esa frontera la marca el principio «Datos mínimos» de la constitución (`constitution.md`, las reglas innegociables del proyecto): solo nombre, correo corporativo y reservas.

Y puedes ir más allá: escribir tú la especificación de un proceso de tu área. La «Solicitud de vacaciones» (una persona pide días, su manager aprueba o rechaza con motivo y RRHH lo registra) es exactamente eso.

*Para saber más:* [el papel de Jorge en ReservaSalas](06-roles-quien-hace-que.md#rrhh-y-otros-perfiles-de-negocio-jorge) · [la especificación resuelta de la solicitud de vacaciones](../ejercicios/soluciones/01-solicitud-de-vacaciones/especificacion.md)

### ¿Sirve para cosas que no son software?

Sí, sobre todo la parte de pensar. Poner por escrito qué quieres, por qué y cómo sabrás que está bien sirve igual aunque al final lo resuelva una hoja de cálculo, un formulario o un procedimiento en papel. La «Solicitud de vacaciones» del ejercicio 01 no tiene ni una palabra de tecnología.

En un proceso sin código, el «plan» es el procedimiento, las «tareas» son quién hace qué, e «implementar» es ponerlo en marcha y medirlo contra los criterios de éxito. Lo que no aplica es lo propio del software, como las pruebas automáticas.

*Para saber más:* [sin herramientas: plantillas y un chat de IA](07-herramientas.md#sin-herramientas-plantillas-y-un-chat-de-ia) · [para quién es SDD](02-que-es-sdd.md#para-quién-es)

### ¿Y si el asistente me pregunta algo que no sé responder?

Dilo y averigua quién lo decide. El asistente suele proponer una respuesta recomendada, pero decidir es cosa de quien encarga el proyecto; si responde otra persona «para no molestar», el paso pierde su sentido.

Mientras tanto, no inventes el dato: un requisito con un límite que nadie ha decidido parece cerrado, y es peor que una frase vaga. Deja el marcador `[NECESITA ACLARACIÓN: …]` en la especificación y pregúntalo a quien decide. Si necesitas una cifra provisional para seguir trabajando, escríbela a la vista como supuesto («se asume 5 segundos; confirmar con Seguridad») y no des la especificación por aprobada hasta que quien encarga la confirme.

*Para saber más:* [paso 2: aclarar](03-el-flujo-paso-a-paso.md#paso-2-aclarar) · [si te falta un dato](05-escribir-requisitos-claros-ears.md#si-te-falta-un-dato)

### Me pasan una especificación para revisar: ¿en qué me fijo?

Empieza por tres preguntas: ¿se entiende sin ayuda?, ¿hay alguna palabra de tecnología (una base de datos, un lenguaje de programación, un producto concreto)?, ¿cada requisito se puede comprobar con un sí o un no? Después, mira que la historia P1 (la imprescindible) resuelva por sí sola el problema principal y que cada criterio de éxito lleve una cifra.

Para ir más a fondo está la lista de verificación (o *checklist*): preguntas de sí o no sobre la calidad del texto. Funciona mejor si la pasa alguien que no escribió la especificación.

*Para saber más:* [la lista de verificación](04-los-artefactos.md#la-lista-de-verificación) · [su plantilla](../ejercicios/plantillas/lista-de-verificacion.md) · [ejercicio 05: arreglar una especificación mala](../ejercicios/05-arreglar-una-especificacion-mala.md)

## Para construir con SDD

### ¿Qué pasa con proyectos que ya existen?

No hace falta tirarlos ni documentarlos enteros de golpe. Empieza por el próximo cambio: escribe su especificación a partir de lo que la aplicación hace hoy y de lo que debería hacer, y sigue el flujo desde ahí. El asistente puede ayudarte con un borrador, pero lo corrige quien sabe qué *debería* hacer el sistema.

Con GitHub Spec Kit (la herramienta que añade el flujo a tu asistente), `specify init --here` prepara la carpeta actual: avisa de que mezclará sus plantillas con tus ficheros (y de que puede sobrescribir alguno) y pide confirmación. Haz antes un *commit* (guardar una versión en el historial) para poder comparar.

*Para saber más:* [síntomas y causa raíz](01-el-problema-del-vibe-coding.md#síntomas-y-causa-raíz) · [cómo se inicia un proyecto con Spec Kit](07-herramientas.md#cómo-se-inicia-un-proyecto)

### ¿Entonces ya no voy a escribir código?

Vas a teclear menos y a pensar, decidir y revisar más. Eliges la tecnología y la justificas en el plan, compruebas que cada requisito aparece en alguna tarea, lees lo que genera el asistente antes de aceptarlo, ejecutas las pruebas y vuelves a la especificación cuando algo no cuadra. La edición a mano queda para detalles que no cambian el comportamiento.

Para quien empieza, el método da una estructura que antes solo daba la experiencia; para quien ya la tiene, el valor se desplaza a revisar planes y tareas.

*Para saber más:* [qué cambia en el trabajo de quien programa](06-roles-quien-hace-que.md#qué-cambia-en-el-trabajo-de-quien-programa)

### Si el asistente se equivoca, ¿no es más rápido arreglarlo a mano?

En el momento, quizá; dos semanas después, no. Si parcheas el código y no la especificación, el documento deja de contar la verdad, el código y las pruebas se separan de lo escrito, y la siguiente regeneración puede borrar tu arreglo sin que nadie sepa por qué.

Antes de tocar nada, busca dónde está el error: ¿la especificación dice lo que de verdad se quiere?, ¿el plan y las tareas la cumplen?, ¿el código hace lo que dicen las tareas? Se corrige en ese nivel; si es un fallo de implementación, lo corrige el asistente y se añade una prueba que lo demuestre.

*Para saber más:* [cuando algo falla: qué se corrige](08-buenas-practicas-y-errores-comunes.md#cuando-algo-falla-qué-se-corrige) · [el riesgo de saltarse la especificación por prisa](06-roles-quien-hace-que.md#quien-programa-se-salta-la-especificación-porque-tiene-prisa)

### ¿Hay que recorrer todo el flujo hasta para un cambio pequeño?

No. Para cambiar algo que ya existe se toca la especificación (y el plan, si recoge el dato) y se regenera solo lo afectado. Es el paso 9 del ejercicio 03: la antelación máxima de ReservaSalas pasa de 30 a 60 días cambiando el requisito RF-006, y con Spec Kit `/speckit.converge` añade las tareas que faltan y `/speckit.implement` las ejecuta.

Para una funcionalidad nueva y muy pequeña, Spec Kit admite un camino corto (`specify → plan → tasks → implement → converge`). En él no aparecen aclarar ni analizar, aunque suelen ser los pasos que más disgustos evitan.

*Para saber más:* [cada herramienta lo llama a su manera](03-el-flujo-paso-a-paso.md#cada-herramienta-lo-llama-a-su-manera) · [ejercicio 03: ReservaSalas paso a paso](../ejercicios/03-reserva-salas-paso-a-paso.md)

### ¿Sirve para proyectos grandes o solo para aplicaciones pequeñas como ReservaSalas?

El método trabaja funcionalidad a funcionalidad: cada una tiene su carpeta con especificación, plan y tareas (`specs/001-…`, `specs/002-…`), y todas comparten la misma constitución. Un sistema grande no se aborda con una especificación gigante, sino como una serie de funcionalidades pequeñas, cada una con una P1 que vale sola.

Siendo honestos, este material solo enseña ejemplos pequeños, porque es como mejor se aprende. Cuanto más grande es el proyecto, más importa que la constitución prohíba cosas concretas y que cada plan pase una revisión técnica seria.

*Para saber más:* [buenas prácticas al especificar](08-buenas-practicas-y-errores-comunes.md#al-especificar-pasos-0-a-2) · [dónde viven los artefactos en un proyecto](04-los-artefactos.md#dónde-viven-en-un-proyecto)

## Sobre herramientas

### ¿Es obligatorio usar Spec Kit?

No. SDD es un método, no un programa, y se puede seguir de tres formas: con GitHub Spec Kit (una herramienta gratuita que añade los pasos del método al asistente que ya usas), con Kiro (un editor de AWS con un flujo parecido integrado) o sin herramientas, con las plantillas y un chat de IA autorizado.

Las tres producen lo mismo: una especificación que es la fuente de verdad, y un plan y unas tareas que salen de ella. Si en tu equipo todavía no se puede instalar nada, no esperes: cuando llegue la herramienta, los ficheros ya estarán escritos.

*Para saber más:* [tres formas de hacer SDD](07-herramientas.md#tres-formas-de-hacer-sdd) · [plantillas de los artefactos](../ejercicios/plantillas/README.md)

### ¿Qué asistente necesito?

Depende de lo que vayas a hacer. Si no vas a construir software, ninguno: bastan las plantillas y, si quieres, el chat de IA genérico que tenga autorizado la empresa. Si vas a construir con Spec Kit, un asistente de programación con IA compatible: en la fecha de este material, Spec Kit reconoce 41, más una integración genérica para el resto. Claude Code, GitHub Copilot, Cursor o Gemini CLI son ejemplos de asistentes compatibles.

Cuál usar no es una elección personal: lo decide la empresa. Pregunta cuál está autorizado antes de instalar ninguno.

*Para saber más:* [asistentes compatibles](07-herramientas.md#asistentes-compatibles) · [qué necesitas según lo que vayas a hacer](07-herramientas.md#qué-necesitas-según-tu-perfil)

### ¿Cuánto cuesta?

El método, nada: es una forma de trabajar. Spec Kit es gratuito y de código abierto, con licencia MIT (que permite usarlo también en empresas). El asistente de IA tiene su propio coste, el que ya pague la empresa; y si se elige Kiro, hay que consultar antes las condiciones de AWS.

Lo que sí cuesta es tiempo al principio: escribir y aclarar la especificación antes de pedir código. La apuesta del método es recuperarlo después, cuando llegan los cambios y nadie tiene que adivinar qué debía hacer el sistema.

*Para saber más:* [la comparativa de las tres opciones](07-herramientas.md#comparativa) · [lo que le cuesta a la empresa no tener especificación](01-el-problema-del-vibe-coding.md#lo-que-le-cuesta-a-la-empresa)

### He seguido el material y un comando no funciona: ¿qué hago?

Primero, mira cómo lo escribe tu asistente: `/speckit.specify`, `/speckit-specify` y `$speckit-specify` son la misma orden, y se escriben en el chat del asistente. En la terminal (la ventana donde se escriben órdenes al ordenador) solo van los comandos que empiezan por `specify`.

Si aun así falla, sospecha de la versión: Spec Kit cambia deprisa, y un error como «No such option: --integration» indica que la tuya es muy antigua. Compruébala con `specify version` y reinstala la versión actual con `uv tool install --force specify-cli`: en una versión tan antigua, `specify self upgrade` todavía no existe (úsalo a partir de ahora para las siguientes actualizaciones). Ante la duda, vale lo que diga [la documentación oficial](https://github.github.io/spec-kit/); y avisa para que corrijamos el material.

*Para saber más:* [cómo se escriben según el asistente](07-herramientas.md#cómo-se-escriben-según-el-asistente) · [las herramientas cambian; el método no](07-herramientas.md#las-herramientas-cambian-el-método-no) · [errores frecuentes al instalar](../ejercicios/00-preparacion-del-entorno.md#errores-frecuentes)

## Sobre cómo empezar en la empresa

### ¿Cómo empiezo mañana?

Con algo pequeño, según lo que vayas a hacer:

- **Si vas a escribir o revisar especificaciones:** haz el [ejercicio 01](../ejercicios/01-tu-primera-especificacion-sin-codigo.md), la especificación de la «Solicitud de vacaciones», en una hora u hora y media y sin instalar nada.
- **Si vas a construir con SDD:** prepara el entorno con la vía B del [ejercicio 00](../ejercicios/00-preparacion-del-entorno.md) y recorre el flujo completo en el [ejercicio 03](../ejercicios/03-reserva-salas-paso-a-paso.md).
- **Si diriges un equipo:** lleva la [dinámica de 20 minutos](../ejercicios/04-dinamica-de-equipo-20-minutos.md) a tu próxima reunión; no hace falta ningún ordenador.

*Para saber más:* [itinerarios por perfil](../diagramas/06-mapa-del-repositorio.md#itinerarios-por-perfil) · [índice de documentación](README.md)

### ¿Puedo meter datos de clientes en el asistente?

> [!WARNING]
> No, salvo en un asistente que la empresa haya autorizado expresamente para ello. Y lo mismo vale para cualquier dato real de personas: nombres, correos, nóminas, contratos o listados de clientes o de empleados.

Para probar, inventa los datos, como hace todo este repositorio (Ana, Luis, la sala Mediterráneo…), y ante la duda pregunta a IT o a seguridad antes de pegar nada. Una especificación tampoco los necesita: describe qué datos guarda el sistema (en ReservaSalas, solo nombre, correo corporativo y reservas), no los datos en sí.

*Para saber más:* [uso responsable de los asistentes de IA](../ejercicios/00-preparacion-del-entorno.md#uso-responsable-de-los-asistentes-de-ia) · [el principio «Datos mínimos» de ReservaSalas](../ejercicios/soluciones/03-reserva-salas/constitution.md#principio-4-datos-mínimos)

### ¿Puedo instalar Spec Kit en el ordenador del trabajo?

Depende de las normas de la empresa, así que pregunta antes a tu responsable o a IT. Necesitas permiso para instalar Python 3.11 o superior, `uv` y Spec Kit, y que el asistente que vayas a usar esté autorizado. Si la red corporativa bloquea la descarga, IT puede darte la dirección de su índice privado de paquetes (el almacén interno del que se descargan los programas).

Si no se puede instalar nada, empieza igual: el método se puede seguir con las plantillas y un documento compartido.

*Para saber más:* [ejercicio 00, vía B: entorno completo](../ejercicios/00-preparacion-del-entorno.md#pasos-de-la-vía-b-entorno-completo-con-spec-kit) · [qué hay que pedir antes de instalar](07-herramientas.md#comparativa)

### ¿Con qué proyecto pruebo la primera vez?

Con uno pequeño, real y que no sea crítico: un problema que se explique en cinco frases y cuya parte imprescindible (la historia P1) quepa en uno o dos días de trabajo, con sus pruebas. Mejor si alguien lo sufre y puede responder a las aclaraciones por escrito, como Ana con ReservaSalas. El préstamo de portátiles, un buzón de sugerencias o los días en la oficina son buenos candidatos.

Y si gusta y alguien quiere usarlo de verdad, habla antes con IT y con seguridad: un ejercicio de formación no está listo, sin más, para que lo use toda la empresa.

*Para saber más:* [ocho ideas de proyecto](../ejercicios/06-reto-final-tu-propio-proyecto.md#ocho-ideas-de-proyecto) · [empieza pequeño](08-buenas-practicas-y-errores-comunes.md#al-especificar-pasos-0-a-2)

### ¿Cómo monto un piloto en mi equipo?

Elige una funcionalidad pequeña cuya historia P1 quepa en uno o dos días de trabajo. Nombra a tres personas: quien encarga y decide; quien construye con un asistente autorizado (si en tu equipo nadie programa, pídeselo al equipo técnico que os da servicio), y quien revisa sin haber escrito la especificación.

Antes de empezar, pregunta a IT qué asistente está autorizado y pide un repositorio donde quien encarga pueda leer los documentos. Dale un plazo corto (en nuestra experiencia, de dos a cuatro semanas bastan para recorrer el flujo y hacer algún cambio) y, al final, repasa las señales de que lo estás haciendo bien (¿quien encarga corrigió la especificación?, ¿el último cambio empezó por ella?) y decide: seguir, ajustar o parar.

*Para saber más:* [quién hace qué en cada paso](06-roles-quien-hace-que.md#quién-hace-qué-en-cada-paso) · [señales de que lo estás haciendo bien](08-buenas-practicas-y-errores-comunes.md#señales-de-que-lo-estás-haciendo-bien) · [cómo justificarlo ante dirección](#cómo-se-lo-justifico-a-dirección)

### ¿Cómo lo presento a mi equipo?

Para que un equipo lo pruebe sin ordenadores, la [dinámica de 20 minutos](../ejercicios/04-dinamica-de-equipo-20-minutos.md), que puede dirigir cualquiera con su guion minuto a minuto, también en línea. Para que cada persona siga a su ritmo, comparte la [portada](../README.md): tiene una ruta de lectura para cada necesidad.

*Para saber más:* [variantes de la dinámica](../ejercicios/04-dinamica-de-equipo-20-minutos.md#variantes) · [por dónde empezar](../README.md#empieza-por-aquí)

## En tres frases

1. SDD pide más tiempo al principio, para escribir y aclarar la especificación, a cambio de que cada cambio posterior parta de un texto que todo el mundo puede leer; el método y Spec Kit son gratuitos, y el asistente de IA es el que autorice la empresa.
2. No hace falta saber programar para escribir o revisar una especificación; las personas deciden y responden de cada paso, y el asistente redacta y ejecuta, pero no aprueba nada.
3. Para empezar, algo pequeño (el ejercicio 01 si vas a escribir o revisar especificaciones, el 00 y el 03 si vas a construir con SDD, la dinámica de 20 minutos si diriges un equipo) y ningún dato real en un asistente que la empresa no haya autorizado.

## Siguiente paso

Continúa con el [Glosario](10-glosario.md): las palabras de este repositorio que pueden sonarte raras, en orden alfabético y en lenguaje llano, cada una con un enlace al documento donde se explica.

---

⬅️ [Anterior: Buenas prácticas y errores comunes](08-buenas-practicas-y-errores-comunes.md) · 🏠 [Índice de documentación](README.md) · ➡️ [Siguiente: Glosario](10-glosario.md)
