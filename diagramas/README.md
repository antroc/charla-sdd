# Diagramas

> **Para quién:** todos los perfiles (managers, RRHH, negocio y quien programa) · **Tiempo de lectura:** ~3 min · **Nivel:** 🟢 básico

Esta carpeta cuenta con dibujos lo mismo que la [documentación](../docs/README.md): qué problema resuelve SDD (*Spec-Driven Development*, desarrollo guiado por especificaciones), cómo es el flujo, qué documentos produce, quién hace qué y cómo se escribe un buen requisito. Cada fichero explica sus diagramas con texto, para que se entiendan aunque no los veas.

**Qué vas a encontrar**

- [Los seis ficheros](#los-seis-ficheros)
- [Cómo verlos](#cómo-verlos)
- [Versiones para presentaciones](#versiones-para-presentaciones)
- [Cómo cambiar un diagrama](#cómo-cambiar-un-diagrama)

## Los seis ficheros

| Nº | Fichero | Qué muestra | Para quién | Lo desarrolla |
|---|---|---|---|---|
| 01 | [*Vibe coding* frente a SDD](01-vibe-coding-vs-sdd.md) | Los dos caminos, uno al lado del otro: el bucle de parches frente a especificar primero, y una tabla que los compara | Todos | [docs 01](../docs/01-el-problema-del-vibe-coding.md) y [02](../docs/02-que-es-sdd.md) |
| 02 | [Flujo completo de SDD](02-flujo-completo-sdd.md) | El diagrama principal: los siete pasos, el fichero que deja cada uno, quién participa y los bucles de vuelta; y una conversación entre Ana, Luis y el asistente de IA | Todos | [docs 03](../docs/03-el-flujo-paso-a-paso.md) |
| 03 | [Artefactos y relaciones](03-artefactos-y-relaciones.md) | Cómo se alimentan los documentos de SDD entre sí, cómo se sigue un requisito hasta el código y dónde vive cada fichero | Perfiles técnicos y quien quiera saber «qué fichero es cada cosa» | [docs 04](../docs/04-los-artefactos.md) |
| 04 | [Roles y participación](04-roles-y-participacion.md) | Quién lidera y quién revisa en cada paso, y la matriz de responsabilidades | Todos | [docs 06](../docs/06-roles-quien-hace-que.md) |
| 05 | [Anatomía de un requisito EARS](05-anatomia-de-un-requisito-ears.md) | Las piezas de un requisito bien escrito y cómo elegir la plantilla adecuada | Todos | [docs 05](../docs/05-escribir-requisitos-claros-ears.md) |
| 06 | [Mapa del repositorio](06-mapa-del-repositorio.md) | Todas las carpetas y ficheros del repositorio, y el itinerario de lectura de cada perfil | Todos | [Portada](../README.md) |

Si solo vas a mirar uno, que sea el [02, el flujo completo](02-flujo-completo-sdd.md): resume el método entero en una imagen.

## Cómo verlos

Los diagramas están escritos en Mermaid, un formato de texto que GitHub dibuja directamente: abre el fichero en GitHub y los verás como imágenes, sin instalar nada. En tu ordenador también se ven en cualquier editor cuya vista previa de Markdown admita Mermaid.

## Versiones para presentaciones

Cada diagrama está exportado además como imagen, para pegarlo en una presentación o en un documento:

- [`svg/`](svg/README.md): imágenes vectoriales, que se pueden ampliar sin perder calidad. Para PowerPoint, Keynote y documentos.
- [`png/`](png/README.md): imágenes normales, con fondo blanco. Para Google Slides, el correo o un chat.

Los ficheros se llaman como el diagrama del que salen, con un número al final según su orden dentro del fichero: `02-flujo-completo-sdd-1.svg` es el primer diagrama del fichero 02. Se generan automáticamente a partir de los ficheros de esta carpeta, así que no se editan a mano.

## Cómo cambiar un diagrama

Un diagrama es texto dentro de un bloque que empieza por ` ```mermaid `. Para cambiarlo, edita ese texto y comprueba el resultado en la vista previa de GitHub. Después hay que regenerar sus versiones en `svg/` y `png/`. Las reglas para que un diagrama no falle y cómo proponer el cambio están en [CONTRIBUIR.md](../CONTRIBUIR.md).

## Siguiente paso

Empieza por [*Vibe coding* frente a SDD](01-vibe-coding-vs-sdd.md), o por el [mapa del repositorio](06-mapa-del-repositorio.md) si quieres ver primero qué hay en cada sitio.

---

🏠 [Portada del repositorio](../README.md)
