# Ejercicios

> **Para quién:** todos los perfiles (managers, RRHH, negocio y quien programa) · **Tiempo de lectura:** ~4 min · **Nivel:** 🟢 básico

Esta carpeta es la práctica del repositorio. Son siete ejercicios guiados paso a paso, desde escribir una especificación con papel y bolígrafo hasta construir una aplicación con un asistente de IA siguiendo SDD (*Spec-Driven Development*, desarrollo guiado por especificaciones). Cada ejercicio dice qué necesitas, qué tienes que hacer en cada paso y qué deberías ver. Incluye una casilla para marcar lo que vas terminando, una tabla de errores frecuentes, unas preguntas de autoevaluación y, casi siempre, una solución para comparar.

**Qué vas a encontrar**

- [Los siete ejercicios](#los-siete-ejercicios)
- [Las dos vías: con o sin herramientas](#las-dos-vías-con-o-sin-herramientas)
- [Qué ejercicios hacer según tu perfil](#qué-ejercicios-hacer-según-tu-perfil)
- [Cómo usarlos](#cómo-usarlos)
- [Plantillas y soluciones](#plantillas-y-soluciones)

## Los siete ejercicios

| Nº | Ejercicio | Qué vas a hacer | Nivel | Tiempo (hacerlo) | ¿Hay que instalar algo? | Solución |
|---|---|---|---|---|---|---|
| 00 | [Preparación del entorno](00-preparacion-del-entorno.md) | Dejar listo lo que necesitas: la vía A no instala nada; la vía B instala Spec Kit y comprueba que funciona | 🟡 | 10-45 min | Solo en la vía B | Comprobaciones en el propio ejercicio |
| 01 | [Tu primera especificación sin código](01-tu-primera-especificacion-sin-codigo.md) | Escribir con una plantilla la especificación de «Solicitud de vacaciones»: historias, casos límite, requisitos y criterios de éxito | 🟢 | 30 min | No | [Especificación resuelta](soluciones/01-solicitud-de-vacaciones/especificacion.md) |
| 02 | [Practicar requisitos EARS](02-practicar-requisitos-ears.md) | Convertir doce frases vagas en requisitos que solo se pueden leer de una manera, reconocer patrones y cazar errores | 🟢 | 20 min | No | [Requisitos resueltos](soluciones/02-requisitos-ears-resueltos.md) |
| 03 | [ReservaSalas paso a paso con Spec Kit](03-reserva-salas-paso-a-paso.md) | Construir ReservaSalas recorriendo los siete pasos del flujo con Spec Kit y un asistente de IA, y cambiarla tocando solo la especificación | 🟡 | 90-120 min | Sí (vía B) | [Ejemplo completo](soluciones/03-reserva-salas/README.md) |
| 04 | [Dinámica de equipo de 20 minutos](04-dinamica-de-equipo-20-minutos.md) | Taller en grupo, sin ordenador: de una petición vaga a historias, requisitos y preguntas de aclaración | 🟢 | 20 min | No | Ejemplos dentro del propio ejercicio |
| 05 | [Arreglar una especificación mala](05-arreglar-una-especificacion-mala.md) | Encontrar los problemas de una especificación escrita con prisa y reescribir sus requisitos y criterios de éxito | 🟡 | 30-40 min | No | [Especificación arreglada](soluciones/05-especificacion-arreglada.md) |
| 06 | [Reto final: tu propio proyecto](06-reto-final-tu-propio-proyecto.md) | Llevar un problema real de tu día a día por todo el flujo, hasta una aplicación pequeña que funciona | 🔴 | 2-4 h, en dos o tres sesiones | Sí (vía B) | Sin solución: rúbrica de autoevaluación y ejemplos de buen resultado |

🟢 básico: no hace falta ningún conocimiento técnico. 🟡 intermedio: ayuda saber qué es un repositorio y haber visto código. 🔴 avanzado: para quien programa habitualmente.

## Las dos vías: con o sin herramientas

La mayoría de los ejercicios se hacen sin instalar nada. Solo el 03 y el 06 necesitan herramientas, y el [ejercicio 00](00-preparacion-del-entorno.md) te explica cómo prepararlas.

```mermaid
flowchart LR
  e00["00 Preparar el entorno"]
  subgraph viaA ["Vía A: sin instalar nada"]
    e01["01 Primera especificación"] --> e02["02 Requisitos EARS"]
    e02 --> e05["05 Arreglar una especificación"]
    e04["04 Dinámica de equipo"]
  end
  subgraph viaB ["Vía B: con Spec Kit y un asistente de IA"]
    e03["03 ReservaSalas paso a paso"] --> e06["06 Reto final"]
  end
  e00 -->|"vía A"| e01
  e00 -->|"vía B"| e03
  e02 -.->|"recomendable antes"| e03
```

De izquierda a derecha: el ejercicio 00 te dice qué vía necesitas. Por la vía A, sin instalar nada, vas de la primera especificación (01) a practicar requisitos (02) y a arreglar una especificación mala (05); la dinámica de equipo (04) se hace en grupo cuando quieras. Por la vía B, con Spec Kit y un asistente de IA, construyes ReservaSalas (03) y después tu propio proyecto (06). Conviene haber hecho el 02 antes del 03, porque en el 03 vas a revisar requisitos escritos así.

> [!WARNING]
> Usa solo el asistente de IA que haya autorizado la empresa, y nunca metas en él datos reales de clientes o de personas de la plantilla. Los ejercicios usan siempre ejemplos ficticios.

## Qué ejercicios hacer según tu perfil

| Si eres… | Haz | Por qué |
|---|---|---|
| Manager o responsable de equipo | [01](01-tu-primera-especificacion-sin-codigo.md), y el [04](04-dinamica-de-equipo-20-minutos.md) con tu equipo | Para saber qué pedir y cómo revisar lo que te entreguen |
| RRHH o perfil de negocio | [01](01-tu-primera-especificacion-sin-codigo.md) → [02](02-practicar-requisitos-ears.md), y el [05](05-arreglar-una-especificacion-mala.md) si quieres ir más allá | Para escribir peticiones que no se puedan malinterpretar |
| Programador junior | [00](00-preparacion-del-entorno.md) (vía B) → [02](02-practicar-requisitos-ears.md) → [03](03-reserva-salas-paso-a-paso.md) → [05](05-arreglar-una-especificacion-mala.md) → [06](06-reto-final-tu-propio-proyecto.md) | El recorrido completo, de la práctica guiada a un proyecto propio |
| Programador con experiencia | [00](00-preparacion-del-entorno.md) (vía B, si aún no tienes Spec Kit) → [03](03-reserva-salas-paso-a-paso.md) → [06](06-reto-final-tu-propio-proyecto.md) | Ver el flujo con una herramienta real y aplicarlo a algo tuyo |
| Quien facilita una charla o un taller | [04](04-dinamica-de-equipo-20-minutos.md), y el [01](01-tu-primera-especificacion-sin-codigo.md) y el [02](02-practicar-requisitos-ears.md) para prepararlo | Es la dinámica que se usa en la charla y en el taller |

El itinerario completo de cada perfil, con documentos y diagramas, está en el [mapa del repositorio](../diagramas/06-mapa-del-repositorio.md#itinerarios-por-perfil).

## Cómo usarlos

- **Por tu cuenta.** Cada paso termina con una casilla: márcala cuando veas lo que el ejercicio dice que deberías ver. Si te atascas, mira la tabla de errores frecuentes del final antes de abrir la solución.
- **En pareja.** Funciona muy bien una persona de negocio con una que programa: una escribe la especificación y la otra la revisa, y luego al revés. Es lo que pasa en un proyecto real.
- **En grupo.** El [ejercicio 04](04-dinamica-de-equipo-20-minutos.md) está pensado para hacerlo en una reunión de equipo o en la charla. La [guía del facilitador](../charla/guia-del-facilitador.md) explica cómo montar un taller de dos horas con varios ejercicios.

Haz primero el ejercicio y compara después con la solución. Las soluciones son ejemplos: si tu respuesta es distinta pero cumple lo que pide el ejercicio, también vale.

## Plantillas y soluciones

- [Plantillas](plantillas/README.md): la constitución, la especificación, la lista de aclaraciones, el plan técnico, la lista de tareas y la lista de verificación, en castellano y listas para copiar. Los ejercicios 01, 05 y 06 las usan.
- [Soluciones](soluciones/README.md): las respuestas de los ejercicios 01, 02 y 05, y el ejemplo completo de ReservaSalas del ejercicio 03, con los siete ficheros que produce el flujo.

## Siguiente paso

Si no programas, empieza por el [ejercicio 01](01-tu-primera-especificacion-sin-codigo.md). Si programas, empieza por el [ejercicio 00](00-preparacion-del-entorno.md) para preparar el entorno.

---

🏠 [Portada del repositorio](../README.md)
