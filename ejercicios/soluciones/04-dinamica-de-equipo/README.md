# Solución del ejercicio 04: dinámica de equipo

> **Para quién:** participantes y facilitadores de la dinámica · **Tiempo de lectura:** ~5 min, más las tarjetas resueltas · **Nivel:** 🟢 básico

Esta portada explica cómo evaluar el [ejercicio 04](../../04-dinamica-de-equipo-20-minutos.md). El desarrollo completo de las seis tarjetas está en [Dinámica de equipo resuelta](../04-dinamica-de-equipo-resuelta.md).

## Mínimo esperado

Cada grupo debe entregar, para su tarjeta:

- una historia P1 que resuelva el problema principal;
- una o dos historias posteriores, claramente priorizadas;
- cinco requisitos EARS;
- al menos tres preguntas de aclaración;
- una lista breve de fuera de alcance;
- al menos una vaguedad detectada durante la revisión de otro grupo.

No se espera una especificación completa ni una decisión técnica.

## Criterios de corrección

| Elemento | Correcto | Bloquea si… |
|---|---|---|
| P1 | Puede aportar valor de forma independiente | Mezcla todo el producto en una sola historia |
| Requisitos | Tienen condición o disparador y respuesta observable | Dicen «fácil», «bien» o «rápido» sin concretar |
| Aclaraciones | Preguntan por decisiones que cambian el resultado | Son preguntas de tecnología o de diseño visual |
| Fuera de alcance | Evita que la primera versión crezca | Está vacío o dice «todo entra» |
| Revisión cruzada | Señala una ambigüedad real y explica su efecto | Se limita a corregir estilo o erratas |

No penalices que dos grupos tomen decisiones distintas: en la dinámica muchas preguntas quedan deliberadamente sin responder.

## Solución razonada

Las [seis tarjetas resueltas](../04-dinamica-de-equipo-resuelta.md) muestran una posible salida para:

1. plazas de parking;
2. dudas de nóminas;
3. estado de proyectos;
4. material de oficina;
5. cursos internos;
6. visitas a la oficina.

Para cada caso, la solución mantiene el mismo recorrido:

- identifica el problema principal;
- propone una P1 independiente;
- convierte frases vagas en cinco requisitos EARS;
- señala qué datos o reglas faltan;
- formula preguntas de aclaración;
- recorta la primera versión.

Un ejemplo mínimo para «plazas de parking» podría ser:

```text
P1: solicitar una plaza para un día y saber si se ha asignado.

RF-001: El sistema deberá mostrar cuántas plazas están disponibles para cada día laborable.
RF-002: CUANDO una persona solicita una plaza disponible, el sistema deberá registrarla a su nombre para ese día.
RF-003: SI no quedan plazas para el día solicitado, ENTONCES el sistema deberá rechazar la solicitud e indicar que el aforo está completo.
RF-004: SI una persona ya tiene una plaza para ese día, ENTONCES el sistema deberá impedir una segunda asignación.
RF-005: CUANDO una persona cancela su plaza, el sistema deberá liberarla para otra solicitud.

Aclaraciones: prioridad de asignación, hora límite y tratamiento de plazas accesibles.
Fuera de alcance: abonos mensuales, visitas y control de acceso físico.
```

El resto de respuestas se desarrolla en el fichero ampliado.

## Alternativas válidas

- Formular la P1 desde el punto de vista de Oficina en vez de la persona usuaria, si sigue resolviendo el problema principal.
- Dejar una cifra como aclaración en vez de asumirla.
- Separar un requisito con dos respuestas si pueden fallar de forma independiente.
- Proponer otro fuera de alcance, siempre que la primera versión siga siendo coherente.
- Usar un chat de IA después de la dinámica como revisor, no como sustituto del debate del grupo.

## Errores frecuentes

| Error | Corrección |
|---|---|
| Intentar terminar una spec completa en 20 minutos | Limita la entrega a historia, cinco requisitos, preguntas y alcance |
| Debatir tecnología | Vuelve al comportamiento y a las reglas |
| Inventar respuestas para cerrar rápido | Registra la pregunta; quien encarga debe decidir |
| Revisar solo la gramática del otro grupo | Busca términos que permitan dos interpretaciones |
| Comparar palabra por palabra con la solución | Compara claridad, patrón y cobertura |

## En tres frases

1. La dinámica entrena el criterio y la revisión, no la producción de documentación extensa.
2. Las preguntas sin respuesta son un resultado útil: hacen visible lo que todavía no puede construirse con seguridad.
3. Varias soluciones pueden ser correctas si acotan una P1 y expresan reglas comprobables.

## Volver al ejercicio

Vuelve a la [Dinámica de equipo de 20 minutos](../../04-dinamica-de-equipo-20-minutos.md) o continúa con [Arreglar una especificación mala](../../05-arreglar-una-especificacion-mala.md).

---

🏠 [Índice de soluciones](../README.md)
