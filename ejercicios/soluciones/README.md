# Soluciones

> **Para quién:** cualquier persona que haya hecho un ejercicio y quiera comparar · **Tiempo de lectura:** ~2 min · **Nivel:** 🟢 básico

Aquí están las respuestas de los ejercicios y el ejemplo completo de ReservaSalas, la aplicación que sirve de hilo conductor a todo el material.

> [!NOTE]
> Son ejemplos, no la única respuesta correcta. Si tu solución es distinta pero cumple lo que pedía el ejercicio (requisitos que solo se leen de una manera, criterios de éxito con cifra, nada de tecnología en la especificación…), también vale. Haz primero el ejercicio y compara después: así aprendes mucho más.

## Qué hay en cada una

| Ejercicio | Solución | Qué contiene | Tiempo · nivel |
|---|---|---|---|
| [00 · Preparación del entorno](../00-preparacion-del-entorno.md) | [Entorno resuelto](00-preparacion-del-entorno-resuelta.md) | Cómo debería quedar tu entorno: lo que ves en cada comprobación, el árbol de carpetas del proyecto de prueba, los nueve comandos en cada escritura y una lista final de diez casillas | ~7 min · 🟡 |
| [01 · Tu primera especificación sin código](../01-tu-primera-especificacion-sin-codigo.md) | [Especificación: Solicitud de vacaciones](01-solicitud-de-vacaciones/especificacion.md) | La especificación completa: tres historias priorizadas, casos límite, catorce requisitos en EARS, tres criterios de éxito y la sesión de aclaraciones | ~12 min · 🟢 |
| [02 · Practicar requisitos EARS](../02-practicar-requisitos-ears.md) | [Requisitos EARS resueltos](02-requisitos-ears-resueltos.md) | Las doce frases vagas reescritas, con su patrón y su porqué; la clasificación de requisitos y el «caza el error» | ~10 min · 🟢 |
| [03 · ReservaSalas paso a paso](../03-reserva-salas-paso-a-paso.md) | [Ejemplo completo de ReservaSalas](03-reserva-salas/README.md) y [los pasos 7 a 10 por dentro](03-reserva-salas-pasos-7-a-10.md) | Los ficheros que deja el flujo SDD (*Spec-Driven Development*, desarrollo guiado por especificaciones): constitución, especificación, aclaraciones, lista de verificación, plan técnico y lista de tareas; y, aparte, lo que esos ficheros no guardan: el informe de `/speckit.analyze`, el cambio de 30 a 60 días y la reflexión | ~25 min + ~15 min · 🟡 |
| [04 · Dinámica de equipo de 20 minutos](../04-dinamica-de-equipo-20-minutos.md) | [Las seis tarjetas resueltas](04-dinamica-de-equipo-resuelta.md) | La hoja rellena de cada tarjeta (historias, cinco requisitos EARS, preguntas de aclaración y fuera de alcance) y las vaguedades más habituales de cada una | ~15 min · 🟢 |
| [05 · Arreglar una especificación mala](../05-arreglar-una-especificacion-mala.md) | [La especificación arreglada](05-especificacion-arreglada.md) | Todos los problemas de la especificación mala, explicados uno a uno con su arreglo, y los requisitos y criterios de éxito reescritos | ~15 min · 🟡 |
| [06 · Reto final: tu propio proyecto](../06-reto-final-tu-propio-proyecto.md) | [Ejemplo completo y punto de partida de cada idea](06-reto-final/README.md) | Un proyecto entero de principio a fin (el préstamo de portátiles: petición, constitución, especificación, plan, tareas y autoevaluación) y un esqueleto resuelto para cada una de las otras seis ideas | ~12 min + ~20 min · 🟡 |

El reto final es un proyecto tuyo, así que no tiene una solución única: lo que hay aquí son ejemplos para compararte cuando lo hayas hecho, no una clave de respuestas. Lo que lo evalúa es la lista de entrega y la rúbrica del propio ejercicio.

## El ejemplo completo de ReservaSalas

La carpeta [03-reserva-salas/](03-reserva-salas/README.md) es la referencia de todo el repositorio: los documentos, los diagramas y los ejercicios citan sus principios, sus requisitos (RF-001 a RF-012) y sus criterios de éxito (CE-001 a CE-004). Léela en este orden:

1. [README.md](03-reserva-salas/README.md): qué contiene y cómo se generó.
2. [constitution.md](03-reserva-salas/constitution.md): las reglas del juego.
3. [spec.md](03-reserva-salas/spec.md): qué tiene que hacer ReservaSalas y por qué.
4. [aclaraciones.md](03-reserva-salas/aclaraciones.md) y [checklist.md](03-reserva-salas/checklist.md): cómo se cerraron los huecos y cómo se comprobó la calidad.
5. [plan.md](03-reserva-salas/plan.md): cómo se va a construir.
6. [tasks.md](03-reserva-salas/tasks.md): en qué orden y con qué pruebas.
7. [Los pasos 7 a 10 por dentro](03-reserva-salas-pasos-7-a-10.md): lo que viene después de las tareas y no es un fichero del ejemplo: el informe de `/speckit.analyze`, el cambio de antelación de 30 a 60 días y la reflexión.

Si no vas a construirla, con los tres primeros (y las aclaraciones) tienes de sobra: son los que hablan del qué y del porqué.

## El ejemplo completo del reto final

La carpeta [06-reto-final/](06-reto-final/README.md) reúne los materiales para compararte cuando hayas hecho tu proyecto. Léela en este orden:

1. [README.md](06-reto-final/README.md): qué hay, por qué el reto no tiene una solución única y cómo usar los materiales sin estropearte el ejercicio.
2. [El préstamo de portátiles](06-reto-final/prestamo-de-portatiles/README.md): un proyecto de la idea 1 de principio a fin, con su [petición](06-reto-final/prestamo-de-portatiles/peticion.md), su [constitución](06-reto-final/prestamo-de-portatiles/constitution.md), su [especificación](06-reto-final/prestamo-de-portatiles/spec.md), su [plan](06-reto-final/prestamo-de-portatiles/plan.md), sus [tareas](06-reto-final/prestamo-de-portatiles/tasks.md) y su [autoevaluación](06-reto-final/prestamo-de-portatiles/autoevaluacion.md).
3. [Otras ideas](06-reto-final/otras-ideas.md): un esqueleto resuelto para cada una de las otras seis ideas (la 4, vacaciones, es la especificación del [ejercicio 01](01-solicitud-de-vacaciones/especificacion.md)).

## Siguiente paso

Vuelve al [índice de ejercicios](../README.md) para elegir el siguiente, o abre las [plantillas](../plantillas/README.md) para aplicar lo aprendido a un caso tuyo.

---

🏠 [Índice de ejercicios](../README.md)
