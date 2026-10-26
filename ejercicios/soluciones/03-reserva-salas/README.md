# Solución del ejercicio 03: ReservaSalas

> **Para quién:** quien haya recorrido el flujo completo del ejercicio 03 · **Tiempo de lectura:** ~10 min, más los artefactos · **Nivel:** 🟡 intermedio

Esta solución reúne los artefactos de referencia de [ReservaSalas paso a paso](../../03-reserva-salas-paso-a-paso.md). Se generaron siguiendo las acciones SDD en orden; no dependen de la sintaxis, las carpetas ni la configuración de un asistente concreto.

## Mínimo esperado

El ejercicio está bien resuelto si incluye:

- una constitución con cinco principios aplicables;
- una especificación sin tecnología, con P1-P3, requisitos, casos límite y criterios medibles;
- las aclaraciones aplicadas a la spec;
- una lista de verificación sin fallos bloqueantes;
- un plan que cubra los requisitos y compruebe la constitución;
- tareas pequeñas, trazables y con paralelismo justificado;
- un análisis sin contradicciones bloqueantes;
- una implementación con pruebas;
- el cambio de antelación de 30 a 60 días iniciado en la spec;
- una reflexión final.

No se exige que el texto coincida literalmente con estos ficheros ni que se haya utilizado el mismo asistente.

## Criterios de corrección

| Artefacto | Debe demostrar | Bloquea si… |
|---|---|---|
| Constitución | Sus principios cambian decisiones del plan | Son frases genéricas sin efecto práctico |
| Spec | Define comportamiento y alcance, sin tecnología | Mezcla frameworks, base de datos o diseño técnico |
| Aclaraciones | Cierran decisiones y modifican la spec | Quedan solo en el chat o en una lista desconectada |
| Checklist | Revisa contenido y completitud | Se marca todo sin evidencia o deja fallos bloqueantes |
| Plan | Cubre cada requisito y respeta la constitución | Añade funciones o no explica las desviaciones |
| Tareas | Tienen orden, prueba, resultado y dependencias | Hay requisitos sin tarea o paralelismo falso |
| Implementación | Las pruebas cubren reglas y errores | Solo funciona el camino feliz |
| Cambio | Sigue spec → plan/tareas → pruebas/código | Se edita primero el código |

No se penaliza una arquitectura distinta si el plan la justifica y cumple la misma especificación. En este ejercicio concreto, la tecnología propuesta sirve para comparar resultados, no para configurar el asistente.

## Solución razonada

Lee los artefactos en este orden:

1. [constitution.md](constitution.md): reglas permanentes del proyecto.
2. [spec.md](spec.md): historias, casos límite, requisitos y criterios de éxito.
3. [aclaraciones.md](aclaraciones.md): preguntas que cerraron decisiones del negocio.
4. [checklist.md](checklist.md): comprobación funcional antes del plan.
5. [plan.md](plan.md): arquitectura, datos, pruebas y contraste con la constitución.
6. [tasks.md](tasks.md): orden de implementación y dependencias.
7. [Pasos 7 a 10](../03-reserva-salas-pasos-7-a-10.md): análisis, implementación, cambio de 30 a 60 días y reflexión.

### Correspondencia entre acciones y resultados

| Acción SDD | Resultado de referencia |
|---|---|
| `constitution` | [constitution.md](constitution.md) |
| `specify` | Primera versión de [spec.md](spec.md) |
| `clarify` | [aclaraciones.md](aclaraciones.md) y cambios en la spec |
| `checklist` | [checklist.md](checklist.md) |
| `plan` | [plan.md](plan.md) |
| `tasks` | [tasks.md](tasks.md) |
| `analyze` | Informe descrito en [Pasos 7 a 10](../03-reserva-salas-pasos-7-a-10.md) |
| `implement` | Código y pruebas generados en el proyecto de quien realiza el ejercicio |
| `converge` | Detección de trabajo pendiente tras cambios o implementación |

El código no se conserva como solución canónica porque distintos asistentes y decisiones técnicas pueden producir implementaciones correctas diferentes. Los documentos son la referencia común.

### Decisiones importantes del ejemplo

- Una reserva solapada se rechaza, no se limita a mostrar un aviso.
- Una sala en mantenimiento no admite nuevas reservas.
- Solo administración puede gestionar mantenimiento o reservas ajenas.
- El horario es 08:00-20:00 y la duración máxima, 4 horas, sin excepciones.
- El correo sirve como comprobante al confirmar, modificar o cancelar.
- Toda reserva muestra su responsable.
- El cambio posterior amplía la antelación máxima de 30 a 60 días.

## Alternativas válidas

- Separar un requisito compuesto en varios requisitos más atómicos.
- Usar otra arquitectura, lenguaje o almacenamiento si el plan lo justifica y mantiene los criterios de éxito.
- Organizar tareas por historia o por incrementos verticales, siempre que la trazabilidad sea visible.
- Guardar las aclaraciones dentro de `spec.md` en vez de un fichero separado. Aquí se separan para enseñar el proceso.
- Implementar tareas independientes con varios agentes o con uno solo en conversaciones distintas.
- Usar una estrategia de correo simulada en local, siempre que el plan explique cómo se prueba el comportamiento observable.

## Errores frecuentes

| Error | Corrección |
|---|---|
| Copiar una clave de integración o una ruta del asistente | Selecciona tu herramienta localmente y mantén los artefactos neutrales |
| Tratar estos ficheros como una salida literal obligatoria | Compara cobertura, coherencia y trazabilidad |
| Leer las aclaraciones pero no comprobar la spec final | Verifica que cada respuesta cambió el requisito afectado |
| Marcar tareas paralelas por estar en fases distintas | Comprueba dependencias y ficheros compartidos |
| Reproducir la tecnología sin entenderla | Usa el plan del ejercicio o justifica una alternativa que conozcas |
| Cambiar el límite directamente en una constante | Empieza por la spec y deja rastro en Git |

## En tres frases

1. La solución de referencia son los artefactos coherentes entre sí, no una conversación ni una herramienta concreta.
2. Cada documento recibe decisiones cerradas y entrega un contrato revisable para el siguiente paso.
3. La implementación puede variar, pero debe cubrir la misma spec y demostrarlo con pruebas.

## Volver al ejercicio

Vuelve a [ReservaSalas paso a paso](../../03-reserva-salas-paso-a-paso.md) o continúa con el [Reto final](../../06-reto-final-tu-propio-proyecto.md).

---

🏠 [Índice de soluciones](../README.md)
