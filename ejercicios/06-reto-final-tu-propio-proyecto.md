# Ejercicio 06: reto final, tu propio proyecto

> **Para quién:** quien haya terminado el ejercicio 03 y quiera aplicar SDD a un problema propio · **Tiempo de lectura:** ~10 min · **Tiempo para hacerlo:** 60-90 min · **Nivel:** 🔴 avanzado

Hasta ahora has trabajado con casos preparados. En este reto elegirás una necesidad pequeña de tu entorno y recorrerás el flujo completo sin que el ejercicio tome las decisiones por ti.

El reto no depende de Codex, Claude Code, GitHub Copilot, Cursor ni de ningún otro asistente concreto. Se evalúan los artefactos, las decisiones y el resultado, no la sintaxis de los comandos ni la carpeta de configuración de la herramienta.

**Qué vas a encontrar**

- [Objetivo](#objetivo)
- [Qué necesitas](#qué-necesitas)
- [Cómo invocar las acciones](#cómo-invocar-las-acciones)
- [Ideas de proyecto](#ideas-de-proyecto)
- [Pasos](#pasos)
- [Lista de entrega](#lista-de-entrega)
- [Rúbrica de autoevaluación](#rúbrica-de-autoevaluación)
- [Errores frecuentes](#errores-frecuentes)
- [Comprueba lo que has aprendido](#comprueba-lo-que-has-aprendido)
- [Solución o ejemplo resuelto](#solución-o-ejemplo-resuelto)
- [En tres frases](#en-tres-frases)
- [Siguiente paso](#siguiente-paso)

## Objetivo

Al terminar habrás llevado una historia P1 desde la petición inicial hasta una implementación probada. También habrás introducido un cambio funcional empezando por la especificación y podrás explicar qué decidió cada artefacto.

El tamaño recomendado es deliberadamente pequeño:

- una P1 completa;
- entre cuatro y seis requisitos;
- entre dos y tres criterios de éxito;
- entre tres y cinco aclaraciones;
- un plan que pueda revisarse en pocos minutos;
- tareas pequeñas con dependencias visibles;
- pruebas y código solo para la P1;
- un cambio posterior trazable.

## Qué necesitas

- La vía B del [ejercicio 00](00-preparacion-del-entorno.md).
- Haber terminado [ReservaSalas paso a paso](03-reserva-salas-paso-a-paso.md).
- Git, Spec Kit y cualquier asistente compatible autorizado por tu organización.
- Una persona que conozca el problema y pueda responder a las aclaraciones. Si no la tienes, puedes representar ambos papeles, pero cada decisión debe escribirse antes de utilizarla.
- Datos ficticios. El problema puede ser real; los nombres, correos, cifras sensibles y documentos no.

## Cómo invocar las acciones

Cuando veas una indicación como:

```text
Acción SDD: plan
```

usa la acción equivalente de tu asistente. Puede aparecer como comando, *skill*, agente, menú o plantilla. Si no existe, utiliza la plantilla correspondiente de [ejercicios/plantillas](plantillas/README.md) y pide al asistente que la complete.

No copies al proyecto claves de integración, rutas internas ni instrucciones específicas de una marca. Estas configuraciones cambian entre herramientas y no forman parte del aprendizaje.

## Ideas de proyecto

Elige una necesidad cuya P1 pueda construirse y probarse durante el ejercicio.

| Idea | Posible P1 | Qué dejar fuera al principio |
|---|---|---|
| Préstamo de portátiles | Consultar disponibilidad y solicitar un equipo para unas fechas | Prórrogas, avisos y compras |
| Buzón de sugerencias | Registrar una sugerencia y verla publicada | Votos, moderación y estadísticas |
| Días en la oficina | Indicar un día de asistencia sin superar el aforo | Informes mensuales e integración con calendarios |
| Vacaciones | Registrar una solicitud pendiente | Aprobación, cancelación e informes de RRHH |
| Incidencias de oficina | Registrar una incidencia con responsable visible | Escalados, SLA e informes |
| Cursos internos | Consultar cursos y solicitar una plaza | Lista de espera, certificados y recordatorios |
| Turnos de guardia | Publicar el calendario de un mes desde una rotación fija | Intercambios, festivos y vacaciones |
| Horas por proyecto | Registrar horas de una semana abierta | Aprobación y cierre mensual |

También puedes usar una de las tarjetas del [ejercicio 04](04-dinamica-de-equipo-20-minutos.md). Si eliges un problema propio, debe poder explicarse en cinco o seis frases y tener una P1 independiente.

## Pasos

### 1. Escribe la petición

Crea `peticion.md` con esta estructura:

```markdown
# Petición: [nombre breve]

Lo pide: [rol ficticio].

Hoy [cómo se trabaja y qué problema provoca].
Lo usarán [perfiles].
La primera versión debe permitir [resultado de la P1].
Límites conocidos: [cantidades, plazos o permisos ya decididos].
Queda fuera: [funciones que no entran en esta entrega].
```

Pide a la persona que conoce el problema que lo lea. Si haces los dos papeles, escribe sus decisiones en el documento antes de seguir.

- [ ] La petición ocupa como máximo media página, no contiene tecnología y acota una P1.

### 2. Crea y versiona el proyecto

```bash
specify init nombre-del-proyecto
cd nombre-del-proyecto
git init
git add -A
git commit -m "Preparar proyecto SDD"
git switch -c reto-sdd
```

Selecciona tu asistente cuando Spec Kit lo pregunte. Si tu versión de Git no admite `git switch`, utiliza `git checkout -b reto-sdd`.

- [ ] El proyecto existe, el asistente está abierto en su carpeta y Git está limpio.

### 3. Define una constitución breve

**Acción SDD: `constitution`**

Crea entre tres y cinco principios. Como mínimo:

1. **Sencillez:** solo se construye la P1; cualquier complejidad adicional se justifica.
2. **Datos mínimos:** se guardan únicamente los datos necesarios para el caso.
3. **Pruebas:** cada regla de negocio tiene una prueba automática.
4. **Principio propio del problema:** una regla que realmente prohíba o exija algo, por ejemplo «ningún equipo puede tener dos préstamos activos».

Comprueba que cada principio sirve para rechazar alguna decisión posible. Si no cambia ninguna decisión, es una frase decorativa.

- [ ] La constitución tiene entre tres y cinco principios concretos.

### 4. Especifica solo la P1

**Acción SDD: `specify`**

Pasa la petición y la constitución. Pide:

- una historia P1 con prueba independiente;
- entre dos y cuatro criterios Dado/Cuando/Entonces;
- entre tres y cinco casos límite;
- entre cuatro y seis requisitos EARS;
- entre dos y tres criterios de éxito medibles;
- entidades mínimas;
- supuestos y fuera de alcance;
- marcadores de aclaración donde falten decisiones.

Rechaza cualquier tecnología concreta en la spec. También rechaza historias adicionales salvo que queden explícitamente como futuras iteraciones.

- [ ] La spec cubre una sola P1 y puede revisarse en menos de diez minutos.

### 5. Cierra las aclaraciones

**Acción SDD: `clarify`**

Pide entre tres y cinco preguntas, de una en una, sobre reglas que puedan cambiar el resultado. Da prioridad a:

- límites y plazos;
- roles y permisos;
- estados y transiciones;
- datos imprescindibles;
- qué ocurre en errores o casos límite.

Registra cada respuesta y aplícala a la sección afectada. No mantengas decisiones importantes solo en el chat.

- [ ] No quedan aclaraciones bloqueantes y cada respuesta ha modificado la spec cuando correspondía.

### 6. Comprueba la calidad funcional

**Acción SDD: `checklist`**

Revisa que:

- la P1 aporta valor por sí sola;
- los requisitos son comprobables y no incluyen tecnología;
- los casos límite tienen respuesta;
- los criterios contienen cifras;
- el alcance está acotado;
- la spec respeta la constitución.

Corrige todos los fallos bloqueantes antes de planificar.

- [ ] La spec está aprobada para el plan.

### 7. Crea un plan pequeño

**Acción SDD: `plan`**

Elige una tecnología que conozcas y mantenla deliberadamente sencilla. Pide al plan:

- contexto técnico;
- arquitectura y estructura del proyecto;
- modelo de datos;
- interfaces o contratos necesarios;
- estrategia de pruebas;
- arranque local;
- riesgos;
- comprobación principio por principio contra la constitución;
- registro de cualquier complejidad excepcional.

La tecnología es una decisión del proyecto, no una configuración del asistente. El mismo ejercicio puede resolverse con lenguajes y frameworks distintos.

- [ ] El plan cubre todos los requisitos sin añadir funciones.

### 8. Genera tareas y analiza la coherencia

**Acción SDD: `tasks`**

Pide tareas pequeñas, con resultado observable, fichero o área afectada y dependencias. Las pruebas deben aparecer antes de la implementación de cada regla. Marca como paralelas solo las tareas que no dependen entre sí ni modifican los mismos ficheros.

Después ejecuta:

**Acción SDD: `analyze`**

Corrige contradicciones, requisitos sin cobertura y tareas que no correspondan a la P1. Repite hasta que no haya fallos bloqueantes.

- [ ] Cada requisito tiene prueba y tarea; el análisis no muestra bloqueantes.

### 9. Implementa y prueba

**Acción SDD: `implement`**

Implementa por fases. Revisa cada diff antes de aceptarlo y ejecuta las pruebas. No autorices instalaciones ni comandos que no entiendas.

Criterios de cierre:

- la P1 puede demostrarse de principio a fin;
- todas las pruebas pasan;
- no hay funciones fuera de alcance;
- una persona distinta puede arrancar el proyecto siguiendo el plan.

- [ ] La P1 funciona y está probada.

### 10. Introduce un cambio desde la spec

Pide a quien encarga un cambio pequeño que afecte a una regla: un límite, un plazo, un permiso o un estado. No vale corregir una errata ni cambiar un color.

Sigue este orden:

1. Cambia la especificación y sus criterios afectados.
2. Haz commit.
3. Ajusta el plan si cambia el diseño.
4. Ejecuta **Acción SDD: `converge`** para detectar trabajo pendiente.
5. Ejecuta **Acción SDD: `implement`** y las pruebas.
6. Comprueba el historial.

- [ ] Git muestra que el cambio empezó en la spec y terminó en pruebas y código.

### 11. Autoevalúa y comparte

Crea `autoevaluacion.md` con:

- puntuación de la rúbrica;
- una decisión que salió bien;
- una aclaración que cambió la spec;
- una incidencia detectada antes de implementar;
- tres cosas que mejorarías;
- enlaces a petición, constitución, spec, plan y tareas.

Comparte el resultado mediante una pull request o una revisión equivalente en el repositorio de tu equipo. Pide dos revisiones distintas:

- funcional: «¿esto es lo que pedí?»;
- técnica: «¿el plan, las pruebas y el historial respetan los artefactos?».

- [ ] El trabajo puede revisarse sin abrir primero el código.

## Lista de entrega

- [ ] `peticion.md`
- [ ] constitución
- [ ] especificación de una P1
- [ ] aclaraciones aplicadas
- [ ] lista de verificación
- [ ] plan técnico
- [ ] tareas
- [ ] informe de análisis sin bloqueantes
- [ ] código y pruebas
- [ ] cambio iniciado en la spec
- [ ] `autoevaluacion.md`

## Rúbrica de autoevaluación

Puntúa cada criterio de 1 a 4.

| Criterio | 1 | 2 | 3 | 4 |
|---|---|---|---|---|
| Alcance | La P1 sigue siendo demasiado grande | Hay recorte, pero quedan funciones mezcladas | Una P1 clara y revisable | Además, el fuera de alcance evita ampliaciones concretas |
| Especificación | Ambigua o con tecnología | Parcialmente comprobable | Requisitos claros y criterios medibles | Otra persona la valida sin preguntas nuevas bloqueantes |
| Coherencia | Artefactos contradictorios | Hay huecos conocidos | Análisis limpio antes de implementar | Trazabilidad completa requisito → prueba → tarea → código |
| Pruebas | Manuales o posteriores | Cubren solo el camino feliz | Cubren reglas y errores de la P1 | Otra persona puede reproducirlas siguiendo el plan |
| Constitución | Genérica o decorativa | Algunos principios influyen | El plan la comprueba punto por punto | Hay una decisión rechazada explícitamente gracias a ella |

Un resultado de 15 puntos o más indica que el ciclo está bien cerrado. La puntuación no mide la cantidad de código.

## Errores frecuentes

| Síntoma | Causa | Corrección |
|---|---|---|
| La spec tiene varias P1 | No se ha elegido un resultado mínimo | Quédate con una sola historia y mueve el resto fuera de alcance |
| Se copia la tecnología de ReservaSalas | Se confunde ejemplo con requisito | Elige una solución que conozcas y justifícala en tu plan |
| El ejercicio depende de una clave o carpeta del asistente | Se ha documentado la integración, no el método | Sustituye esa referencia por la acción SDD y el artefacto esperado |
| `tasks.md` parece un índice de capas técnicas | No está organizado por resultados | Agrupa por preparación, pruebas y P1 |
| El cambio se hace directamente en código | Se ha roto la trazabilidad | Deshazlo y comienza por la spec |
| La autoevaluación solo dice que «todo ha ido bien» | No sirve para aprender ni revisar | Añade evidencias y límites concretos |

## Comprueba lo que has aprendido

1. ¿Qué tamaño debe tener la primera entrega?
2. ¿Dónde se decide la tecnología?
3. ¿Qué diferencia una tarea paralela de una tarea independiente solo en apariencia?
4. ¿Qué dos tipos de revisión necesita la entrega?
5. ¿Qué demuestra el historial del cambio final?

<details><summary>Ver respuestas</summary>

1. Una P1 completa, con cuatro a seis requisitos y sus pruebas.
2. En el plan técnico, después de aprobar la spec.
3. Una tarea paralela real no depende de resultados pendientes ni modifica las mismas áreas que otra.
4. Una revisión funcional y otra técnica.
5. Que el cambio se dirigió desde la especificación y se propagó de forma trazable.

</details>

## Solución o ejemplo resuelto

La [solución del ejercicio 06](soluciones/06-reto-final/README.md) usa el préstamo de portátiles como ejemplo completo y ofrece puntos de partida para otras ideas. No es una plantilla obligatoria ni fija la tecnología que debes usar.

## En tres frases

1. El reto consiste en cerrar un ciclo pequeño, no en construir una aplicación grande.
2. Las herramientas pueden cambiar; los artefactos, el orden de decisiones y los criterios de revisión permanecen.
3. El resultado se demuestra con trazabilidad, pruebas y revisión de otra persona.

## Siguiente paso

Revisa tu pull request con la rúbrica y compara después con las [soluciones](soluciones/README.md).

---

⬅️ [Anterior: Arreglar una especificación mala](05-arreglar-una-especificacion-mala.md) · 🏠 [Índice de ejercicios](README.md)
