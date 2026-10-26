# Solución del ejercicio 05: reparar una especificación

> **Para quién:** quien haya terminado la revisión del ejercicio 05 · **Tiempo de lectura:** ~5 min, más la auditoría ampliada · **Nivel:** 🟡 intermedio

Esta portada explica cómo corregir el [ejercicio 05](../../05-arreglar-una-especificacion-mala.md). La [auditoría ampliada](../05-especificacion-arreglada.md) conserva todos los problemas encontrados y una versión corregida de las secciones principales.

## Mínimo esperado

El ejercicio está conseguido cuando has identificado y explicado **12 problemas relevantes**:

- al menos 2 de alcance o priorización;
- al menos 2 en requisitos;
- al menos 2 en criterios de éxito;
- al menos 2 contradicciones con la constitución;
- 4 adicionales que puedan cambiar lo que se construye.

Además debes:

- reescribir los requisitos afectados;
- reescribir los criterios de éxito afectados;
- anotar qué decisiones necesitan una aclaración de Ana;
- pasar la lista de verificación sobre lo corregido;
- explicar qué partes seguirían pendientes antes de planificar.

No es necesario encontrar los 46 matices de la auditoría ampliada.

## Criterios de corrección

| Tipo de problema | Ejemplo válido | No basta con… |
|---|---|---|
| Alcance | Estadísticas y catering aparecen antes que reservar | Decir «es demasiado grande» sin localizarlo |
| Prioridad | La primera historia no resuelve el problema principal | Cambiar números sin justificar el valor independiente |
| Requisito | Mezcla tecnología, es vago, doble o no tiene condición | Corregir solo la gramática |
| Criterio de éxito | No tiene cifra o mide un detalle técnico | Sustituir «rápido» por «muy rápido» |
| Constitución | Guarda datos de más o elimina pruebas obligatorias | Citar el principio sin explicar el choque |
| Aclaración | Falta decidir permisos, límites o excepciones | Inventar la respuesta |
| Coherencia | Dos secciones usan reglas o términos distintos | Señalar únicamente una errata |

Un mismo fragmento puede contener varios problemas, pero conviene contar como hallazgo cada decisión independiente que deba corregirse.

## Solución razonada

Una selección mínima de 12 problemas podría ser:

1. La spec está marcada «lista para implementar» aunque contiene aclaraciones pendientes.
2. El resumen fija React, Node.js, PostgreSQL y nube: tecnología dentro de la spec.
3. Parking y catering amplían el alcance sin necesidad.
4. «Ver estadísticas» aparece antes que la historia de reservar.
5. Las historias no tienen prioridad, motivo ni prueba independiente.
6. Los criterios «funciona bien» no son comprobables.
7. No hay casos límite relevantes.
8. Un requisito mezcla rapidez, intuición y facilidad de uso.
9. Otro requisito permite reservas anónimas, contra la trazabilidad de la constitución.
10. Un requisito se contradice al limitar a 4 horas y permitir reuniones de todo el día.
11. Los criterios de éxito «más contenta» y «menos choques» no contienen cifras.
12. La sección de datos personales guarda información innecesaria, contra «Datos mínimos».

### Requisitos corregidos: muestra mínima

```text
RF-001: El sistema deberá mostrar la lista de salas con su planta y aforo.

RF-002: CUANDO una persona indica una fecha y una franja horaria,
el sistema deberá mostrar qué salas están libres en esa franja.

RF-003: CUANDO una persona confirma una reserva válida,
el sistema deberá registrarla y mostrar una confirmación con sala, fecha y hora.

RF-004: SI la franja solicitada se solapa con otra reserva de la misma sala,
ENTONCES el sistema deberá rechazarla e indicar qué franja está ocupada.

RF-005: MIENTRAS una sala esté marcada en mantenimiento,
el sistema deberá impedir nuevas reservas en ella.

RF-006: DONDE la persona tenga permisos de administración,
el sistema deberá permitir marcar una sala en mantenimiento.
```

La corrección completa necesita también límites, cancelación o modificación, permisos sobre reservas ajenas, correo y responsable visible.

### Criterios de éxito corregidos

```text
CE-001: Reservar una sala lleva menos de 1 minuto.
CE-002: Existen cero reservas activas solapadas para una misma sala.
CE-003: El 90 % de las personas completa una reserva sin ayuda en su primer intento.
CE-004: La disponibilidad se muestra en menos de 2 segundos bajo la carga de prueba acordada.
```

La [auditoría ampliada](../05-especificacion-arreglada.md) explica el resto de problemas línea por línea y presenta una especificación corregida más completa.

## Alternativas válidas

- Elegir otros 12 problemas, siempre que cubran las categorías exigidas y afecten al resultado.
- Separar los límites de horario, duración y antelación en requisitos distintos.
- Usar cifras diferentes en los criterios de éxito si quien encarga las aprueba.
- Mantener alguna aclaración abierta y declarar que la spec todavía no está lista para planificar.
- Corregir primero solo las secciones que pide el ejercicio y dejar las historias completas como trabajo posterior, indicándolo en la checklist.

## Errores frecuentes

| Error | Corrección |
|---|---|
| Intentar encontrar todos los problemas del ejemplo ampliado | Detente al cubrir 12 hallazgos relevantes y reescribir lo esencial |
| Contar erratas como problemas funcionales | Prioriza decisiones que cambian alcance, reglas, datos o pruebas |
| Copiar la especificación canónica sin explicar el fallo | Relaciona cada corrección con el fragmento original |
| Dar por respondida una aclaración porque la solución la conoce | En una revisión real, la decisión corresponde a quien encarga |
| Marcar la checklist completa aunque las historias sigan mal | Deja los ítems pendientes con una nota honesta |

## En tres frases

1. Una buena revisión busca decisiones abiertas y contradicciones, no solo mala redacción.
2. Doce problemas relevantes enseñan más que una lista exhaustiva sin correcciones.
3. La spec solo está lista para el plan cuando los fallos bloqueantes y las aclaraciones importantes están cerrados.

## Volver al ejercicio

Vuelve a [Arreglar una especificación mala](../../05-arreglar-una-especificacion-mala.md) o continúa con el [Reto final](../../06-reto-final-tu-propio-proyecto.md).

---

🏠 [Índice de soluciones](../README.md)
