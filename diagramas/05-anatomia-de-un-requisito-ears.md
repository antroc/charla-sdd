# Anatomía de un requisito EARS

> **Para quién:** quien vaya a escribir o revisar una especificación, sepa programar o no · **Tiempo de lectura:** ~6 min · **Nivel:** 🟢 básico

En SDD (*Spec-Driven Development*, desarrollo guiado por especificaciones) la especificación (`spec.md`) recoge, entre otras cosas, los requisitos: qué tiene que hacer el sistema. En este material los escribimos en EARS (*Easy Approach to Requirements Syntax*), una forma sencilla y estructurada de redactar requisitos propuesta por Alistair Mavin y otros en 2009. La idea es que cada requisito sea una sola frase, con las mismas piezas siempre en el mismo orden, para que cualquiera pueda leerla y comprobar si se cumple.

Esta página desmonta un requisito real de ReservaSalas pieza a pieza y te da un árbol de decisión (una cadena de preguntas que se responden con sí o no) para elegir el patrón. La explicación completa, con reglas y ejemplos «antes → después», está en [Escribir requisitos claros (EARS)](../docs/05-escribir-requisitos-claros-ears.md).

**Qué vas a encontrar**

- [Las piezas de un requisito](#las-piezas-de-un-requisito)
- [¿Qué patrón EARS uso?](#qué-patrón-ears-uso)
- [Los cinco patrones y el complejo, con ReservaSalas](#los-cinco-patrones-y-el-complejo-con-reservasalas)

## Las piezas de un requisito

Tomamos el requisito RF-003 de la especificación de ReservaSalas, la que usamos como referencia en todo el material (está en [`spec.md`](../ejercicios/soluciones/03-reserva-salas/spec.md)). «RF» significa requisito funcional; los requisitos van numerados para poder citarlos desde el plan y las tareas.

> **RF-003**: CUANDO una persona confirma una reserva, el sistema deberá guardarla y mostrar un mensaje de confirmación con sala, fecha y hora.

El diagrama muestra las cinco piezas de ese requisito: la palabra clave, el disparador (lo que tiene que ocurrir para que el requisito se aplique), el sujeto, la obligación y la respuesta. Las dos primeras van antes de la coma y describen la situación; las otras tres van después y dicen qué tiene que pasar. Los dos recuadros grises, unidos con línea de puntos, dicen para qué sirve cada mitad.

```mermaid
flowchart LR
  subgraph antes ["Antes de la coma: ¿en qué situación?"]
    direction LR
    clave["Palabra clave: CUANDO"] --> disparador["Disparador: una persona confirma una reserva"]
  end
  subgraph despues ["Después de la coma: ¿qué tiene que pasar?"]
    direction LR
    sujeto["Sujeto: el sistema"] --> verbo["Obligación: deberá"] --> respuesta["Respuesta: guardarla y mostrar un mensaje de confirmación con sala, fecha y hora"]
  end
  disparador --> sujeto
  clave -.-> patron["Marca el patrón: por evento (algo ocurre en un momento concreto)"]
  respuesta -.-> prueba["Es lo que se comprueba en la prueba: ¿se guardó? ¿aparece el mensaje con sala, fecha y hora?"]
  classDef situacion fill:#FDF2E9,stroke:#B7791F;
  classDef accion fill:#E8F0FE,stroke:#1A56DB;
  classDef nota fill:#F3F4F6,stroke:#6B7280;
  class clave,disparador situacion;
  class sujeto,verbo,respuesta accion;
  class patron,prueba nota;
```

De izquierda a derecha: la palabra clave CUANDO avisa de que el requisito solo se aplica en una situación concreta, y el disparador dice cuál (alguien confirma una reserva). Después de la coma aparece siempre el mismo sujeto, «el sistema», seguido de «deberá» (es una obligación, no una sugerencia) y de la respuesta: qué hace exactamente.

Los dos recuadros grises resumen para qué sirve cada mitad: la palabra clave decide el patrón EARS, y la respuesta es la parte que luego se convierte en prueba. De hecho, esa respuesta es la versión general del «entonces» del criterio de aceptación 2 de la historia de usuario 1 de ReservaSalas (una historia de usuario es cada cosa que alguien quiere conseguir con la aplicación; sus criterios de aceptación son ejemplos concretos, con nombres, sala y horas, que se comprueban con un sí o un no).

Lo mismo, subrayado sobre la frase:

```text
CUANDO una persona confirma una reserva, el sistema deberá guardarla y mostrar un mensaje de confirmación con sala, fecha y hora.
└────┘ └──────────────────────────────┘  └────────┘ └────┘ └───────────────────────────────────────────────────────────────────┘
clave             disparador               sujeto   obligación                           respuesta
```

La tabla resume qué pregunta responde cada pieza y qué suele salir mal en ella.

| Pieza | Pregunta que responde | En RF-003 | Error típico |
|---|---|---|---|
| Palabra clave | ¿De qué tipo de situación hablamos? | CUANDO | Omitirla cuando sí hay una condición: «el sistema deberá rechazar reservas solapadas» esconde un SI. |
| Disparador o condición | ¿En qué momento o circunstancia? | una persona confirma una reserva | Vaguedad: «cuando haga falta», «si procede», «en los casos habituales». |
| Sujeto | ¿Quién responde? | el sistema | Nombrar tecnología o pantallas: «la base de datos», «el botón verde». |
| Obligación | ¿Es obligatorio? | deberá | «debería», «podría», «sería bueno que»: nadie sabe si hay que cumplirlo. |
| Respuesta | ¿Qué hace exactamente? | guardarla y mostrar un mensaje de confirmación con sala, fecha y hora | Adjetivos que no se pueden medir: «rápido», «bien», «de forma intuitiva». |

> [!TIP]
> Si no sabes cómo comprobarías la respuesta, el requisito aún no está terminado. «Mostrar un mensaje con sala, fecha y hora» se comprueba mirando la pantalla; «mostrar un mensaje claro» no.

## ¿Qué patrón EARS uso?

El diagrama es un árbol de decisión: partes de una frase sobre lo que debe hacer ReservaSalas, respondes cuatro preguntas con sí o no y llegas al patrón que te toca, con un requisito real de la especificación de ReservaSalas como ejemplo. Las preguntas van en el mismo orden que en [Escribir requisitos claros (EARS)](../docs/05-escribir-requisitos-claros-ears.md#qué-patrón-elijo).

```mermaid
flowchart TD
  frase["Tengo una frase: algo que ReservaSalas tiene que hacer"] --> q1["¿Es algo que no queremos que pase: un error, un intento no permitido, un límite que se incumple?"]
  q1 -->|"sí"| noDeseado["Comportamiento no deseado: SI (condición), ENTONCES el sistema deberá (respuesta) · RF-005"]
  q1 -->|"no"| q2["¿Ocurre en un momento concreto, porque alguien hace algo o llega una fecha? (confirma, cancela, consulta...)"]
  q2 -->|"sí"| cuando["Por evento: CUANDO (disparador), el sistema deberá (respuesta) · RF-003"]
  q2 -->|"no"| q3["¿Depende de un estado que dura un tiempo? (en mantenimiento, pendiente...)"]
  q3 -->|"sí"| mientras["Por estado: MIENTRAS (estado), el sistema deberá (respuesta) · RF-007"]
  q3 -->|"no"| q4["¿Se aplica solo a algunos perfiles, sedes o configuraciones?"]
  q4 -->|"sí"| donde["Opcional: DONDE (característica o perfil), el sistema deberá (respuesta) · RF-009"]
  q4 -->|"no"| ubicuo["Ubicuo: El sistema deberá (respuesta) · RF-001"]
  mientras -.->|"¿y además hay un disparador?"| complejo["Complejo: MIENTRAS (estado), CUANDO (disparador), el sistema deberá (respuesta)"]
  %% Enlaces invisibles: solo alinean los patrones en una columna
  noDeseado ~~~ cuando ~~~ mientras ~~~ complejo
  classDef pregunta fill:#FDF2E9,stroke:#B7791F;
  classDef patronEars fill:#E8F0FE,stroke:#1A56DB;
  classDef neutro fill:#F3F4F6,stroke:#6B7280;
  class q1,q2,q3,q4 pregunta;
  class cuando,mientras,noDeseado,donde,ubicuo,complejo patronEars;
  class frase neutro;
```

De arriba abajo: la primera pregunta es si la frase describe algo que no queremos que pase; si es así, es un comportamiento no deseado (SI…, ENTONCES…). Si no, ¿ocurre en un momento concreto? Es por evento (CUANDO). Si no, ¿depende de un estado que dura un tiempo? Es por estado (MIENTRAS). Si no, ¿se aplica solo a algunos perfiles, sedes o configuraciones? Es opcional (DONDE). Y si no depende de nada, es ubicuo: «El sistema deberá…» a secas.

La flecha punteada recuerda que, cuando hacen falta un estado y un disparador a la vez, se combinan en un requisito complejo (MIENTRAS…, CUANDO…); lo mismo si partes de un CUANDO y descubres que solo vale durante un estado.

La duda más frecuente es entre CUANDO y SI/ENTONCES, porque los dos describen algo que ocurre. Por eso la pregunta sobre lo que no queremos va la primera: confirmar una reserva es el funcionamiento normal (CUANDO); pedir una franja que ya está ocupada es un intento que hay que rechazar (SI/ENTONCES). Pista: si la respuesta del sistema es «rechazar», casi siempre es un SI. Entre MIENTRAS y SI, fíjate en la duración: una sala en mantenimiento es un estado que dura días (MIENTRAS); una franja ocupada es un intento concreto que se rechaza en el momento (SI).

## Los cinco patrones y el complejo, con ReservaSalas

La tabla recoge la plantilla de cada patrón, un requisito real de la especificación de ReservaSalas y cómo se comprobaría. Las palabras clave van siempre en mayúsculas y el verbo es siempre «deberá».

| Patrón | Plantilla | Ejemplo en ReservaSalas | Cómo se comprueba |
|---|---|---|---|
| Ubicuo | `El sistema deberá [respuesta].` | RF-001: El sistema deberá mostrar la lista de salas con su planta y aforo. | En cualquier momento: abres la lista y cada sala muestra planta y aforo. |
| Por evento | `CUANDO [disparador], el sistema deberá [respuesta].` | RF-003: CUANDO una persona confirma una reserva, el sistema deberá guardarla y mostrar un mensaje de confirmación con sala, fecha y hora. | Provocas el disparador (confirmas una reserva) y miras la respuesta. |
| Por estado | `MIENTRAS [estado], el sistema deberá [respuesta].` | RF-007: MIENTRAS una sala esté marcada en mantenimiento, el sistema deberá impedir nuevas reservas en ella. | Pones la sala en mantenimiento e intentas reservarla varias veces durante ese tiempo. |
| Comportamiento no deseado | `SI [condición], ENTONCES el sistema deberá [respuesta].` | RF-005: SI la franja solicitada se solapa con otra reserva de la misma sala, ENTONCES el sistema deberá rechazar la reserva e indicar qué franja está ocupada. | Fuerzas la situación mala (pides una franja ocupada) y compruebas el rechazo y el aviso. |
| Opcional | `DONDE [característica o perfil], el sistema deberá [respuesta].` | RF-009: DONDE la persona tenga permisos de administración, el sistema deberá permitir marcar una sala en mantenimiento. | Con una persona que tiene permisos de administración y con otra que no: solo la primera ve la opción de marcar la sala en mantenimiento. |
| Complejo | `MIENTRAS [estado], CUANDO [disparador], el sistema deberá [respuesta].` | Ejemplo construido a partir del criterio de aceptación 5 de la historia 1 (la especificación de ReservaSalas no usa este patrón): MIENTRAS una sala esté marcada en mantenimiento, CUANDO una persona consulta la disponibilidad, el sistema deberá mostrarla como «en mantenimiento» y no permitir elegirla. | Combinas las dos comprobaciones: con la sala en mantenimiento, consultas la disponibilidad y compruebas que aparece como «en mantenimiento» y no se puede elegir. |

Un detalle que verás en esa especificación: los doce requisitos (RF-001 a RF-012) se reparten entre los cinco patrones básicos, y en la propia `spec.md` hay una tabla que dice cuál usa cada uno. Si alguna vez dudas de un patrón, ese fichero es un buen sitio para comparar.

> [!NOTE]
> EARS no es un corsé: hay frases que admiten dos patrones correctos. Lo importante es que la condición quede explícita, que haya un solo «deberá» y que la respuesta se pueda comprobar. El patrón elegido es la forma de conseguirlo, no el objetivo.

## En tres frases

1. Un requisito EARS es una sola frase con piezas fijas: una palabra clave con su situación (si la hay), «el sistema deberá» y una respuesta concreta que se puede comprobar.
2. La palabra clave dice de qué tipo de situación hablamos: CUANDO (algo ocurre), MIENTRAS (algo dura), SI/ENTONCES (algo que no queremos), DONDE (solo en algunos casos); sin palabra clave, el requisito se cumple siempre.
3. Lo que va después de «deberá» es lo que luego se prueba: si no sabrías cómo comprobarlo, el requisito todavía no está terminado.

## Siguiente paso

Continúa con [Escribir requisitos claros (EARS)](../docs/05-escribir-requisitos-claros-ears.md), que desarrolla las reglas de oro y cómo pasar de una frase vaga a un requisito. Para practicar, tienes [el ejercicio 02: practicar requisitos EARS](../ejercicios/02-practicar-requisitos-ears.md).

---

⬅️ [Anterior: Roles y participación](04-roles-y-participacion.md) · 🏠 [Índice de diagramas](README.md) · ➡️ [Siguiente: Mapa del repositorio](06-mapa-del-repositorio.md)
