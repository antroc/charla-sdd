# Ejercicio 01: tu primera especificación sin código

> **Para quién:** quien vaya a escribir o revisar una especificación · **Tiempo de lectura:** ~7 min · **Tiempo para hacerlo:** 30-45 min · **Nivel:** 🟢 básico

Vas a escribir una especificación pequeña sin programar. El objetivo no es describir todo el proceso de vacaciones, sino dejar una primera historia suficientemente clara para que otra persona pueda revisarla y construirla sin adivinar decisiones.

**Qué vas a encontrar**

- [Objetivo](#objetivo)
- [Qué necesitas](#qué-necesitas)
- [El caso](#el-caso)
- [Pasos](#pasos)
- [Errores frecuentes](#errores-frecuentes)
- [Comprueba lo que has aprendido](#comprueba-lo-que-has-aprendido)
- [Solución o ejemplo resuelto](#solución-o-ejemplo-resuelto)
- [En tres frases](#en-tres-frases)
- [Siguiente paso](#siguiente-paso)

## Objetivo

Al terminar tendrás una especificación breve con:

- un problema y tres perfiles;
- una historia P1 que aporte valor por sí sola;
- entre tres y cinco casos límite;
- entre cuatro y seis requisitos EARS;
- dos criterios de éxito medibles;
- aclaraciones, supuestos y fuera de alcance.

## Qué necesitas

- La plantilla [especificacion.md](plantillas/especificacion.md).
- La plantilla [lista-de-verificacion.md](plantillas/lista-de-verificacion.md).
- Un documento o editor de texto.
- Opcionalmente, cualquier chat de IA autorizado. No necesitas Spec Kit ni un asistente concreto.

## El caso

Hoy las vacaciones se piden por correo. Luis escribe a Marta, su manager; Marta responde cuando puede; Jorge, de RRHH, actualiza el saldo en una hoja de cálculo. Algunas solicitudes se pierden y las personas no saben con seguridad cuántos días les quedan.

La primera versión solo resolverá una cosa: **registrar una solicitud y dejarla pendiente para que no se pierda**. Aprobarla dentro del sistema y consultar informes completos serán iteraciones posteriores.

## Pasos

1. **Prepara la cabecera y el resumen.**

   Usa este título y esta petición original:

   ```text
   Especificación: Solicitud de vacaciones
   Petición original: «Queremos dejar de pedir las vacaciones por correo y saber que cada solicitud queda registrada».
   ```

   Escribe un resumen de tres a cinco frases que explique la situación actual, el problema y el resultado esperado. No menciones tecnología.

   - [ ] La cabecera y el resumen se entienden sin contexto adicional.

2. **Identifica los perfiles.**

   ```text
   - Empleado: quiere pedir días y saber que la solicitud no se ha perdido.
   - Manager: quiere recibir las solicitudes de su equipo.
   - RRHH: quiere disponer de un registro fiable para las siguientes iteraciones.
   ```

   Puedes cambiar la redacción, pero no añadas funciones todavía.

   - [ ] Cada perfil tiene una necesidad concreta.

3. **Escribe la historia P1.**

   La historia es «Pedir días de vacaciones». Debe incluir:

   - recorrido en lenguaje natural;
   - por qué es P1;
   - una prueba independiente;
   - al menos dos criterios Dado / Cuando / Entonces: uno correcto y uno de rechazo.

   Ejemplo de arranque:

   ```text
   Como empleado quiero solicitar unos días de vacaciones para que mi petición quede registrada y mi manager la reciba.

   Dado que Luis tiene 12 días disponibles,
   cuando pide 5 días laborables,
   entonces la solicitud queda pendiente y Marta recibe un aviso.
   ```

   Deja P2 «Aprobar o rechazar» y P3 «Consultar saldos e informes» como siguientes iteraciones, con una sola frase cada una.

   - [ ] La P1 funciona de forma independiente y P2/P3 quedan fuera de esta primera entrega.

4. **Añade entre tres y cinco casos límite.**

   Incluye, como mínimo:

   - más días de los disponibles;
   - fecha de inicio pasada;
   - fechas no válidas o invertidas.

   Añade uno o dos casos más, por ejemplo fines de semana, festivos o una persona sin manager asignado. Si no sabes qué debe ocurrir, márcalo como aclaración.

   - [ ] Cada caso límite dice qué ocurre o qué decisión falta.

5. **Escribe entre cuatro y seis requisitos EARS.**

   Cubre solo la P1. Una posible distribución es:

   ```text
   RF-001: El sistema deberá mostrar a cada persona sus días disponibles del año en curso.

   RF-002: CUANDO una persona envía una solicitud con fechas válidas,
   el sistema deberá registrarla en estado «pendiente» y avisar a su manager.

   RF-003: SI una persona solicita más días de los que tiene disponibles,
   ENTONCES el sistema deberá rechazar la solicitud e indicar su saldo disponible.

   RF-004: SI la fecha de inicio es anterior a la fecha actual,
   ENTONCES el sistema deberá rechazar la solicitud e indicar que no se admiten fechas pasadas.

   RF-005: MIENTRAS una solicitud esté pendiente,
   el sistema deberá mostrarla con ese estado a la persona solicitante.
   ```

   Puedes separar el registro y el aviso en dos requisitos si prefieres que cada uno tenga una única responsabilidad. No incluyas todavía aprobar, rechazar por parte del manager ni vistas de RRHH.

   Entidades mínimas:

   - **Persona:** nombre, correo corporativo, manager y saldo disponible.
   - **Solicitud:** persona, fechas, días consumidos, estado y fecha de creación.

   - [ ] Hay entre cuatro y seis requisitos comprobables, sin tecnología y dentro de la P1.

6. **Define dos criterios de éxito.**

   Deben contener una cifra y poder medirse sin conocer la tecnología.

   ```text
   CE-001: Crear y enviar una solicitud válida lleva menos de 2 minutos.
   CE-002: El 100 % de las solicitudes enviadas correctamente quedan visibles para la persona solicitante y su manager.
   ```

   Puedes proponer otras cifras, siempre que expliques cómo se medirán.

   - [ ] Hay exactamente dos criterios medibles y relacionados con la P1.

7. **Aclara lo que no puedes decidir.**

   Escribe entre tres y cinco preguntas. Por ejemplo:

   - ¿Los días se cuentan en laborables o naturales?
   - ¿Cuál es la antelación mínima?
   - ¿Qué ocurre si una persona no tiene manager asignado?
   - ¿Los días pendientes se descuentan del saldo visible?

   Responde solo si estás haciendo también el papel de quien encarga. En ese caso, escribe la respuesta antes de aplicarla:

   ```text
   P: ¿Los días se cuentan en laborables o naturales?
   R: En laborables.
   ```

   Después modifica los requisitos y criterios afectados. Una aclaración que no cambia el documento no ha cerrado ninguna decisión.

   Añade también:

   - **Supuestos:** por ejemplo, todas las personas tienen saldo cargado para el año.
   - **Fuera de alcance:** aprobación dentro del sistema, cancelaciones, nómina, bajas médicas e informes globales.

   - [ ] Las respuestas están reflejadas en la especificación y el alcance está acotado.

8. **Pasa la lista de verificación.**

   Usa [lista-de-verificacion.md](plantillas/lista-de-verificacion.md). Corrige cada «no» que afecte a la P1. No marques como fallo que P2 y P3 estén incompletas: están fuera de esta entrega y deben aparecer así.

   - [ ] La P1 pasa la lista o cada pendiente tiene una explicación.

### Revisión opcional con cualquier asistente

Pega tu borrador junto con este *prompt*:

```text
Revisa esta especificación como revisor funcional. No propongas tecnología ni reescribas todo el documento. Hazme, de una en una, un máximo de cinco preguntas sobre alcance, reglas, permisos, datos o casos límite. En cada pregunta explica qué parte del documento cambiaría. Espera mi respuesta antes de continuar.

[PEGA AQUÍ LA ESPECIFICACIÓN]
```

El resultado depende del modelo, pero el criterio es común: las preguntas deben cerrar decisiones, no añadir funciones nuevas.

## Errores frecuentes

| Síntoma | Qué ocurre | Cómo corregirlo |
|---|---|---|
| La P1 incluye pedir, aprobar, cancelar e informar a RRHH | El alcance vuelve a ser todo el proceso | Quédate con registrar la solicitud pendiente |
| El ejemplo tiene siete requisitos aunque el ejercicio pide seis como máximo | Se han arrastrado requisitos de P2/P3 | Elimina aprobación, informes y permisos avanzados |
| Los criterios dicen «rápido» o «fácil» | No se pueden medir | Añade tiempo, porcentaje o cantidad |
| Una aclaración está respondida, pero el requisito no cambia | La decisión no se ha propagado | Modifica el texto afectado y vuelve a revisar |
| El asistente diseña pantallas o elige base de datos | Se ha mezclado el qué con el cómo | Devuelve la conversación a comportamiento y reglas |

## Comprueba lo que has aprendido

1. ¿Por qué la P1 no incluye la aprobación del manager?
2. ¿Cuántos requisitos y criterios de éxito pide este ejercicio?
3. ¿Dónde va la decisión de usar una base de datos concreta?
4. ¿Qué haces con una duda que no puedes resolver?
5. ¿Una solución con más historias es necesariamente mejor?

<details><summary>Ver respuestas</summary>

1. Porque la primera entrega ya aporta valor si evita que las solicitudes se pierdan; la aprobación es la siguiente iteración.
2. Entre cuatro y seis requisitos, y dos criterios de éxito.
3. En el plan técnico, no en la especificación.
4. La escribes como aclaración pendiente y no inventas la respuesta.
5. No. Puede estar añadiendo alcance y haciendo más difícil la revisión.

</details>

## Solución o ejemplo resuelto

La [solución del ejercicio 01](soluciones/01-solicitud-de-vacaciones/README.md) distingue entre el mínimo esperado de esta versión y una especificación ampliada del proceso completo.

## En tres frases

1. Una primera especificación útil puede cubrir una sola historia y dejar el resto fuera de alcance.
2. Los requisitos describen comportamiento comprobable; los criterios de éxito miden el resultado.
3. Las aclaraciones se escriben y se propagan al documento antes de continuar.

## Siguiente paso

Continúa con [Practicar requisitos EARS](02-practicar-requisitos-ears.md).

---

⬅️ [Anterior: Preparación del entorno](00-preparacion-del-entorno.md) · 🏠 [Índice](README.md) · ➡️ [Siguiente: Requisitos EARS](02-practicar-requisitos-ears.md)
