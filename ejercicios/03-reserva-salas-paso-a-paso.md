# Ejercicio 03: ReservaSalas paso a paso

> **Para quién:** quien quiera recorrer un flujo SDD completo con Spec Kit y cualquier asistente compatible · **Tiempo de lectura:** ~15 min · **Tiempo para hacerlo:** 90-120 min · **Nivel:** 🟡 intermedio

En este ejercicio construirás una aplicación pequeña para reservar salas. El objetivo no es aprender una herramienta concreta, sino practicar el relevo entre petición, constitución, especificación, aclaraciones, plan, tareas, pruebas y código.

Los artefactos deben permitir que una persona o agente distinto continúe cada etapa sin depender del historial del chat anterior.

**Qué vas a encontrar**

- [Objetivo](#objetivo)
- [Qué necesitas](#qué-necesitas)
- [Cómo invocar las acciones](#cómo-invocar-las-acciones)
- [El caso](#el-caso)
- [Trabajo con varios agentes](#trabajo-con-varios-agentes)
- [Pasos](#pasos)
- [Errores frecuentes](#errores-frecuentes)
- [Comprueba lo que has aprendido](#comprueba-lo-que-has-aprendido)
- [Solución o ejemplo resuelto](#solución-o-ejemplo-resuelto)
- [En tres frases](#en-tres-frases)
- [Siguiente paso](#siguiente-paso)

## Objetivo

Al terminar habrás:

- recorrido el flujo SDD de principio a fin;
- revisado cada artefacto antes de generar el siguiente;
- separado el qué del cómo;
- identificado tareas que pueden ejecutarse en paralelo;
- implementado y probado la primera versión;
- introducido un cambio empezando por la especificación.

## Qué necesitas

- La vía B del [ejercicio 00](00-preparacion-del-entorno.md).
- Git, Python 3.11 o superior y Spec Kit.
- Cualquier asistente compatible autorizado por tu organización.
- Entre 90 y 120 minutos, o dos sesiones.
- La [solución de referencia](soluciones/03-reserva-salas/README.md), que no debes abrir hasta terminar el análisis.

## Cómo invocar las acciones

En este documento no se usa la sintaxis propia de ninguna marca. Cada paso indica una acción de esta forma:

```text
Acción SDD: specify
```

Ejecuta la acción equivalente que ofrezca tu asistente. Puede aparecer como comando, *skill*, agente, menú o plantilla. Si la acción acepta el *prompt* en el mismo mensaje, pégalo junto; si no, ejecútala primero y pega el texto cuando te lo solicite.

Lo que se evalúa es el artefacto producido, no el prefijo del comando ni la carpeta de configuración del asistente.

## El caso

Ana, responsable de Oficina, quiere sustituir una hoja de cálculo usada para reservar 12 salas distribuidas en tres plantas.

La primera versión debe permitir:

- ver las salas con planta y aforo;
- consultar disponibilidad para una fecha y franja;
- reservar sin solapamientos;
- cancelar o modificar una reserva propia;
- marcar salas en mantenimiento con permisos de administración;
- enviar un comprobante por correo al confirmar, modificar o cancelar.

Reglas conocidas:

- horario de 08:00 a 20:00;
- duración máxima de 4 horas;
- antelación máxima inicial de 30 días;
- toda reserva tiene una persona responsable visible;
- no hay reservas recurrentes, calendario externo, catering ni control de asistencia en la primera versión.

## Trabajo con varios agentes

El flujo es secuencial en sus decisiones, pero no obliga a que lo haga todo el mismo agente.

| Rol | Recibe | Entrega |
|---|---|---|
| Especificador | Petición + constitución | `spec.md` |
| Revisor funcional | Constitución + spec | Preguntas y contradicciones |
| Planificador | Spec aprobada + constitución | `plan.md` |
| Revisor técnico | Spec + plan | Huecos entre requisitos y diseño |
| Generador de tareas | Spec + plan | `tasks.md` con dependencias |
| Implementadores | Tareas independientes | Código y pruebas |
| Validador | Todos los artefactos + resultado | Informe de conformidad |

**Regla:** se puede paralelizar la ejecución de tareas independientes, pero no planificar sobre una especificación que todavía no ha sido aprobada.

Si solo tienes un asistente, simula los roles con conversaciones nuevas. Pasa a cada una únicamente los artefactos que necesita.

## Pasos

### 0. Comprueba el entorno

```bash
specify version
specify check
```

Abre el proyecto con tu asistente y confirma que reconoce las acciones SDD.

- [ ] Spec Kit y el asistente están disponibles.

### 1. Crea el proyecto

```bash
specify init reserva-salas
cd reserva-salas
git init
git add -A
git commit -m "Preparar proyecto ReservaSalas"
```

Selecciona tu asistente cuando Spec Kit lo pregunte. No añadas al ejercicio ninguna clave, ruta o configuración específica.

Qué revisar:

- existe la infraestructura de Spec Kit;
- el asistente está abierto en la carpeta correcta;
- Git muestra un árbol limpio después del commit.

- [ ] El proyecto está creado y versionado.

### 2. Define la constitución

**Acción SDD: `constitution`**

**Prompt:**

```text
Crea la constitución de ReservaSalas, una aplicación interna para reservar 12 salas de reuniones. Redáctala en castellano y usa cinco principios:

1. Sencillez primero: se construye lo mínimo que resuelve el problema; cualquier complejidad adicional se justifica en el plan.
2. Accesible y en castellano: textos claros, uso con teclado y errores que expliquen qué ha ocurrido.
3. Pruebas antes de dar una historia por terminada: cada regla de negocio tiene una prueba automática.
4. Datos mínimos: solo nombre, correo corporativo, rol y datos necesarios de la reserva; se usa el acceso corporativo existente.
5. Trazabilidad: toda reserva tiene una persona responsable visible y los cambios relevantes quedan identificados.

Incluye cómo se gobiernan los cambios de la constitución y cómo se comprueba su cumplimiento en el plan.
```

Qué revisar:

- cada principio prohíbe o exige algo concreto;
- no contiene funcionalidades del producto;
- explica cómo se comprobará en el plan.

Haz commit.

- [ ] La constitución está aprobada y versionada.

### 3. Escribe la especificación

**Acción SDD: `specify`**

**Prompt:**

```text
Especifica ReservaSalas en castellano y sin decidir tecnología. Usa la petición y las reglas del caso de este ejercicio.

Historias prioritarias:
P1: consultar disponibilidad y reservar una sala.
P2: cancelar o modificar una reserva propia.
P3: ver las reservas propias y las reservas del día de cada sala.

Incluye criterios Dado/Cuando/Entonces, casos límite, requisitos EARS numerados, entidades, supuestos, fuera de alcance y cuatro criterios de éxito medibles. No inventes decisiones que no aparezcan en la petición: márcalas como aclaraciones.
```

Qué revisar antes de seguir:

- las historias están priorizadas y cada una puede probarse de forma independiente;
- no aparecen lenguajes, bases de datos, frameworks ni pantallas concretas;
- hay requisitos para listar salas, consultar disponibilidad, confirmar, evitar solapamientos, aplicar límites, mantenimiento, permisos, cancelar o modificar, correo y responsable visible;
- los criterios de éxito contienen cifras.

- [ ] La especificación describe el qué y el porqué, sin tecnología.

### 4. Cierra las aclaraciones

**Acción SDD: `clarify`**

Pide un máximo de cinco preguntas, de una en una, priorizando alcance, permisos, límites y datos. Para este ejercicio, las respuestas de Ana son:

1. Solo administración marca una sala en mantenimiento.
2. Solo administración puede modificar o cancelar una reserva ajena.
3. No hay excepciones al horario ni a la duración máxima.
4. El correo de comprobante es obligatorio al confirmar, modificar y cancelar.
5. La antelación máxima inicial es de 30 días.

Comprueba que cada respuesta se incorpora en la historia, requisito o caso límite afectado. No basta con guardarla en una lista separada.

- [ ] Las decisiones están escritas y propagadas a la spec.

### 5. Pasa una lista de verificación funcional

**Acción SDD: `checklist`**

**Prompt:**

```text
Crea una lista de verificación de requisitos para ReservaSalas. Comprueba: ausencia de tecnología en la spec; historias independientes; requisitos EARS comprobables; cobertura de límites, permisos y casos límite; criterios de éxito medibles; coherencia con la constitución; y ausencia de aclaraciones pendientes que bloqueen el plan.
```

Corrige la especificación hasta que no queden fallos bloqueantes. Un elemento sin marcar debe incluir una explicación y un responsable.

- [ ] La spec está lista para planificar.

### 6. Crea y revisa el plan técnico

**Acción SDD: `plan`**

**Prompt:**

```text
Crea un plan técnico pequeño para ReservaSalas. Usa una aplicación web monolítica en Python 3.12, FastAPI, plantillas HTML, SQLite y pytest. No añadas servicios externos salvo el servidor de correo corporativo ya disponible. Incluye arquitectura, modelo de datos, contratos internos, estrategia de pruebas, arranque local, riesgos y una comprobación principio por principio contra la constitución. Justifica cualquier complejidad que no sea imprescindible.
```

Esta tecnología es una decisión didáctica del ejercicio, no una configuración del asistente.

Revisión técnica:

- cada requisito tiene una respuesta en el plan;
- la constitución se comprueba punto por punto;
- no aparecen funciones fuera de alcance;
- el plan puede explicarse en pocos minutos.

- [ ] El plan cubre la spec y respeta la constitución.

### 7. Genera tareas pequeñas

**Acción SDD: `tasks`**

**Prompt:**

```text
Genera las tareas de ReservaSalas por fases e historias. Escribe primero las pruebas de cada regla. Cada tarea debe indicar el fichero o área afectada, el resultado observable y sus dependencias. Marca como paralelas solo las tareas que no modifican los mismos ficheros ni dependen de resultados pendientes. Mantén P1, P2 y P3 separadas.
```

Qué revisar:

- cada requisito aparece en al menos una tarea;
- las pruebas preceden a la implementación correspondiente;
- ninguna tarea mezcla varias historias;
- las tareas paralelas son realmente independientes.

- [ ] `tasks.md` tiene orden, dependencias y trazabilidad.

### 8. Analiza la coherencia

**Acción SDD: `analyze`**

Analiza constitución, spec, plan y tareas. No implementes todavía.

Clasifica los hallazgos:

- **Bloqueante:** contradicción, requisito sin cobertura o principio incumplido.
- **Importante:** ambigüedad que puede cambiar el resultado.
- **Mejora:** redacción o detalle no bloqueante.

Corrige el artefacto que originó el problema, no el informe. Repite el análisis hasta que no haya bloqueantes.

- [ ] El conjunto es coherente antes de generar código.

### 9. Implementa por fases

**Acción SDD: `implement`**

Empieza por la preparación y P1. Revisa el diff y ejecuta las pruebas antes de seguir con P2 y P3. Autoriza comandos e instalaciones solo después de leerlos.

Qué comprobar:

- las pruebas fallan antes de implementar la regla y pasan después;
- el código no añade funciones fuera de la spec;
- la aplicación puede arrancarse siguiendo el plan;
- cada historia puede demostrarse de forma independiente.

Haz commits por fase o por historia.

- [ ] La aplicación funciona y las pruebas pasan.

### 10. Comprueba la convergencia

**Acción SDD: `converge`**

Compara la implementación con los artefactos. Si faltan tareas o código, corrige desde la fuente adecuada y vuelve a implementar. No edites la spec para justificar a posteriori lo que haya hecho el código.

- [ ] La implementación cubre lo escrito y no añade alcance oculto.

### 11. Introduce un cambio desde la especificación

Ana cambia la antelación máxima de 30 a 60 días.

1. Modifica primero la spec y sus criterios afectados.
2. Haz commit del cambio funcional.
3. Revisa si el plan necesita ajuste.
4. Ejecuta `converge` para obtener las tareas que faltan.
5. Ejecuta `implement` y las pruebas.
6. Comprueba en Git que el cambio empezó por la spec.

- [ ] El historial muestra `spec → plan/tareas → pruebas/código`.

### 12. Cierra el ejercicio

Responde por escrito:

1. ¿Qué decisión importante quedó en la spec y no en el chat?
2. ¿Qué hallazgo del análisis evitó retrabajo?
3. ¿Qué tareas pudieron ejecutarse en paralelo y por qué?
4. ¿Qué habría sido más difícil si todo lo hubiera hecho una sola conversación?

- [ ] He documentado lo aprendido.

## Errores frecuentes

| Síntoma | Causa | Corrección |
|---|---|---|
| El ejercicio indica una clave o carpeta concreta del asistente | Se ha confundido la integración con el método | Usa la selección interactiva y valida acciones, no rutas |
| El plan empieza antes de cerrar aclaraciones | La spec todavía no es un contrato estable | Vuelve a `clarify` y aprueba la spec |
| `tasks.md` tiene tareas enormes | El plan se ha troceado por capas técnicas, no por resultados | Divide por historia, prueba y fichero |
| Se marcan como paralelas tareas que modifican lo mismo | El paralelismo es aparente | Añade dependencias o separa ficheros y responsabilidades |
| El código «funciona», pero no cumple una regla | Las pruebas cubren el happy path y no la spec | Añade la prueba de la regla y corrige la implementación |
| El cambio de 30 a 60 días se hace directamente en código | Se ha roto la trazabilidad | Deshaz el cambio y empieza por la spec |

## Comprueba lo que has aprendido

1. ¿Por qué no se valida el prefijo exacto de los comandos?
2. ¿Puede un agente planificar mientras otro sigue cambiando la spec?
3. ¿Qué artefacto se corrige si `analyze` detecta un requisito sin tarea?
4. ¿Cuándo pueden ejecutarse dos tareas en paralelo?
5. ¿En qué orden debe aparecer el cambio de 30 a 60 días en Git?

<details><summary>Ver respuestas</summary>

1. Porque la sintaxis depende del asistente; se validan la acción y el artefacto resultante.
2. No. Puede revisar, pero el plan debe partir de una spec aprobada.
3. `tasks.md`, salvo que el requisito sea incorrecto o el plan no lo contemple; entonces se corrige el artefacto donde nació el hueco.
4. Cuando no dependen entre sí ni compiten por los mismos ficheros o decisiones.
5. Spec primero; después, si hace falta, plan y tareas; finalmente pruebas y código.

</details>

## Solución o ejemplo resuelto

La [solución del ejercicio 03](soluciones/03-reserva-salas/README.md) sigue la estructura común de soluciones y enlaza la constitución, spec, aclaraciones, checklist, plan, tareas y el análisis de los pasos finales.

## En tres frases

1. Los artefactos permiten cambiar de persona o agente sin perder la intención.
2. Las decisiones se cierran en orden; la ejecución se paraleliza solo cuando las dependencias lo permiten.
3. Un cambio funcional empieza por la spec y termina en pruebas y código, nunca al revés.

## Siguiente paso

Haz la [Dinámica de equipo](04-dinamica-de-equipo-20-minutos.md) o pasa directamente al [Reto final](06-reto-final-tu-propio-proyecto.md).

---

⬅️ [Anterior: Requisitos EARS](02-practicar-requisitos-ears.md) · 🏠 [Índice](README.md) · ➡️ [Siguiente: Dinámica de equipo](04-dinamica-de-equipo-20-minutos.md)
