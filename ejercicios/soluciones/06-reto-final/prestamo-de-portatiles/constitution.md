# Constitución de PrestamoPortatiles

> [!NOTE]
> Este fichero es la **constitución** (`constitution.md`) del proyecto: los principios innegociables que todo lo demás (especificación, plan técnico, tareas y código) tiene que respetar. Es el paso 0 del flujo SDD (*Spec-Driven Development*, desarrollo guiado por especificaciones) y se genera con el comando `/speckit.constitution` a partir de los principios que dicta Luis con Ana al lado. Son cuatro, no cinco: el reto pide entre tres y cinco principios que prohíban algo concreto. En un proyecto real vive en `.specify/memory/constitution.md`.

## Principios fundamentales (Core Principles)

### Principio 1: Sencillez primero

PrestamoPortatiles resuelve un problema concreto: saber en cada momento quién tiene cada portátil y cada proyector y cuándo lo va a devolver. Cada funcionalidad tiene que justificarse con ese problema.

- No se añaden funciones «por si acaso»: nada de inventario, reparaciones, estadísticas ni reservas de otros objetos.
- Ante dos soluciones que cumplen la especificación, se elige la que menos piezas tiene: menos pantallas, menos programas de terceros de los que depender y menos datos que guardar.
- Cualquier complejidad extra (un programa aparte, una cola de mensajes, una interfaz para otros sistemas) se justifica por escrito en el plan técnico antes de implementarse.

**Por qué:** la aplicación la mantendrá un equipo pequeño. Cada pieza de más es una pieza que alguien tendrá que entender dentro de un año.

### Principio 2: Datos mínimos

La aplicación guarda solo lo imprescindible: nombre, correo corporativo y los préstamos de cada persona.

- No se almacenan teléfonos, cargos, departamentos ni el motivo por el que alguien pide un equipo.
- No se registran hábitos de uso ni se hacen informes sobre personas concretas.
- Si una funcionalidad futura necesita más datos, esta constitución se revisa antes de empezar.

**Por qué:** menos datos es menos riesgo y menos explicaciones que dar. Para saber quién tiene un equipo basta con un nombre; para avisarle, con un correo.

### Principio 3: Pruebas antes de dar algo por hecho

Ninguna funcionalidad se considera terminada sin al menos una prueba automática que la demuestre.

- Cada historia de usuario tiene pruebas que se escriben **antes** que la implementación y que fallan hasta que la funcionalidad existe.
- Las reglas de negocio (solapamientos, días laborables, duración máxima, prórrogas, avisos) tienen pruebas automáticas propias, pequeñas y específicas (*pruebas unitarias*).
- La batería completa de pruebas se ejecuta antes de cada entrega y tiene que pasar al 100 %.

**Por qué:** el asistente de IA genera código rápido, pero «parece que funciona» no es lo mismo que «funciona». Las pruebas son la forma de comprobarlo sin fiarse de la demo.

### Principio 4: Responsable visible y fecha de devolución

**Todo equipo prestado tiene una persona responsable visible y una fecha de devolución; no existen préstamos abiertos.**

- No hay préstamos anónimos ni sin fecha: sin una persona y una fecha, el sistema no guarda el préstamo.
- Cualquier empleado puede ver quién tiene cada equipo y cuándo tiene que devolverlo.
- Un equipo que no se devuelve a tiempo sigue figurando a nombre de la misma persona hasta que Oficina registra la devolución: no desaparece de la lista.
- Cada entrega y cada devolución quedan registradas con quién las hizo.

**Por qué:** el cuaderno de hoy no dice de quién es cada equipo ni cuándo vuelve, y de ahí salen los equipos que no aparecen. Si hay un nombre y una fecha al lado, se puede hablar con esa persona.

## Restricciones adicionales (Additional Constraints)

- Aplicación de uso interno, accesible solo desde la red de la empresa y con el acceso corporativo existente; no gestiona contraseñas propias.
- Los límites de uso (días máximos de préstamo, número de prórrogas, qué cuenta como día laborable) se fijan en la especificación, no en el código: cambiarlos es cambiar la especificación y regenerar.
- Todos los textos visibles están en castellano claro y las pantallas funcionan con teclado y con lector de pantalla (el programa que lee la pantalla en voz alta a quien no puede verla): formularios con etiquetas, botones con texto y contraste suficiente.
- La primera versión solo usa dos sistemas que ya existen en la empresa: el acceso corporativo, para saber quién es cada persona, y el servidor de correo, para los avisos. No se integra con el inventario de IT ni con el calendario corporativo.
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
- **Revisión:** cada revisión de código y cada ejecución de `/speckit.analyze` comprueba el cumplimiento de los cuatro principios. Cualquier desviación se justifica en la sección «Registro de complejidad» del plan técnico o se corrige.
- **Guía de uso:** los detalles de cómo trabajar en el día a día están en el `README.md` del proyecto.

**Versión:** 1.0.0 · **Ratificada:** 2026-11-03 · **Última modificación:** 2026-11-03

---

⬅️ [Anterior: Petición](peticion.md) · 🏠 [Índice del ejemplo](README.md) · ➡️ [Siguiente: Especificación](spec.md)
