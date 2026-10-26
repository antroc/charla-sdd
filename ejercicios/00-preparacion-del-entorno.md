# Ejercicio 00: preparación del entorno

> **Para quién:** cualquier persona (vía A) y quien vaya a construir con Spec Kit (vía B) · **Tiempo de lectura:** ~8 min · **Tiempo para hacerlo:** 10-40 min · **Nivel:** 🟡 intermedio

Este ejercicio solo prepara el terreno. Puedes seguir el curso de dos formas: con las plantillas del repositorio, sin instalar nada, o con Spec Kit y el asistente de programación que tenga autorizado tu organización.

El ejercicio no presupone una marca concreta. No contiene claves de integración, rutas internas ni comandos de arranque propios de un asistente.

**Qué vas a encontrar**

- [Objetivo](#objetivo)
- [Qué necesitas](#qué-necesitas)
- [Convención neutral](#convención-neutral)
- [Vía A: sin instalar nada](#vía-a-sin-instalar-nada)
- [Vía B: con Spec Kit](#vía-b-con-spec-kit)
- [Uso responsable](#uso-responsable)
- [Errores frecuentes](#errores-frecuentes)
- [Comprueba lo que has aprendido](#comprueba-lo-que-has-aprendido)
- [Solución o ejemplo resuelto](#solución-o-ejemplo-resuelto)
- [En tres frases](#en-tres-frases)
- [Siguiente paso](#siguiente-paso)

## Objetivo

Al terminar tendrás preparado uno de estos dos entornos:

- **Vía A:** un documento y las plantillas necesarias para especificar y revisar sin código.
- **Vía B:** Git, Python, Spec Kit y un proyecto de prueba abierto en cualquier asistente compatible.

## Qué necesitas

| | Vía A | Vía B |
|---|---|---|
| Ejercicios | 01, 02, 04 y 05 | 03 y 06, además de los anteriores |
| Conocimientos | Ninguno | Saber abrir una terminal y un proyecto |
| Materiales | Documento o editor de texto; plantillas | Git, Python 3.11 o superior, un gestor de herramientas de Python, Spec Kit y un asistente autorizado |
| Tiempo | 10 min | 25-40 min |

## Convención neutral

A lo largo de los ejercicios aparecen acciones como `constitution`, `specify`, `clarify`, `plan` o `tasks`. Cada asistente puede mostrarlas con una sintaxis distinta. Usa la acción equivalente que aparezca en tu herramienta.

Los *prompts* están separados de la acción. Si tu asistente permite pasar texto junto con el comando, puedes hacerlo; si no, ejecuta primero la acción y pega el texto cuando te lo pida. El resultado esperado no cambia.

## Vía A: sin instalar nada

1. **Elige dónde vas a escribir.** Puede ser un documento compartido, un editor de texto o papel. Crea un documento llamado `Ejercicio 01 - Solicitud de vacaciones`.

   - [ ] Tengo un sitio donde escribir y revisar comentarios.

2. **Copia las plantillas.** Abre [especificacion.md](plantillas/especificacion.md) y [lista-de-verificacion.md](plantillas/lista-de-verificacion.md). Copia su contenido en tu documento o descárgalas junto con el repositorio.

   Qué deberías ver: títulos como «Resumen», «Historias de usuario», «Requisitos», «Criterios de éxito» y «Aclaraciones».

   - [ ] Tengo las dos plantillas disponibles.

3. **Decide si vas a usar un chat de IA.** Es opcional. Si lo usas, debe estar autorizado por tu organización. Comprueba que entiende este encargo:

   ```text
   Voy a escribir una especificación de software en lenguaje natural. Cuando te la pase, hazme preguntas de aclaración de una en una. No propongas tecnología ni reescribas todo el documento. Confirma en una sola frase que lo has entendido.
   ```

   - [ ] Sé qué herramienta puedo usar o he decidido trabajar sin asistente.

Con esto la vía A está terminada.

## Vía B: con Spec Kit

Los comandos de esta sección se ejecutan en una terminal. La salida exacta puede cambiar entre versiones; comprueba el sentido, no el texto literal.

1. **Comprueba las herramientas base.**

   ```bash
   git --version
   python3 --version
   uv --version
   ```

   En Windows, el comando de Python puede ser `python --version`. Necesitas Python 3.11 o superior. Si alguna herramienta falta, instala la versión aprobada por tu organización.

   - [ ] Git, Python y `uv` responden con una versión.

2. **Prepara un asistente de programación.** Instala o abre el que tenga autorizado tu organización siguiendo su documentación oficial o la guía interna de IT. No hace falta adaptar el ejercicio a una marca concreta.

   Qué deberías comprobar: puede abrir una carpeta como proyecto, leer ficheros del repositorio, proponer cambios y ejecutar pruebas con tu permiso.

   - [ ] El asistente abre un proyecto y responde.

3. **Instala Spec Kit.**

   ```bash
   uv tool install specify-cli
   specify version
   ```

   Si ya estaba instalado, basta con comprobar la versión. Si tu empresa usa otro gestor de herramientas de Python, utiliza el procedimiento corporativo equivalente.

   - [ ] `specify version` responde.

4. **Comprueba el entorno.**

   ```bash
   specify check
   ```

   Qué deberías ver: Spec Kit termina la comprobación sin errores bloqueantes. No es necesario que la salida coincida palabra por palabra con la solución.

   - [ ] La comprobación termina correctamente.

5. **Crea un proyecto de prueba sin fijar una integración en el comando.**

   ```bash
   specify init prueba-sdd
   cd prueba-sdd
   ```

   Cuando Spec Kit pregunte qué asistente vas a usar, selecciona el que tengas disponible. Acepta el tipo de scripts recomendado para tu sistema operativo.

   Qué deberías tener: una carpeta `prueba-sdd` con la infraestructura de Spec Kit y las plantillas del flujo. La carpeta concreta que use el asistente no forma parte del ejercicio y no se valida.

   - [ ] Existe `prueba-sdd` y contiene la infraestructura de Spec Kit.

6. **Abre el proyecto en tu asistente.** Comprueba que puedes invocar estas acciones, con la sintaxis que use tu herramienta:

   ```text
   constitution
   specify
   clarify
   plan
   checklist
   tasks
   analyze
   implement
   converge
   ```

   No ejecutes todavía el flujo. Solo verifica que las acciones están disponibles. Si tu asistente no las presenta como comandos, consulta la integración que haya generado Spec Kit o usa las plantillas manualmente.

   - [ ] Puedo localizar las nueve acciones del flujo.

7. **Guarda el punto de partida con Git.** Es recomendable, aunque Spec Kit no lo hace por ti.

   ```bash
   git init
   git add -A
   git commit -m "Preparar proyecto SDD"
   ```

   - [ ] El proyecto tiene un primer commit o he decidido conscientemente no usar Git en los ejercicios.

## Uso responsable

> [!WARNING]
> No uses datos reales de clientes ni de personas de la plantilla. Todos los nombres, correos, cifras y documentos de los ejercicios deben ser ficticios.

Revisa siempre antes de autorizar que un asistente instale dependencias, ejecute comandos o modifique muchos ficheros. El asistente propone; tú decides.

## Errores frecuentes

| Síntoma | Causa probable | Cómo corregirlo |
|---|---|---|
| `specify` no se reconoce | La herramienta no está instalada o la terminal no ha recargado el `PATH` | Cierra y abre la terminal; revisa la instalación corporativa |
| `specify check` encuentra avisos | Alguna herramienta opcional no está disponible | Comprueba solo si el aviso bloquea el asistente que has elegido |
| El proyecto se crea, pero no aparecen las acciones SDD | El asistente se abrió antes de crear el proyecto o fuera de su carpeta | Cierra y vuelve a abrir el proyecto desde `prueba-sdd` |
| El asistente propone tecnología en la vía A | No se ha acotado su papel | Repite: «solo preguntas de aclaración; sin tecnología» |
| El repositorio contiene datos reales | Se ha copiado un caso de trabajo sin anonimizar | Borra los datos, invalida cualquier secreto y usa ejemplos ficticios |

## Comprueba lo que has aprendido

1. ¿Hace falta instalar algo para escribir una especificación?
2. ¿Por qué el ejercicio no fija una clave de integración concreta?
3. ¿Qué se valida: la carpeta interna del asistente o los artefactos que produce?
4. ¿Spec Kit crea automáticamente un repositorio Git?
5. ¿Puedes usar datos reales para que el ejemplo sea más realista?

<details><summary>Ver respuestas</summary>

1. No. Con la vía A bastan un documento y las plantillas.
2. Porque el flujo debe funcionar con cualquier asistente compatible y la configuración cambia entre herramientas y versiones.
3. Se validan las acciones disponibles y los artefactos resultantes, no la carpeta interna ni el prefijo de los comandos.
4. No. Si quieres historial, inicializa Git tú.
5. No. Usa siempre datos ficticios o anonimizados con autorización expresa.

</details>

## Solución o ejemplo resuelto

Compara tu resultado con [la solución del ejercicio 00](soluciones/00-preparacion-del-entorno-resuelta.md). La solución describe estados observables y evita capturas, rutas y configuraciones específicas de una herramienta.

## En tres frases

1. Para especificar no necesitas instalar nada; para construir, prepara Spec Kit y cualquier asistente compatible.
2. El ejercicio valida acciones y resultados, no la sintaxis ni las carpetas internas de una marca.
3. Git y el uso de datos ficticios te permiten revisar y repetir el flujo con seguridad.

## Siguiente paso

Si sigues la vía A, continúa con [Tu primera especificación sin código](01-tu-primera-especificacion-sin-codigo.md). Si sigues la vía B, también conviene hacer primero el ejercicio 01 antes de pasar a [ReservaSalas paso a paso](03-reserva-salas-paso-a-paso.md).

---

🏠 [Índice de ejercicios](README.md)
