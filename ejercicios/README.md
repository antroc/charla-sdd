# Ejercicios

> **Para quién:** toda la empresa, sepa programar o no · **Tiempo de lectura:** ~4 min · **Nivel:** 🟢 básico

Aquí se deja de leer y se empieza a practicar. Los siete ejercicios van desde redactar una primera especificación sin instalar nada hasta recorrer un flujo SDD completo y construir una funcionalidad pequeña.

No hace falta hacerlos todos ni seguirlos como un examen. La idea es equivocarse aquí, comparar después con las soluciones y entender qué información necesita otra persona —o cualquier asistente de programación— para continuar el trabajo sin depender del contexto oculto de una conversación.

## Convención neutral para cualquier asistente

Los ejercicios no dependen de Codex, Claude Code, GitHub Copilot, Cursor ni de ningún otro producto concreto. Cuando aparezca una expresión como **Acción SDD: `specify`**, significa: ejecuta la acción equivalente en el asistente que estés usando.

La forma exacta de invocarla puede cambiar según la herramienta: comando, menú, *skill*, agente o *prompt*. En este material importan el nombre de la acción, el artefacto que recibe y el resultado que debe producir; no el prefijo del comando ni la carpeta donde cada herramienta guarda su configuración.

Las acciones usadas son:

`constitution → specify → clarify → plan → checklist → tasks → analyze → implement → converge`

Si tu asistente no ofrece una acción equivalente, usa las [plantillas](plantillas/README.md) y pega el *prompt* del ejercicio en un chat autorizado. El flujo y los criterios de revisión son los mismos.

## Los siete ejercicios

| Nº | Ejercicio | Qué vas a hacer | Nivel | Tiempo | ¿Hay que instalar algo? | Solución |
|---|---|---|---|---|---|---|
| 00 | [Preparación del entorno](00-preparacion-del-entorno.md) | Elegir la vía con plantillas o preparar Spec Kit con cualquier asistente compatible, sin configuración específica de una marca | 🟡 | 10-40 min | Solo en la vía B | [Solución del ejercicio 00](soluciones/00-preparacion-del-entorno/README.md) |
| 01 | [Tu primera especificación sin código](01-tu-primera-especificacion-sin-codigo.md) | Escribir una especificación pequeña de «Solicitud de vacaciones»: una P1, casos límite, requisitos y criterios de éxito | 🟢 | 30-45 min | No | [Solución del ejercicio 01](soluciones/01-solicitud-de-vacaciones/README.md) |
| 02 | [Practicar requisitos EARS](02-practicar-requisitos-ears.md) | Convertir frases vagas en requisitos comprobables, reconocer patrones y detectar errores | 🟢 | 30 min | No | [Solución del ejercicio 02](soluciones/02-requisitos-ears/README.md) |
| 03 | [ReservaSalas paso a paso](03-reserva-salas-paso-a-paso.md) | Recorrer el flujo completo con Spec Kit y cualquier asistente compatible, incluida una revisión multiagente y un cambio desde la spec | 🟡 | 90-120 min | Sí (vía B) | [Solución del ejercicio 03](soluciones/03-reserva-salas/README.md) |
| 04 | [Dinámica de equipo de 20 minutos](04-dinamica-de-equipo-20-minutos.md) | Pasar en grupo de una petición vaga a historias, requisitos y preguntas de aclaración | 🟢 | 20 min | No | [Solución del ejercicio 04](soluciones/04-dinamica-de-equipo/README.md) |
| 05 | [Arreglar una especificación mala](05-arreglar-una-especificacion-mala.md) | Encontrar los problemas que bloquean una especificación y corregir solo lo necesario para poder planificar | 🟡 | 25-30 min | No | [Solución del ejercicio 05](soluciones/05-especificacion-arreglada/README.md) |
| 06 | [Reto final: tu propio proyecto](06-reto-final-tu-propio-proyecto.md) | Llevar una funcionalidad pequeña de un problema real por todo el flujo, hasta código, pruebas y un cambio desde la spec | 🔴 | 60-90 min | Sí (vía B) | [Solución del ejercicio 06](soluciones/06-reto-final/README.md) |

🟢 básico: no hace falta conocimiento técnico. 🟡 intermedio: ayuda conocer Git y haber visto código. 🔴 avanzado: hace falta desenvolverse con un repositorio y revisar código generado.

## Las dos vías

La mayoría de los ejercicios se hacen sin instalar nada. Solo el 03 y el 06 necesitan un entorno de programación; el ejercicio 00 explica cómo prepararlo sin fijar una herramienta concreta.

- **Vía A, con plantillas:** ejercicios 01, 02, 04 y 05. Basta con un documento, las plantillas y, opcionalmente, un chat de IA autorizado.
- **Vía B, con Spec Kit:** ejercicios 03 y 06. Necesitas Git, Python, Spec Kit y cualquier asistente compatible autorizado por tu organización.

> [!WARNING]
> Usa solo herramientas autorizadas por tu empresa y trabaja siempre con datos ficticios. No pegues nombres, correos, contratos, nóminas ni información de clientes en un asistente sin aprobación expresa.

## Qué ejercicios hacer según tu objetivo

| Si quieres… | Recorrido recomendado |
|---|---|
| Entender SDD y decidir si tiene sentido para tu equipo | 01 → 04 |
| Aprender a escribir y revisar requisitos | 01 → 02 → 05 |
| Construir una funcionalidad completa con SDD | 00 (vía B) → 02 → 03 → 06 |
| Ir al grano porque ya trabajas con asistentes de programación | 00 (vía B) → 03 → 06 |

## Cómo usarlos

Haz primero el ejercicio y abre después la carpeta de su solución. Todas las soluciones siguen la misma estructura:

1. **Mínimo esperado.** Lo necesario para considerar el ejercicio bien resuelto.
2. **Criterios de corrección.** Qué comprobar y qué no penalizar.
3. **Solución razonada.** Un ejemplo completo o los artefactos de referencia.
4. **Alternativas válidas.** Decisiones distintas que también cumplen el ejercicio.
5. **Errores frecuentes.** Señales de que todavía falta revisar algo.

Una solución diferente también es válida si es clara, comprobable, coherente y mantiene el alcance. Una respuesta más larga no es necesariamente mejor.

## Plantillas y soluciones

- [Plantillas](plantillas/README.md): constitución, especificación, aclaraciones, plan técnico, tareas y lista de verificación.
- [Soluciones](soluciones/README.md): una carpeta por ejercicio, con su portada, criterios de corrección y materiales resueltos.

## Siguiente paso

Empieza por [Preparación del entorno](00-preparacion-del-entorno.md) si todavía no sabes qué vía vas a seguir. Si solo quieres practicar especificación, puedes ir directamente a [Tu primera especificación sin código](01-tu-primera-especificacion-sin-codigo.md).

---

🏠 [Portada del repositorio](../README.md)
