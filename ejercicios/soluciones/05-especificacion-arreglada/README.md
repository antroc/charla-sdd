# Solución del ejercicio 05: arreglar una especificación mala

> **Para quién:** quien haya terminado el ejercicio 05 · **Tiempo de lectura:** ~6 min, más la revisión comentada · **Nivel:** 🟡 intermedio

Esta carpeta reúne la solución del [ejercicio 05](../../05-arreglar-una-especificacion-mala.md). La auditoría desarrollada está en [revision-comentada.md](revision-comentada.md).

## Mínimo esperado

El ejercicio se considera resuelto cuando se identifican y corrigen **12 problemas relevantes**:

- dos de alcance o prioridad;
- dos de requisitos funcionales;
- dos de criterios de éxito;
- dos contradicciones con la constitución;
- cuatro problemas adicionales que puedan cambiar el producto construido.

No hace falta localizar todas las erratas ni reproducir la auditoría completa.

## Criterios de corrección

| Área | Correcto | Bloquea si… |
|---|---|---|
| Alcance | La primera versión queda acotada | Se añaden funciones no solicitadas o «todo entra» |
| Historias | La P1 resuelve el problema principal | La prioridad se basa en lo vistoso o lo fácil de programar |
| Requisitos | Son comprobables, atómicos y sin tecnología | Usan adjetivos vagos, mezclan capacidades o contradicen la constitución |
| Criterios de éxito | Incluyen cifra y forma de medida | Se limitan a «rápido», «fácil» o «la gente estará contenta» |
| Aclaraciones | Cierran decisiones y actualizan la spec | Quedan como preguntas sueltas o respuestas solo en el chat |
| Checklist | Señala lo que todavía falta | Se marca todo como correcto sin evidencia |

Una clasificación distinta es válida si identifica el mismo riesgo y propone una corrección coherente.

## Solución razonada

La [revisión comentada](revision-comentada.md) contiene:

- una selección de doce problemas suficientes para resolver el ejercicio;
- una posible reescritura de los requisitos funcionales;
- criterios de éxito medibles;
- preguntas de aclaración pendientes;
- cambios necesarios en historias, casos límite, entidades, supuestos y alcance;
- la forma correcta de usar la lista de verificación.

Los defectos más importantes no son las erratas. Son los que pueden provocar que se construya otra cosa:

1. tecnología dentro de la especificación;
2. prioridades que no responden al problema principal;
3. funciones añadidas sin petición;
4. requisitos con varias interpretaciones;
5. permisos y límites sin decidir;
6. contradicciones con los principios del proyecto;
7. criterios imposibles de medir;
8. casos límite aplazados hasta la programación.

La especificación canónica de ReservaSalas está en [../03-reserva-salas/spec.md](../03-reserva-salas/spec.md), pero conviene abrirla después de terminar tu propia revisión.

## Alternativas válidas

- Agrupar varios síntomas bajo una causa común, siempre que expliques su impacto.
- Separar un requisito compuesto en varios requisitos más pequeños.
- Utilizar otra numeración para RF y CE si no hay duplicados ni huecos confusos.
- Proponer cifras distintas para los criterios de éxito si están señaladas como provisionales o confirmadas por quien encarga.
- Detectar más de doce problemas, siempre que la revisión siga siendo útil y no se convierta en una búsqueda de estilo.

## Errores frecuentes

| Error | Corrección |
|---|---|
| Buscar solo erratas y gramática | Prioriza ambigüedades, contradicciones, alcance y trazabilidad |
| Comparar desde el principio con la solución canónica | Revisa primero con la constitución y la checklist |
| Reescribir todo sin explicar los fallos | Conserva una lista que relacione problema, impacto y arreglo |
| Inventar las respuestas de negocio | Registra aclaraciones y deja que quien encarga decida |
| Marcar la spec como lista porque los requisitos ya están corregidos | Revisa también historias, casos límite, supuestos y alcance |

## En tres frases

1. Revisar una spec consiste en detectar decisiones abiertas o contradictorias antes de que lleguen al plan y al código.
2. Los requisitos se corrigen con condiciones, respuestas observables y una sola regla; los criterios, con cifras.
3. Doce problemas que cambian el producto enseñan más que cuarenta correcciones de estilo.

## Volver al ejercicio

Vuelve a [Arreglar una especificación mala](../../05-arreglar-una-especificacion-mala.md) o continúa con el [Reto final](../../06-reto-final-tu-propio-proyecto.md).

---

🏠 [Índice de soluciones](../README.md)
