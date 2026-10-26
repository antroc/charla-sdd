# Solución del ejercicio 06: reto final

> **Para quién:** quien haya terminado un proyecto propio con SDD · **Tiempo de lectura:** ~8 min, más los artefactos del ejemplo · **Nivel:** 🔴 avanzado

El [ejercicio 06](../../06-reto-final-tu-propio-proyecto.md) no tiene una única respuesta correcta. Esta solución proporciona un mínimo común para evaluarlo, un proyecto completo de préstamo de portátiles y puntos de partida para otras ideas.

La solución no depende de un asistente ni de una integración concreta. Puedes comparar un proyecto creado con Codex, Claude Code, GitHub Copilot, Cursor u otra herramienta siempre que produzca artefactos y evidencias equivalentes.

## Mínimo esperado

La entrega debe contener:

- una petición breve y aprobada;
- una constitución de tres a cinco principios;
- una sola historia P1 completa;
- entre cuatro y seis requisitos;
- entre dos y tres criterios de éxito;
- entre tres y cinco aclaraciones aplicadas;
- una lista de verificación sin bloqueantes;
- un plan pequeño que respete la constitución;
- tareas con pruebas, dependencias y paralelismo justificado;
- un análisis de coherencia sin bloqueantes;
- código y pruebas para la P1;
- un cambio funcional iniciado en la spec;
- una autoevaluación honesta.

No es obligatorio reproducir el tamaño del ejemplo de préstamo de portátiles. Ese proyecto es deliberadamente más completo para mostrar cómo pueden evolucionar los artefactos.

## Criterios de corrección

| Área | Debe demostrar | Bloquea si… |
|---|---|---|
| Alcance | La P1 aporta valor y cabe en el ejercicio | Hay varias historias imprescindibles mezcladas |
| Petición | Explica problema, perfiles, límites y fuera de alcance | Ya contiene arquitectura o herramientas |
| Constitución | Sus principios cambian decisiones | Solo contiene valores genéricos |
| Spec | Requisitos comprobables y criterios medibles | Depende de información no escrita |
| Aclaraciones | Cierran reglas reales y se propagan | Permanecen solo en la conversación |
| Plan | Responde a la spec y justifica la tecnología | Copia una solución sin relacionarla con requisitos |
| Tareas | Son pequeñas, ordenadas y trazables | Faltan pruebas o requisitos sin cobertura |
| Implementación | La P1 funciona y las pruebas pasan | Solo hay una demo manual sin evidencia |
| Cambio | El historial empieza en la spec | Se modifica directamente el código |
| Revisión | Otra persona puede validar qué se pidió y cómo se construyó | La entrega solo se entiende leyendo el código |

No se penaliza usar una tecnología distinta, otra estructura de repositorio o una redacción diferente si todo está justificado y es coherente.

## Solución razonada

### Ejemplo completo: préstamo de portátiles

Abre [Préstamo de portátiles](prestamo-de-portatiles/README.md). El ejemplo incluye:

- [peticion.md](prestamo-de-portatiles/peticion.md)
- [constitution.md](prestamo-de-portatiles/constitution.md)
- [spec.md](prestamo-de-portatiles/spec.md)
- [plan.md](prestamo-de-portatiles/plan.md)
- [tasks.md](prestamo-de-portatiles/tasks.md)
- [autoevaluacion.md](prestamo-de-portatiles/autoevaluacion.md)

El proyecto parte de un cuaderno donde Oficina apunta préstamos. Su P1 permite consultar disponibilidad y solicitar un equipo para unas fechas. Las siguientes iteraciones cubren entrega, devolución, prórroga y avisos.

Al comparar tu proyecto, observa especialmente:

1. cómo la petición recorta el problema;
2. qué prohíbe cada principio de la constitución;
3. cómo las aclaraciones fijan límites y permisos;
4. cómo cada requisito aparece en el plan y en las tareas;
5. qué tareas pueden ejecutarse en paralelo;
6. cómo la autoevaluación reconoce lo que falta.

### Otras ideas

[Otras ideas](otras-ideas.md) ofrece un punto de partida para buzón de sugerencias, días en la oficina, vacaciones, incidencias, cursos, turnos y horas por proyecto.

Estos esqueletos sirven para comparar el recorte de alcance y las primeras decisiones. No son especificaciones listas para implementar: debes completar aclaraciones, criterios, plan y pruebas según tu caso.

### Evidencia del cambio desde la spec

Una entrega completa debería mostrar en Git una secuencia semejante a:

```text
Cambiar la regla en spec.md
Actualizar plan o tareas si corresponde
Añadir o modificar la prueba
Actualizar la implementación
```

Los mensajes exactos no importan. Sí importa que el cambio funcional se decida antes de tocar el código.

## Alternativas válidas

- Elegir cualquiera de las ideas propuestas o un problema propio de tamaño similar.
- Usar una tecnología diferente a la del ejemplo.
- Guardar las aclaraciones dentro de la spec o en un fichero separado.
- Hacer la revisión mediante pull request, revisión interna del repositorio o sesión conjunta documentada.
- Implementar las tareas con un solo agente, con conversaciones separadas o con varios agentes especializados.
- Obtener una puntuación menor en la rúbrica si la autoevaluación explica con precisión qué falta y por qué.

## Errores frecuentes

| Error | Corrección |
|---|---|
| Comparar número de ficheros o líneas con el ejemplo | Compara cobertura, claridad y trazabilidad |
| Copiar la tecnología del ejemplo sin conocerla | Elige una solución sencilla que puedas probar y justificar |
| Convertir cada idea futura en una historia de la primera entrega | Mantén una sola P1 y mueve el resto fuera de alcance |
| Incluir instrucciones propias de un asistente en los artefactos | Documenta acciones SDD y resultados, no configuración local |
| Presentar código sin petición ni spec | Completa primero la cadena de decisiones |
| Autoevaluarse con puntuación máxima sin evidencias | Cita artefactos, pruebas, commits y revisiones concretas |

## En tres frases

1. El reto se aprueba cerrando un ciclo pequeño y trazable, no construyendo el proyecto más grande.
2. La tecnología y el asistente pueden variar; los contratos entre petición, spec, plan, tareas y pruebas siguen siendo revisables.
3. El ejemplo ampliado ayuda a comparar decisiones, pero el mínimo esperado es mucho más pequeño.

## Volver al ejercicio

Vuelve al [Reto final: tu propio proyecto](../../06-reto-final-tu-propio-proyecto.md) o al [índice de ejercicios](../../README.md).

---

🏠 [Índice de soluciones](../README.md)
