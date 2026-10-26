# Solución del ejercicio 02: requisitos EARS

> **Para quién:** quien haya terminado el ejercicio 02 · **Tiempo de lectura:** ~5 min, más las respuestas comentadas · **Nivel:** 🟢 básico

Esta carpeta reúne la solución del [ejercicio 02](../../02-practicar-requisitos-ears.md). El desarrollo frase por frase está en [respuestas-comentadas.md](respuestas-comentadas.md).

## Mínimo esperado

La solución debe incluir:

- F01-F12 reescritas como requisitos comprobables;
- el patrón EARS de R1-R4;
- un diagnóstico y una corrección para E1-E4;
- marcadores de aclaración o supuestos visibles cuando faltan datos;
- ninguna tecnología dentro de los requisitos funcionales;
- criterios medibles para las frases de rendimiento o facilidad de uso.

No es necesario coincidir palabra por palabra con el ejemplo.

## Criterios de corrección

| Comprobación | Correcto | Incorrecto |
|---|---|---|
| Sujeto | El sistema, la cafetera o el torno | «El usuario deberá…» |
| Verbo | «deberá» | «debería», «podría» o «se espera» |
| Patrón | Corresponde a evento, estado, error, opción o regla permanente | Todos los requisitos empiezan por CUANDO |
| Comprobabilidad | La respuesta se verifica con un sí o un no | Usa «rápido», «intuitivo» o «bien» sin cifra |
| Atomicidad | Una regla o una respuesta coherente | Dos comportamientos independientes unidos por «y» |
| Datos ausentes | Se pregunta o se anota un supuesto | Se inventa una cifra sin señalarla |
| Tecnología | No aparece en el requisito | PostgreSQL, API, framework o tabla concreta |

Dos respuestas distintas pueden ser correctas si expresan la misma regla de negocio con igual precisión.

## Solución razonada

### Resumen de patrones esperados

| Frase | Patrón principal |
|---|---|
| F01 · Mostrar salas | Ubicuo |
| F02 · Avisar al pedir vacaciones | Por evento |
| F03 · No preparar café sin agua | Comportamiento no deseado; también es defendible por estado |
| F04 · Abrir el torno con tarjeta | Por evento, con aclaraciones |
| F05 · Sala en mantenimiento | Por estado |
| F06 · Permiso de RRHH | Opcional |
| F07 · Mostrar que la cafetera calienta | Por estado |
| F08 · Evitar solapamientos | Comportamiento no deseado |
| F09 · Límites de horario y duración | Uno o dos comportamientos no deseados |
| F10 · Saldo insuficiente | Comportamiento no deseado |
| F11 · Acceso fuera de horario | Complejo: estado + evento |
| F12 · Limpieza y aviso | Un requisito por evento y un criterio medible o aclaración |

### Clasificación R1-R4

- R1: por evento.
- R2: ubicuo.
- R3: opcional.
- R4: complejo.

### Diagnóstico E1-E4

- **E1:** mezcla comportamiento con PostgreSQL. Se elimina la tecnología y se conserva el comportamiento.
- **E2:** reúne reservar y marcar mantenimiento. Se divide en dos requisitos y se aclaran los permisos.
- **E3:** «rápido y fácil» no es comprobable. Se convierte en uno o varios criterios de éxito con cifra.
- **E4:** no dice cuándo se rechaza. Se añade la condición, por ejemplo saldo insuficiente o fechas inválidas.

La redacción completa, las explicaciones y las alternativas de cada frase están en [respuestas-comentadas.md](respuestas-comentadas.md).

## Alternativas válidas

- F03 puede escribirse con `SI… ENTONCES` o con `MIENTRAS`, según se describa el intento o el estado del depósito.
- F09 puede reunir los dos límites si la respuesta del sistema es exactamente la misma, o separarlos para mejorar la trazabilidad.
- F04 y F11 pueden dejar la duración y el horario como aclaraciones en vez de usar supuestos provisionales.
- R1 puede mantener dos efectos en la misma frase si ambos son la respuesta inseparable al mismo evento.
- Los criterios de éxito pueden usar cifras distintas si están justificadas por quien encarga el sistema.

## Errores frecuentes

| Error | Corrección |
|---|---|
| Elegir el patrón por la palabra informal de la frase original | Decide por el significado: error, evento, estado, opción o regla permanente |
| Añadir detalles que nadie pidió | Márcalos como aclaración o elimínalos |
| Copiar literalmente la solución canónica | Comprueba patrón, condición y respuesta; no la coincidencia textual |
| Convertir toda frase vaga en un requisito funcional | Algunas expresan criterios de éxito o decisiones aún pendientes |
| Confundir dos efectos del mismo evento con dos reglas distintas | Sepáralos solo si pueden cumplirse o fallar de forma independiente |

## En tres frases

1. EARS obliga a decir cuándo se aplica una regla y qué respuesta observable debe producir el sistema.
2. Los datos que faltan se preguntan o se anotan como supuestos, nunca se inventan a escondidas.
3. La solución correcta se reconoce por su precisión y comprobabilidad, no por coincidir palabra por palabra.

## Volver al ejercicio

Vuelve a [Practicar requisitos EARS](../../02-practicar-requisitos-ears.md) o continúa con [ReservaSalas paso a paso](../../03-reserva-salas-paso-a-paso.md).

---

🏠 [Índice de soluciones](../README.md)
