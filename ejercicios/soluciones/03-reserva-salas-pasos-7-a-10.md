# Solución del ejercicio 03: análisis, implementación, cambio y cierre

> **Para quién:** quien haya llegado a las últimas fases de ReservaSalas · **Tiempo de lectura:** ~10 min · **Nivel:** 🟡 intermedio

Este documento completa la [solución de ReservaSalas](03-reserva-salas/README.md) con las fases que no quedan representadas por un único artefacto estático: analizar la coherencia, implementar, introducir un cambio y cerrar el ejercicio.

Las acciones se nombran de forma neutral. Usa la forma equivalente que ofrezca tu asistente.

## Mínimo esperado

Al terminar estas fases debes tener:

- un análisis sin hallazgos bloqueantes;
- pruebas y código para P1, P2 y P3;
- una comprobación de convergencia entre artefactos e implementación;
- el cambio de antelación máxima de 30 a 60 días iniciado en la spec;
- un historial Git que muestre el orden de propagación;
- una reflexión final sobre decisiones, revisión y paralelismo.

## Criterios de corrección

| Fase | Correcto | Bloquea si… |
|---|---|---|
| Análisis | Detecta contradicciones y cobertura incompleta antes del código | Se ignoran requisitos sin plan o sin tarea |
| Implementación | Las pruebas cubren reglas y errores | Solo se prueba el camino feliz |
| Convergencia | Compara código, pruebas y artefactos | Se da por bueno porque la aplicación «parece funcionar» |
| Cambio | Empieza en la spec y se propaga | Se cambia primero una constante del código |
| Cierre | Explica evidencias y límites | Solo afirma que todo ha ido bien |

## Solución razonada

### 1. Analizar la coherencia

**Acción SDD: `analyze`**

El análisis recibe constitución, spec, plan y tareas. Debe buscar como mínimo:

- requisitos sin cobertura en el plan;
- requisitos sin prueba o tarea;
- decisiones del plan que contradigan la constitución;
- límites distintos entre artefactos;
- tareas fuera de alcance;
- términos usados con significados diferentes.

Un informe razonable puede contener hallazgos como estos:

```text
IMPORTANTE · RF-011 exige un correo al modificar y cancelar, pero tasks.md solo contempla el envío al confirmar.
Corrección: añadir las pruebas y tareas correspondientes antes de implementar P2.

MEJORA · La spec usa «administración» y el plan «rol admin».
Corrección: unificar el término para evitar permisos distintos por interpretación.
```

La corrección se realiza en el artefacto donde nace el problema. El informe no sustituye el cambio.

Repite el análisis hasta que no queden hallazgos bloqueantes. Los elementos de mejora pueden aceptarse si se documenta el motivo.

### 2. Implementar por incrementos

**Acción SDD: `implement`**

El orden recomendado es:

1. preparación del proyecto;
2. modelo y utilidades compartidas;
3. pruebas de P1;
4. implementación de P1;
5. pruebas e implementación de P2;
6. pruebas e implementación de P3;
7. pruebas de integración y arranque local.

Después de cada incremento:

- revisa el diff;
- ejecuta las pruebas;
- prueba manualmente la historia;
- comprueba que no ha aparecido alcance nuevo;
- crea un commit que describa el resultado.

No se considera suficiente que el asistente diga que las pruebas pasan. Debes ver la ejecución y su resultado.

### 3. Comprobar la convergencia

**Acción SDD: `converge`**

La convergencia compara lo construido con lo decidido. Un resultado útil debe responder:

- ¿todos los requisitos tienen implementación?
- ¿todas las reglas tienen pruebas?
- ¿hay código que no corresponde a ningún requisito?
- ¿los límites y permisos coinciden con la spec?
- ¿las tareas están realmente terminadas?

Si aparecen huecos, no los corrijas siempre en código. Decide su origen:

- comportamiento incorrecto o ausente → pruebas y código;
- tarea olvidada → `tasks.md`;
- diseño insuficiente → `plan.md`;
- decisión funcional equivocada o ambigua → `spec.md` y, si hace falta, aclaraciones.

### 4. Introducir el cambio de 30 a 60 días

Ana pide ampliar la antelación máxima.

#### Paso 1: cambiar la spec

Actualiza el requisito y cualquier criterio o caso límite que cite 30 días. Haz un commit independiente, por ejemplo:

```text
Ampliar a 60 días la antelación máxima en la especificación
```

#### Paso 2: revisar el plan

Si el plan no contiene ninguna decisión técnica dependiente del valor 30, basta con dejar constancia de que se ha revisado. Si lo duplica en contratos, datos de prueba o configuración, actualízalo.

#### Paso 3: obtener el trabajo pendiente

**Acción SDD: `converge`**

El resultado debería identificar, como mínimo:

- prueba del límite superior actualizada;
- datos de prueba ajustados;
- implementación de la regla actualizada;
- documentación o ejemplos afectados.

#### Paso 4: implementar y probar

**Acción SDD: `implement`**

Comprueba estos tres casos:

- 60 días: se acepta si el resto de reglas se cumple;
- 61 días: se rechaza;
- una reserva válida anterior: sigue funcionando.

El historial debe mostrar el cambio funcional antes que el cambio de código.

### 5. Reflexión final

Una respuesta razonable podría ser:

- **Decisión importante escrita:** quién puede modificar reservas ajenas quedó en la spec y no dependió del contexto de una conversación.
- **Hallazgo que evitó retrabajo:** el análisis detectó que faltaban tareas para los correos de modificación y cancelación antes de implementar P2.
- **Paralelismo seguro:** las pruebas de accesibilidad y la preparación del correo simulado podían avanzar a la vez porque no dependían de la misma implementación.
- **Límite observado:** algunas tareas eran demasiado grandes y hubo que dividirlas por regla y fichero.
- **Cambio trazable:** la ampliación a 60 días se propagó desde la spec hasta las pruebas y el código.

## Alternativas válidas

- Implementar P1 en una primera sesión y P2/P3 en otra.
- Utilizar varios agentes para tareas independientes o uno solo con conversaciones separadas.
- Mantener un hallazgo de mejora abierto si no afecta a la corrección y tiene responsable.
- Actualizar el plan durante el cambio o simplemente registrar que se revisó y no necesitaba cambios.
- Usar mensajes de commit diferentes, siempre que el orden sea visible.

## Errores frecuentes

| Error | Corrección |
|---|---|
| Ejecutar la implementación antes del análisis | Vuelve a comprobar artefactos y corrige inconsistencias antes de seguir |
| Aceptar un informe sin modificar el artefacto origen | Aplica cada corrección donde corresponde y repite el análisis |
| Marcar tareas terminadas sin ver pruebas | Ejecuta la suite y guarda evidencia del resultado |
| Cambiar 30 por 60 solo en código | Deshaz el cambio y empieza por la spec |
| Pedir al asistente que «arregle todo» sin revisar el diff | Implementa por fases y valida cada incremento |
| Considerar paralelas tareas que editan la misma regla | Añade la dependencia o reparte responsabilidades de forma real |

## En tres frases

1. Analizar antes de implementar convierte contradicciones baratas de corregir en decisiones explícitas.
2. La convergencia no es «las pruebas están verdes»: es la correspondencia entre lo pedido, lo planeado, lo asignado y lo construido.
3. El cambio de 30 a 60 días demuestra la trazabilidad cuando empieza en la spec y termina en pruebas y código.

## Volver al ejercicio

Vuelve al [ejercicio 03](../03-reserva-salas-paso-a-paso.md) o a la [portada de su solución](03-reserva-salas/README.md).

---

🏠 [Índice de soluciones](README.md)
