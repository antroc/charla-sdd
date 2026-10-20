# Cómo contribuir

> **Para quién:** cualquier persona de la empresa que quiera mejorar este material · **Tiempo de lectura:** ~7 min · **Nivel:** 🟢 básico

Este repositorio es material vivo: lo usamos para formar a gente de perfiles muy distintos, y mejora cada vez que alguien avisa de algo que no se entiende, de un ejemplo que falta o de un comando que ha cambiado. No hace falta saber programar para contribuir. Una errata señalada a tiempo vale tanto como un ejercicio nuevo.

**Qué vas a encontrar**

- [Tres formas de proponer un cambio](#tres-formas-de-proponer-un-cambio)
- [Qué cambios encajan](#qué-cambios-encajan)
- [Guía de estilo resumida](#guía-de-estilo-resumida)
- [Diagramas](#diagramas)
- [Si cambias el ejemplo ReservaSalas](#si-cambias-el-ejemplo-reservasalas)
- [Antes de enviar](#antes-de-enviar)
- [Qué no incluir](#qué-no-incluir)

## Tres formas de proponer un cambio

1. **Contándolo, sin tocar nada.** Abre una incidencia (*issue*, una petición o aviso que queda registrado en el repositorio) en la pestaña «Issues» de GitHub. Di qué fichero es, qué parte, qué falla y cómo lo dejarías. Si no tienes cuenta de GitHub, escribe al contacto que figura en la [portada](README.md#sobre-este-material).
2. **Editando en la web de GitHub.** Abre el fichero, pulsa el icono del lápiz y haz el cambio. Al guardar, GitHub te ofrece proponerlo («Propose changes») y crea una *pull request* (una propuesta de cambio que otra persona revisa antes de incorporarla). Es la forma más rápida para erratas y frases que se pueden decir mejor.
3. **Con Git, para cambios grandes.** Crea una rama (una copia de trabajo con nombre propio), haz los cambios en tu ordenador, revisa cómo se ven y abre una *pull request* explicando qué cambia y por qué. Ningún cambio entra sin que lo revise otra persona.

## Qué cambios encajan

- Erratas, frases que no se entienden y explicaciones que se pueden simplificar.
- Ejemplos nuevos, sobre todo de áreas que no son tecnología (RRHH, finanzas, operaciones…).
- Preguntas nuevas para las [preguntas frecuentes](docs/09-preguntas-frecuentes.md) y términos nuevos para el [glosario](docs/10-glosario.md).
- Ejercicios nuevos, con la misma estructura que los que ya hay (lo explica la guía de estilo).
- Actualizaciones de herramientas: las herramientas cambian cada pocos meses. Si un comando de Spec Kit ha cambiado, actualízalo citando la documentación oficial (<https://github.github.io/spec-kit/>) y la versión con la que lo has comprobado.

Si dudas de si algo encaja, abre una incidencia y lo hablamos antes de que te pongas a escribir.

## Guía de estilo resumida

Lo que más cuida este material es que lo entienda alguien que no ha programado nunca.

- **Tono.** Castellano de España, de tú, cercano y sin humo. Frases cortas y una idea por párrafo. Ejemplos concretos antes que definiciones abstractas.
- **Palabras inglesas.** Solo las que son estándar en el sector (*prompt*, *commit*, *pull request*…). La primera vez, en cursiva y explicadas en la misma frase. Si hay palabra en castellano, se usa la de castellano.
- **Sin promesas absolutas.** SDD reduce riesgos, no los elimina. Nada de cifras sin fuente.
- **Terminología fija.** Escribe siempre:

| Usa | En lugar de |
|---|---|
| SDD (*Spec-Driven Development*, desarrollo guiado por especificaciones) | «Spec-Driven» sin explicar, «desarrollo dirigido por specs» |
| *vibe coding*, explicado la primera vez | «programación por vibras» |
| asistente de IA | «la IA» a secas, «el modelo», «el LLM» |
| constitución, especificación, plan técnico, lista de tareas, lista de verificación | «spec» o «doc» sin explicar |
| aclarar, analizar, implementar | «clarificar», «implantar» |
| requisito | «requerimiento» |
| EARS | «formato de requisitos» sin nombrarlo |
| ReservaSalas, con Ana, Luis, Marta y Jorge | nombres de personas o salas reales |

- **Formato de cada documento.** Un único título principal (`#`); debajo, la cabecera «Para quién · Tiempo de lectura · Nivel» (🟢 básico, 🟡 intermedio, 🔴 avanzado); si el documento es largo, el bloque «Qué vas a encontrar» con enlaces a sus secciones; y al final, «En tres frases», «Siguiente paso» y la línea de navegación (anterior · índice · siguiente). Copia la estructura de cualquier documento de [docs/](docs/README.md).
- **Avisos.** Solo `> [!NOTE]`, `> [!TIP]`, `> [!IMPORTANT]` y `> [!WARNING]`, y pocos (cuatro o cinco por documento como mucho).
- **Huecos para rellenar.** Entre corchetes: `[respuesta]`. Nunca con ángulos como `<respuesta>`, porque GitHub los borra al mostrar la página.
- **Enlaces.** Siempre relativos al fichero en el que estás (`../docs/05-escribir-requisitos-claros-ears.md`), nunca la dirección completa de GitHub.
- **Ejercicios.** Siguen siempre el mismo orden: objetivo, qué necesitas, pasos numerados (cada uno con lo que hay que hacer, lo que deberías ver y una casilla `- [ ]`), errores frecuentes, preguntas para comprobar lo aprendido con las respuestas ocultas y, si aplica, la solución en [ejercicios/soluciones/](ejercicios/soluciones/README.md). Ofrece siempre una vía que no exija instalar nada.

## Diagramas

Los diagramas están escritos en Mermaid, un formato de texto que GitHub dibuja directamente. Para que no fallen:

- Escribe el texto de cada recuadro entre corchetes y comillas dobles: `A["Texto con tildes (y paréntesis)"]`. Los identificadores (`A`, `paso2`) van sin tildes ni espacios.
- Entre 6 y 14 recuadros por diagrama; si necesitas más, divídelo en dos.
- Antes del diagrama, una frase que diga qué muestra; después, dos o tres líneas que lo cuenten en voz alta, para quien no pueda verlo.
- Comprueba que se dibuja en la vista previa de GitHub (o en tu editor, si su vista previa admite Mermaid).

Cada diagrama de [diagramas/](diagramas/README.md) tiene además una copia en imagen en `diagramas/svg/` y `diagramas/png/`, para presentaciones. Si cambias un diagrama de esa carpeta, hay que regenerar sus imágenes. Copia el bloque en un fichero `.mmd` y usa la herramienta oficial de Mermaid (necesita Node.js), o pide a quien mantiene el material que lo haga:

```bash
npx -p @mermaid-js/mermaid-cli mmdc -i diagrama.mmd -o diagrama.svg -b white
npx -p @mermaid-js/mermaid-cli mmdc -i diagrama.mmd -o diagrama.png -b white -s 2
```

El nombre de la imagen es el del fichero de origen con el número del diagrama dentro de él: `02-flujo-completo-sdd-1.svg`.

## Si cambias el ejemplo ReservaSalas

ReservaSalas es el hilo conductor: sus principios, requisitos (RF-001 a RF-012) y criterios de éxito (CE-001 a CE-004) se citan en muchos documentos, diagramas y ejercicios. La versión de referencia está en [ejercicios/soluciones/03-reserva-salas/](ejercicios/soluciones/03-reserva-salas/README.md). Si cambias algo de ella, busca el identificador en todo el repositorio (con el buscador de GitHub o, en tu ordenador, con `grep -rn "RF-006" .`) y actualiza todos los sitios donde aparece. Lo mismo vale para el ejemplo de solicitud de vacaciones.

## Antes de enviar

- [ ] Lo entendería alguien que no programa (o el nivel de la cabecera avisa de que es técnico).
- [ ] Tiene la cabecera, «En tres frases», «Siguiente paso» y la línea de navegación.
- [ ] Los enlaces funcionan: los has probado en la vista previa.
- [ ] Los diagramas se dibujan en la vista previa y, si son de `diagramas/`, sus imágenes están regeneradas.
- [ ] Los comandos están copiados de la documentación oficial de la herramienta, con su versión.
- [ ] Si has tocado ReservaSalas o las vacaciones, has revisado los ficheros que los citan.
- [ ] No hay ningún dato real.

## Qué no incluir

- Datos reales de clientes, de personas de la plantilla o de proyectos, ni capturas que los muestren.
- Nombres de personas reales en los ejemplos: usa los personajes ficticios.
- Contraseñas, claves, direcciones internas o cualquier información que no deba salir de la empresa.
- Material de terceros copiado sin permiso, ni enlaces a cursos o vídeos externos como si fueran parte del material. Las fuentes que citamos son la documentación oficial de las herramientas y el método EARS.
- Promesas («elimina todos los errores») y cifras que no puedas respaldar.

## En tres frases

1. Cualquiera puede mejorar este material: con una incidencia, editando en la web de GitHub o con una *pull request*, y siempre con la revisión de otra persona.
2. Lo que más se cuida es que se entienda sin saber programar: tono cercano, terminología fija, la misma estructura en todos los documentos y diagramas que se explican también con texto.
3. ReservaSalas es el hilo conductor: si lo cambias, cambia todos los sitios donde se cita, y nunca incluyas datos reales.

## Siguiente paso

Vuelve a la [portada](README.md) o abre una incidencia con lo primero que te gustaría mejorar.

---

🏠 [Portada](README.md)
