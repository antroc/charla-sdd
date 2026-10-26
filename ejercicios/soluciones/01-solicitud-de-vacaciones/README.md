# Solución del ejercicio 01: primera especificación

> **Para quién:** quien haya terminado el ejercicio 01 · **Tiempo de lectura:** ~5 min, más el ejemplo ampliado · **Nivel:** 🟢 básico

Esta portada explica cómo comparar tu trabajo con el [ejercicio 01](../../01-tu-primera-especificacion-sin-codigo.md). La [especificación ampliada](especificacion.md) desarrolla el proceso completo de vacaciones, pero el ejercicio actual solo exige una P1 pequeña.

## Mínimo esperado

Tu solución es suficiente si contiene:

- un resumen sin tecnología;
- los perfiles empleado, manager y RRHH;
- una P1 completa para registrar una solicitud pendiente;
- P2 y P3 identificadas como iteraciones posteriores;
- entre tres y cinco casos límite;
- entre cuatro y seis requisitos EARS que cubran únicamente la P1;
- exactamente dos criterios de éxito medibles;
- entre tres y cinco aclaraciones;
- supuestos y fuera de alcance.

No necesitas reproducir las tres historias ni los catorce requisitos del ejemplo ampliado.

## Criterios de corrección

| Elemento | Debe cumplir | Bloquea si… |
|---|---|---|
| P1 | Aporta valor por sí sola y puede probarse de forma independiente | Incluye aprobación, cancelación e informes completos |
| Requisitos | Entre 4 y 6, comprobables, sin tecnología y trazables a la P1 | Hay decisiones técnicas o requisitos de P2/P3 |
| Casos límite | Cada uno tiene respuesta o aclaración pendiente | Solo aparece el camino correcto |
| Criterios de éxito | Son 2, contienen cifras y explican cómo se medirán | Dicen «rápido», «fácil» o «mejor» sin medida |
| Aclaraciones | Las respuestas se aplican al texto afectado | La decisión queda únicamente en el chat |
| Alcance | P2/P3, bajas, nómina e informes quedan fuera | El documento intenta resolver todo el proceso |

No penalices una redacción diferente ni cifras distintas si están justificadas y son comprobables.

## Solución razonada

Una solución mínima puede tomar estas decisiones:

### Historia P1

> Como empleado quiero solicitar unos días de vacaciones para que mi petición quede registrada y mi manager la reciba.

Prueba independiente: una persona con saldo suficiente envía una solicitud; esta aparece como pendiente para ella y para su manager.

### Requisitos mínimos posibles

```text
RF-001: El sistema deberá mostrar a cada persona sus días disponibles del año en curso.

RF-002: CUANDO una persona envía una solicitud con fechas válidas,
el sistema deberá registrarla en estado «pendiente».

RF-003: CUANDO una solicitud queda registrada,
el sistema deberá avisar al manager de la persona con las fechas y los días solicitados.

RF-004: SI una persona solicita más días de los que tiene disponibles,
ENTONCES el sistema deberá rechazar la solicitud e indicar su saldo disponible.

RF-005: SI la fecha de inicio es anterior a la fecha actual,
ENTONCES el sistema deberá rechazar la solicitud e indicar que no se admiten fechas pasadas.

RF-006: MIENTRAS una solicitud esté pendiente,
el sistema deberá mostrar ese estado a la persona solicitante.
```

Separar el registro y el aviso en RF-002 y RF-003 facilita probar ambos comportamientos por separado. También sería correcto reunirlos si el equipo considera que forman una única respuesta atómica.

### Criterios de éxito

```text
CE-001: Crear y enviar una solicitud válida lleva menos de 2 minutos.
CE-002: El 100 % de las solicitudes enviadas correctamente quedan visibles para la persona y su manager.
```

### Alcance posterior

- P2: aprobar o rechazar con motivo.
- P3: consultar saldos e informes globales.

La [especificación ampliada](especificacion.md) muestra cómo podrían desarrollarse esas iteraciones. Léela como continuación posible, no como mínimo obligatorio.

## Alternativas válidas

- Descontar provisionalmente del saldo los días pendientes o mantenerlos separados, siempre que una aclaración lo decida.
- Contar días laborables o naturales, si la decisión queda escrita y se propaga a requisitos y criterios.
- Enviar un aviso por correo, por notificación interna o dejar el canal para el plan, siempre que la spec describa el resultado observable sin fijar tecnología innecesaria.
- Tratar «persona sin manager» como rechazo, cola de RRHH o aclaración bloqueante.
- Usar cinco requisitos en vez de seis si no se pierde comportamiento.

## Errores frecuentes

| Error | Corrección |
|---|---|
| Copiar completa la especificación ampliada | Vuelve al mínimo esperado y elimina P2/P3 de esta entrega |
| Mantener siete requisitos aunque el ejercicio pide seis como máximo | Retira permisos e informes que todavía no pertenecen a P1 |
| Escribir tres criterios porque el ejemplo antiguo los tenía | Conserva únicamente dos criterios relacionados con la P1 |
| Responder aclaraciones sin modificar la spec | Actualiza requisito, caso límite o criterio afectado |
| Incluir base de datos, framework o diseño de pantallas | Mueve esas decisiones al plan técnico |

## En tres frases

1. La solución mínima cubre una sola historia y deja el resto visible, pero fuera de alcance.
2. Cuatro a seis requisitos y dos criterios medibles son suficientes para este ejercicio.
3. El ejemplo ampliado enseña una evolución posible; no es una plantilla obligatoria.

## Volver al ejercicio

Vuelve a [Tu primera especificación sin código](../../01-tu-primera-especificacion-sin-codigo.md) o continúa con [Requisitos EARS](../../02-practicar-requisitos-ears.md).

---

🏠 [Índice de soluciones](../README.md)
