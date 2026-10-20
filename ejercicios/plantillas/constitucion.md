# Plantilla: constitución

> *Qué es: los principios innegociables del proyecto; todo lo que venga después (especificación, plan, tareas y código) tiene que respetarlos. · Para quién: la escriben juntos quien encarga el proyecto y quien lo construye; la lee todo el mundo, incluido el asistente de IA en cada paso. · Consejo: entre tres y siete principios (cinco suele bastar); si no sabes decir qué prohíbe un principio, es demasiado genérico y no servirá para decidir nada.*

> [!TIP]
> Copia este fichero a tu proyecto, renómbralo `constitution.md` y rellena todo lo que va entre corchetes. Después borra este aviso y cambia el título por `# Constitución de [nombre del proyecto]`.
>
> Con Spec Kit no hace falta copiar nada: el comando `/speckit.constitution` rellena su equivalente en `.specify/memory/constitution.md`. Esta plantilla te sirve para trabajar sin herramientas o para revisar lo que genere el asistente de IA.
>
> Las ayudas de cada sección van en cursiva, en una cita bajo su título: se ven en la vista normal de GitHub y se copian con el resto. Bórralas cuando el documento esté listo.

**Proyecto:** [ReservaSalas: aplicación interna para reservar las 12 salas de reuniones de la empresa]

## Principios fundamentales

> *Qué se escribe: entre tres y siete principios (cinco suele bastar), numerados y con un nombre corto; cada uno, con una regla de 2-4 líneas y un «por qué». · Para quién: para quien tome decisiones durante el proyecto (negocio y equipo técnico) y para el asistente de IA, que los consulta antes de planificar y de implementar. · Consejo: redáctalos como reglas («cada funcionalidad tiene al menos una prueba»), no como deseos («intentaremos probar»).*

### Principio 1: [Sencillez primero]

> *Consejo: un principio es una regla clara más su motivo. Usa palabras tajantes: «siempre», «nunca», «solo».*

[Construimos lo mínimo que resuelve el problema. Nada de funciones «por si acaso»: si nadie la ha pedido, no se hace.]

**Por qué:** [Cada función extra es más código que mantener, más pruebas y más sitios donde fallar.]

### Principio 2: [Accesible y en castellano]

> *Consejo: piensa en la persona menos técnica que vaya a usar el sistema. ¿Qué le prometes?*

[Cualquier empleado la usa sin formación previa: textos en castellano, sin jerga técnica y manejable solo con teclado.]

**Por qué:** [La usará gente de todos los departamentos, no solo el equipo técnico.]

### Principio 3: [Pruebas antes de dar algo por hecho]

> *Consejo: si hay un principio que el asistente de IA tiende a saltarse cuando tiene prisa, es este. Márcalo como innegociable.*

[Cada funcionalidad tiene al menos una prueba automática que demuestra que hace lo que dice la especificación. Nada se da por terminado sin ella.]

**Por qué:** [Cuando el asistente de IA regenera el código, las pruebas avisan de lo que se ha roto.]

### Principio 4: [Datos mínimos]

> *Consejo: enumera qué datos sí se guardan; todo lo demás queda prohibido por defecto.*

[Solo guardamos nombre, correo corporativo y reservas. Ningún dato personal que no haga falta para reservar una sala.]

**Por qué:** [Menos datos significan menos riesgo si algo se filtra y menos obligaciones legales.]

### Principio 5: [Transparencia]

> *Consejo: un buen principio nace de un dolor real; aquí, las reservas «fantasma» de la hoja de cálculo.*

[Toda reserva tiene un responsable visible: cualquiera puede ver quién ha reservado cada sala y cuándo.]

**Por qué:** [Las reservas de las que nadie sabía el dueño eran el problema original del encargo.]

## Restricciones adicionales

> *Qué se escribe: límites que no son principios pero tampoco se negocian: tecnología impuesta por la empresa, normas de seguridad, plazos, presupuesto, dónde se instala (equivale a la segunda sección de la plantilla oficial de Spec Kit). · Para quién: sobre todo para quien escriba el plan técnico, y para que negocio sepa qué no va a cambiar por mucho que se pida. · Consejo: si no hay restricciones reales, escribe «Ninguna por ahora»; inventarlas solo complica el plan.*

- [Solo accesible desde la red de la empresa; sin acceso desde fuera en la primera versión.]
- [Sin integración con el calendario corporativo en la primera versión.]
- [...]

## Flujo de trabajo y puertas de calidad

> *Qué se escribe: cómo trabajamos y qué hay que cumplir para pasar de un paso al siguiente: quién revisa, quién aprueba y qué pruebas tienen que pasar (equivale a la tercera sección de la plantilla oficial). · Para quién: para el equipo que construye y para quien revisa; aquí se decide, por ejemplo, que negocio aprueba la especificación antes de planificar. · Consejo: nombra roles, no personas («la responsable de Oficina», no «Ana»): la gente cambia de puesto y el proyecto sigue.*

- [Ninguna especificación pasa a plan sin que la persona que encarga el proyecto la haya leído y aprobado.]
- [El plan técnico se comprueba contra estos principios antes de trocearlo en tareas.]
- [Nada se considera hecho si sus pruebas automáticas no pasan.]
- [...]

## Gobernanza

> *Qué se escribe: qué manda cuando hay conflicto (esta constitución está por encima de cualquier otra práctica), cómo se cambia (quién propone, quién aprueba, dónde se anota) y cómo se numera cada versión. · Para quién: para quien tenga que cambiar un principio dentro de seis meses y no sepa a quién preguntar. · Consejo: numera las versiones como Spec Kit: sube el primer número si quitas o redefines un principio, el segundo si añades uno y el tercero si solo aclaras la redacción.*

- [Esta constitución está por encima de cualquier otra práctica del proyecto. Si el plan o el código la contradicen, se corrigen el plan o el código, no la constitución.]
- [Cualquier cambio se propone por escrito, lo aprueba la persona responsable del proyecto y se anota en la tabla de versiones.]
- [Toda revisión de plan o de código comprueba de forma explícita que se cumplen los cinco principios.]

**Versión:** [1.0.0] · **Ratificada:** [AAAA-MM-DD] · **Última modificación:** [AAAA-MM-DD]

| Versión | Fecha | Qué cambió | Quién lo aprobó |
|---|---|---|---|
| [1.0.0] | [AAAA-MM-DD] | [Versión inicial con cinco principios] | [Responsable de Oficina] |

> *Volver al [índice de plantillas](README.md). Borra esta línea cuando copies la plantilla.*
