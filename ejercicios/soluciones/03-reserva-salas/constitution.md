# Constitución de ReservaSalas

> [!NOTE]
> Este fichero es la **constitución** (`constitution.md`) del proyecto: los principios innegociables que todo lo demás (especificación, plan técnico, tareas y código) tiene que respetar. Es el paso 0 del flujo SDD (*Spec-Driven Development*, desarrollo guiado por especificaciones) y se genera con el comando `/speckit.constitution` a partir de los principios que dicta la persona responsable. En un proyecto real vive en `.specify/memory/constitution.md`.

## Principios fundamentales (Core Principles)

### Principio 1: Sencillez primero

ReservaSalas resuelve un problema concreto: que las 12 salas de la empresa se reserven sin choques ni reservas fantasma. Cada funcionalidad tiene que justificarse con ese problema.

- No se añaden funciones «por si acaso» ni opciones de configuración que nadie ha pedido.
- Ante dos soluciones que cumplen la especificación, se elige la que menos piezas tiene: menos pantallas, menos programas de terceros de los que depender y menos datos que guardar.
- Cualquier complejidad extra (un sistema aparte para enviar avisos, un panel de administración completo, una aplicación móvil) se justifica por escrito en el plan técnico antes de implementarse.

**Por qué:** la aplicación la mantendrá un equipo pequeño. Cada pieza de más es una pieza que alguien tendrá que entender dentro de un año.

### Principio 2: Accesible y en castellano

Cualquier empleado tiene que poder usar la aplicación sin formación previa.

- Todos los textos visibles (pantallas, mensajes de error, avisos) están en castellano claro, sin jerga técnica.
- Las pantallas funcionan con teclado y con lector de pantalla (el programa que lee la pantalla en voz alta a quien no puede verla): formularios con etiquetas, botones con texto y contraste suficiente.
- Un error siempre dice qué ha pasado y qué puede hacer la persona a continuación: «La sala Báltico ya está reservada de 10:00 a 11:00. Prueba otra franja o elige otra sala».

**Por qué:** si Marta o Jorge tienen que preguntar cómo se reserva una sala, la aplicación no ha resuelto el problema.

### Principio 3: Pruebas antes de dar algo por hecho

Ninguna funcionalidad se considera terminada sin al menos una prueba automática que la demuestre.

- Cada historia de usuario tiene pruebas que se escriben **antes** que la implementación y que fallan hasta que la funcionalidad existe.
- Las reglas de negocio críticas (solapamientos, horario, duración máxima, permisos) tienen pruebas automáticas propias, pequeñas y específicas (*pruebas unitarias*).
- La batería completa de pruebas se ejecuta antes de cada entrega y tiene que pasar al 100 %.

**Por qué:** el asistente de IA genera código rápido, pero «parece que funciona» no es lo mismo que «funciona». Las pruebas son la forma de comprobarlo sin fiarse de la demo.

### Principio 4: Datos mínimos

La aplicación guarda solo lo imprescindible: nombre, correo corporativo y las reservas de cada persona.

- No se almacenan teléfonos, fotos, cargos, departamentos ni ningún dato personal que no haga falta para reservar una sala.
- No se registran hábitos de uso ni se hacen informes sobre personas concretas.
- Si una funcionalidad futura necesita más datos, esta constitución se revisa antes de empezar.

**Por qué:** menos datos es menos riesgo, menos obligaciones legales y menos explicaciones que dar.

### Principio 5: Transparencia: toda reserva tiene un responsable visible

Cada reserva muestra quién la ha hecho.

- No existen reservas anónimas ni «de la empresa».
- Cualquier empleado puede ver quién tiene reservada una sala en cada momento.
- Cualquier cambio en una reserva (modificación o cancelación) queda registrado con quién lo hizo.

**Por qué:** las reservas «fantasma» de la hoja de cálculo nacían de no saber de quién eran. Si hay un nombre al lado, se puede hablar con esa persona.

## Restricciones adicionales (Additional Constraints)

- Aplicación de uso interno, accesible solo desde la red de la empresa y con el acceso corporativo existente; no gestiona contraseñas propias.
- Los límites de uso (horario, duración máxima, antelación) se fijan en la especificación, no en el código: cambiarlos es cambiar la especificación y regenerar.
- La primera versión no se integra con el calendario corporativo ni con ningún otro sistema externo.
- Tiene que poder ejecutarse en un único servidor modesto, sin servicios adicionales que instalar.

## Flujo de trabajo y puertas de calidad (Development Workflow)

1. Toda funcionalidad empieza por una especificación en lenguaje natural que Ana (responsable de Oficina) revisa y aprueba.
2. Las dudas se resuelven en la fase de aclarar, por escrito, antes de planificar.
3. El plan técnico se comprueba punto por punto contra esta constitución antes de trocearlo en tareas.
4. Las tareas se implementan en orden, con las pruebas de cada historia escritas antes que su código.
5. Si el resultado no es el esperado, se corrige la especificación y se regenera; no se parchea el código a mano «para salir del paso».
6. Cada entrega incluye la ejecución completa de las pruebas y una revisión de esta constitución.

## Gobernanza (Governance)

Esta constitución prevalece sobre cualquier otra práctica, preferencia personal o sugerencia del asistente de IA. Si una decisión técnica choca con un principio, se cambia la decisión, no el principio.

- **Cambios:** cualquier modificación se propone por escrito, indica qué principio cambia y por qué, y la aprueba Ana. La versión se actualiza según el tipo de cambio: mayor (se quita o se redefine un principio), menor (se añade un principio o se amplía uno) o de corrección (redacción, erratas).
- **Revisión:** cada revisión de código y cada ejecución de `/speckit.analyze` comprueba el cumplimiento de los cinco principios. Cualquier desviación se justifica en la sección «Registro de complejidad» del plan técnico o se corrige.
- **Guía de uso:** los detalles de cómo trabajar en el día a día están en el `README.md` del proyecto.

**Versión:** 1.0.0 · **Ratificada:** 2026-10-05 · **Última modificación:** 2026-10-05

---

🏠 [Índice de la solución](README.md) · ➡️ [Siguiente: Especificación](spec.md)
