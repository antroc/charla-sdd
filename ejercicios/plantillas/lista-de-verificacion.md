# Plantilla: lista de verificación

> [!TIP]
> Este fichero es una lista de preguntas de sí o no sobre la calidad de la especificación: un control de calidad del texto, no del código (en Spec Kit lo llaman «las pruebas unitarias de la especificación»). Copia este fichero junto a la especificación, renómbralo `checklist.md` (en Spec Kit, `checklists/requirements.md` o `checklists/<tema>.md`), responde cada pregunta y marca `[x]` solo las que cumplan. Borra este aviso al terminar.
>
> Con Spec Kit, `/speckit.specify` crea y evalúa una lista automática de calidad de la especificación (`checklists/requirements.md`), que `/speckit.clarify` vuelve a evaluar; `/speckit.checklist` genera listas por tema (experiencia de uso, seguridad…) y en estas el asistente de IA nunca marca casillas: eso lo hace quien revisa. Esta plantilla sirve para revisar una especificación sin herramientas o para contrastar la que genere el asistente.
>
> Cada «no» es algo que hay que arreglar antes de planificar: la lista no comprueba que el sistema funcione, comprueba que lo que has escrito es claro, completo y medible.

<!--
  Qué es: una lista de preguntas de sí o no sobre la calidad de la especificación. Cada «no» es algo que hay que arreglar antes de planificar.
  Para quién: la pasa quien *no* escribió la especificación (otra persona del equipo, negocio, o el asistente de IA como primera pasada). Cuatro ojos ven más que dos.
  Consejo: cita siempre la sección o el requisito que motiva cada pregunta: [Completitud, Spec §RF-005]. Así se encuentra rápido.
-->

**Propósito:** [comprobar que la especificación de ReservaSalas está lista para pasar al plan técnico] · **Creada:** [AAAA-MM-DD] · **Funcionalidad:** [`specs/001-reserva-salas/spec.md`] · **Responsable de la revisión:** [Marta, manager y futura usuaria]
<!-- «Responsable de la revisión» traduce el campo «Review Ownership» de la plantilla oficial de Spec Kit. Allí no es un nombre: es una nota que dice que la lista pertenece a quien revisa y que solo esa persona marca las casillas. Aquí aprovechamos el campo para apuntar quién la pasa, y así se sabe a quién preguntar. -->

**Significado de las marcas:** `[x]` quiere decir «revisado y cumple»; una casilla vacía quiere decir «falta, está mal o no se ha mirado todavía». No significa que el código esté hecho.

**Significado de las etiquetas:** al final de cada ítem, la primera palabra dice qué aspecto se revisa (Completitud: no falta nada · Claridad: se entiende de una sola forma · Coherencia: no se contradice · Medibilidad: se puede comprobar con un número o con un sí/no · Cobertura: todos los casos están tratados) y, cuando procede, el tipo de fallo que se busca ([Laguna] falta algo · [Ambigüedad] se entiende de dos formas · [Conflicto] dos partes se contradicen · [Supuesto] se da por hecho sin decirlo). Lo que va tras «Spec §» es la sección o el requisito donde mirar.

## Calidad del contenido
<!-- Qué se escribe: ¿la especificación habla de qué y por qué, y la entiende alguien de negocio? Para quién: cualquiera. Consejo: haz que la lea la persona menos técnica del equipo y pregúntale qué no ha entendido. -->

- [ ] CHK001 ¿La especificación está libre de tecnología: lenguajes, bases de datos, herramientas o nombres de API (la conexión entre dos programas)? [Completitud, Spec §toda]
- [ ] CHK002 ¿Está centrada en lo que las personas necesitan y en el valor para la empresa, no en cómo se construye? [Claridad]
- [ ] CHK003 ¿Puede leerla y entenderla alguien que no programa? [Claridad]
- [ ] CHK004 ¿Están rellenas todas las secciones obligatorias (historias, requisitos, criterios de éxito)? [Completitud]

## Completitud de los requisitos
<!-- Qué se escribe: ¿cada requisito está completo, es comprobable y sigue EARS? Para quién: quien revisa y quien luego escribirá las pruebas. Consejo: lee cada requisito y pregúntate «¿cómo demostraría que se cumple?». Si no sabes, no es comprobable. -->

- [ ] CHK005 ¿Están resueltos todos los marcadores [NECESITA ACLARACIÓN: …] (la etiqueta que deja quien escribe, o el asistente de IA, allí donde falta información)? [Laguna, Spec §Aclaraciones]
- [ ] CHK006 ¿Cada requisito sigue una de las cinco plantillas EARS: «El sistema deberá…», «CUANDO…, el sistema deberá…», «MIENTRAS…, el sistema deberá…», «SI…, ENTONCES el sistema deberá…», «DONDE…, el sistema deberá…»? [Claridad, Spec §Requisitos funcionales]
- [ ] CHK007 ¿Cada requisito dice *una* sola cosa y se puede comprobar con un sí o un no? [Medibilidad, Spec §Requisitos funcionales]
- [ ] CHK008 ¿Todo adjetivo como «rápido», «intuitivo» o «robusto» lleva un número al lado? [Ambigüedad]
- [ ] CHK009 ¿Los requisitos están numerados (RF-001, RF-002…) y ninguno se repite con otras palabras? [Coherencia]
- [ ] CHK010 ¿Hay casos límite escritos (solapamientos, fuera de horario, sala en mantenimiento, más de 4 horas)? [Cobertura, Spec §Casos límite]
- [ ] CHK011 ¿El alcance está acotado: existe la sección «Fuera de alcance» y dice algo concreto? [Laguna, Spec §Fuera de alcance]
- [ ] CHK012 ¿Están escritos los supuestos y las dependencias (correo corporativo, sin calendario en la primera versión)? [Supuesto, Spec §Supuestos]

## Preparación de la funcionalidad
<!-- Qué se escribe: ¿historias, criterios de aceptación y criterios de éxito encajan entre sí? Para quién: negocio y quien construye, juntos. Consejo: coge un requisito al azar y busca en qué historia y en qué criterio de éxito se refleja; si no lo encuentras, hay una laguna. -->

- [ ] CHK013 ¿Cada historia tiene prioridad (P1, P2, P3), un «por qué» y se puede probar por separado? [Completitud, Spec §Historias]
- [ ] CHK014 ¿La historia P1, ella sola, ya resolvería el problema principal? [Coherencia, Spec §Historia 1]
- [ ] CHK015 ¿Cada historia tiene al menos dos criterios de aceptación en formato Dado/Cuando/Entonces? [Completitud]
- [ ] CHK016 ¿Cada requisito funcional se refleja en algún criterio de aceptación? [Cobertura]
- [ ] CHK017 ¿Los criterios de éxito tienen número (tiempo, porcentaje, cantidad) y no mencionan tecnología? [Medibilidad, Spec §CE-001 a CE-004]
- [ ] CHK018 ¿Las historias cubren los recorridos principales de cada tipo de persona (empleado, administración)? [Cobertura]
- [ ] CHK019 ¿Los requisitos son compatibles entre sí y con la constitución (por ejemplo, ninguno pide datos que «Datos mínimos» prohíbe)? [Conflicto]

## [Categoría propia: experiencia de uso]
<!-- Qué se escribe: añade categorías según el proyecto (seguridad, accesibilidad, datos…). Para quién: quien conozca ese tema. Consejo: preguntas sobre la *especificación*, no sobre el producto: «¿está dicho qué ve la persona si falla?», no «¿la pantalla es bonita?». -->

- [ ] CHK020 [¿Está definido qué mensaje ve la persona cuando se rechaza una reserva (RF-005)?] [Laguna, Spec §RF-005]
- [ ] CHK021 [¿Está dicho qué pasa cuando no hay ninguna sala libre en la franja pedida?] [Laguna, Spec §Casos límite]
- [ ] CHK022 [...]

## Notas
<!-- Qué se escribe: hallazgos, decisiones y qué se ha cambiado en la especificación a raíz de la revisión. Para quién: quien vuelva a revisar después. Consejo: fecha y nombre en cada nota. -->

- Marca `[x]` solo después de comprobarlo en la especificación; en caso de duda, déjala vacía y apunta por qué.
- Con Spec Kit, `/speckit.implement` lee estas casillas antes de empezar: si hay ítems sin marcar, pregunta si continuar.
- [AAAA-MM-DD, Marta: CHK008 fallaba porque CE-001 decía «rápido»; cambiado a «menos de 1 minuto».]
- [...]

<!-- Volver al índice de plantillas: abre README.md en esta misma carpeta (ejercicios/plantillas/README.md). -->
