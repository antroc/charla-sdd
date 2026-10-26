# Ejercicio 00 resuelto: así debería quedar tu entorno

> **Para quién:** cualquier persona que haya hecho el ejercicio 00 · **Tiempo de lectura:** ~7 min · **Nivel:** 🟡 intermedio

El [ejercicio 00](../00-preparacion-del-entorno.md) no tiene una solución que comparar con un texto: su resultado es tu entorno. Esta referencia describe cómo debería quedar para que te lo compruebes tú mismo: primero la vía A, sin instalar nada, y después la vía B, con GitHub Spec Kit. No repite los pasos: cada comprobación dice qué deberías ver y qué hacer si no lo ves, y enlaza al paso del ejercicio.

> [!NOTE]
> Es un ejemplo de cómo debería quedar tu entorno, no la única respuesta correcta. Las salidas cambian con las versiones de `uv`, de Spec Kit y de tu asistente de IA: manda lo que diga tu terminal y la [documentación oficial de Spec Kit](https://github.github.io/spec-kit/). Lo que aquí se marca como «orientativo» es un resumen fiel de lo que imprime Spec Kit 1.x, no una captura de pantalla.

**Qué vas a encontrar**

- [Vía A: sin instalar nada](#vía-a-sin-instalar-nada)
- [Vía B: con Spec Kit](#vía-b-con-spec-kit)
- [El árbol de carpetas del proyecto de prueba](#el-árbol-de-carpetas-del-proyecto-de-prueba)
- [Los nueve comandos del asistente](#los-nueve-comandos-del-asistente)
- [Tu lista final de comprobación](#tu-lista-final-de-comprobación)
- [Las tres confusiones más frecuentes](#las-tres-confusiones-más-frecuentes)
- [En tres frases](#en-tres-frases)
- [Siguiente paso](#siguiente-paso)

## Vía A: sin instalar nada

Son los pasos 1 a 3 del [ejercicio](../00-preparacion-del-entorno.md#pasos-de-la-vía-a-sin-instalar-nada). Al terminar deberías tener:

- **Un documento propio** con el título «Ejercicio 01: Solicitud de vacaciones», en un sitio al que puedas volver mañana (un documento compartido, un editor de texto o un cuaderno).
- **Las dos plantillas pegadas con formato** en ese documento: la de [especificación](../plantillas/especificacion.md) y la de [lista de verificación](../plantillas/lista-de-verificacion.md). Se reconocen por sus secciones como títulos («Resumen», «Historias de usuario y escenarios», «Requisitos», «Criterios de éxito»; en la lista, «Calidad del contenido», «Completitud de los requisitos»…), por los ejemplos de ReservaSalas entre corchetes `[…]` y por la ayuda en cursiva bajo cada título («Qué se escribe: … · Para quién: … · Consejo: …»), que borrarás al terminar. Si te faltan los corchetes o las ayudas, repite la copia desde la vista normal de GitHub, sin pulsar «Raw».
- **Opcional, un chat de IA autorizado** que has probado (paso 3). Solo el que autorice la empresa y solo con datos ficticios, como pide el [uso responsable](../00-preparacion-del-entorno.md#uso-responsable-de-los-asistentes-de-ia).

El *prompt* (la instrucción que le escribes al asistente) del paso 3 pide que confirme en una sola frase que ha entendido el encargo: preguntas de aclaración de una en una y ninguna solución técnica. Una respuesta razonable es del estilo de esta; las palabras cambian en cada chat y en cada ocasión:

> Entendido: cuando me pases tu especificación, te haré preguntas de aclaración de una en una y no propondré soluciones técnicas.

Lo que cuenta no son las palabras, sino tres cosas: es una sola frase, confirma el encargo y todavía no hace preguntas ni propone nada. Si empieza a hablar de bases de datos o de lenguajes de programación, no pasa nada: los [errores frecuentes del ejercicio 01](../01-tu-primera-especificacion-sin-codigo.md#errores-frecuentes) explican cómo reconducirlo.

## Vía B: con Spec Kit

Son los pasos 4 a 9 del [ejercicio](../00-preparacion-del-entorno.md#pasos-de-la-vía-b-entorno-completo-con-spec-kit). Los comandos se escriben en una terminal (en Windows, PowerShell). «Orientativo» quiere decir que importa el sentido y no la letra; el remedio detallado de cada fallo está en los [errores frecuentes](../00-preparacion-del-entorno.md#errores-frecuentes) del ejercicio.

| Comprobación | Comando | Qué deberías ver (orientativo) | Si no lo ves |
|---|---|---|---|
| Python 3.11 o superior | `python3 --version` (en Windows, `python --version`) | Una línea `Python 3.x.y` con 3.11 o más; el ejercicio 03 usa la 3.12 | Instala Python desde python.org o pide a IT la versión corporativa; para la 3.12, `uv python install 3.12` |
| `uv` | `uv --version` | Una línea que empieza por `uv` y lleva un número de versión | Instálalo con el comando de tu sistema (paso 4); si no responde justo después, cierra la terminal y ábrela de nuevo |
| Tu asistente | El de tu asistente (`claude`, `gemini`, `codex`, `kiro-cli`…) o abrir tu editor | Arranca, pide iniciar sesión la primera vez (con la cuenta corporativa) y responde a un saludo | Repite la instalación con la guía de IT o la oficial (paso 5) |
| Instalar Spec Kit | `uv tool install specify-cli` | `uv` instala el paquete y termina sin error; ese texto es de `uv`, no de Spec Kit, y cambia con su versión | Con «Permission denied», no uses `sudo`: se instala en tu carpeta de usuario. Si falla por la red o por un certificado, pide a IT su índice privado y pásalo con `--default-index` (paso 6) |
| `specify` responde | `specify version` | El banner «GitHub Spec Kit - Spec-Driven Development Toolkit» y un panel «Specify CLI Information» con `CLI Version` (1.x en la fecha de este material), `Python`, `Platform`, `Architecture`, `OS Version` y, si tu Python lo incluye, `OpenSSL` | Con `specify: command not found`, cierra la terminal y ábrela; si sigue igual, `uv tool update-shell` y vuelve a abrirla |
| Spec Kit ve tu asistente | `specify check` | La lista «Check Available Tools», con un asistente por línea, y al final «Specify CLI is ready to use!» (abajo, un extracto) | Tu asistente sale `not found`: revisa su instalación (paso 5) o añade `--ignore-agent-tools` al `init` |
| Proyecto de prueba | `specify init prueba-sdd --integration claude` (con la clave de tu asistente) | Un selector «Choose script type», la lista de pasos que se completan, `Project ready.` y los paneles «Next Steps» y «Enhancement Skills» (abajo, el detalle) | Mira «Si `specify init` falla», debajo del detalle |

`specify check` no usa la red ni comprueba versiones: solo mira qué ejecutables tienes. Extracto orientativo (la lista real incluye todos los asistentes que Spec Kit conoce y cambia con la versión; en tu terminal `available` sale en verde y `not found` en rojo):

```text
Checking for installed tools...

Check Available Tools
├── ● Claude Code (available)
├── […]
├── ○ GitHub Copilot (IDE-based, no CLI check)
├── ○ Cursor (IDE-based, no CLI check)
├── […]
├── ● Gemini CLI (not found)
├── […]
├── ● Visual Studio Code (available)
└── ● Visual Studio Code Insiders (not found)

Specify CLI is ready to use!
Tip: Run 'specify self check' to verify you have the latest CLI version
```

Esa frase final aparece aunque no encuentre ningún asistente (si no encuentra ninguno de terminal, añade «Tip: Install a coding agent for the best experience»): lo que tienes que mirar es la línea del tuyo, que debe decir `available` o, si es de los que no se buscan (GitHub Copilot, Cursor), `IDE-based, no CLI check`.

Qué ves al ejecutar `specify init prueba-sdd --integration claude`, en este orden (orientativo):

1. El panel «Specify Project Setup» (`Project`, `Working Path`, `Target Path`) y el selector «Choose script type (or press Enter)»: pulsa Intro para aceptar `sh` (en Windows, `ps`).
2. Las líneas `Selected coding agent integration: claude` y `Selected script type: sh`.
3. La lista «Initialize Specify Project», cuyos pasos se van completando: `Check required tools`, `Select coding agent integration`, `Select script type`, `Install integration`, `Install shared infrastructure`, `Ensure scripts executable`, `Constitution setup`, `Install bundled workflow` y `Finalize (project ready)`. En Windows, `Ensure scripts executable` puede quedarse en gris: ese paso no se aplica allí.
4. En verde, `Project ready.`, y un aviso amarillo «Agent Folder Security» que sugiere valorar añadir la carpeta de tu asistente (`.claude/`) al `.gitignore`: es un consejo, no un error.
5. El panel «Next Steps»: ir a la carpeta (`cd prueba-sdd`), arrancar el asistente en ella y usar `/speckit-constitution`, `/speckit-specify`, `/speckit-plan`, `/speckit-tasks`, `/speckit-implement` y `/speckit-converge`.
6. El panel «Enhancement Skills» (con otros asistentes, «Enhancement Commands») con los opcionales `clarify`, `analyze` y `checklist`.

**Si `specify init` falla**

- `Unknown integration`: la clave no es correcta. Copia la de la tabla de [Qué necesitas](../00-preparacion-del-entorno.md#qué-necesitas): `kiro-cli`, no `kiro`.
- Panel «Agent Detection Error»: no encuentra el ejecutable de tu asistente de terminal. Instálalo o añade `--ignore-agent-tools`.
- Panel «Directory Conflict»: ya existe una carpeta `prueba-sdd`. Elige otro nombre o bórrala; con `--force` la mezclaría con lo que ya hay.
- `No such option: --integration`: tu Spec Kit es muy antiguo. Reinstálalo con `uv tool install --force specify-cli` y repite.

## El árbol de carpetas del proyecto de prueba

Así queda `prueba-sdd` tras el `init` con Claude Code y scripts Bash. Es orientativo: la lista exacta cambia con la versión.

```text
prueba-sdd/
├── .specify/                              # carpeta de Spec Kit: plantillas, scripts, constitución y configuración
│   ├── .gitignore                         # qué no guarda Git: feature.json, extensions/*/local-config.yml e integrations/packages*
│   ├── init-options.json                  # opciones de tu init: asistente, tipo de scripts, versión de Spec Kit…
│   ├── integration.json                   # qué asistente es el predeterminado y cuáles hay instalados
│   ├── integrations/                      # manifiestos: listas de los ficheros que Spec Kit ha creado
│   │   ├── speckit.manifest.json          # los compartidos (scripts, plantillas y .gitignore)
│   │   └── claude.manifest.json           # los de tu asistente (con otro, su clave: copilot.manifest.json…)
│   ├── memory/
│   │   └── constitution.md                # constitución sin rellenar, hasta que ejecutes /speckit.constitution
│   ├── templates/                         # las plantillas que usan los comandos
│   │   ├── constitution-template.md       # de la constitución
│   │   ├── spec-template.md               # de la especificación
│   │   ├── plan-template.md               # del plan técnico
│   │   ├── tasks-template.md              # de la lista de tareas
│   │   └── checklist-template.md          # de la lista de verificación
│   ├── scripts/
│   │   └── bash/                          # scripts auxiliares (powershell/ con --script ps, el valor por defecto en Windows)
│   │       ├── check-prerequisites.sh     # comprueba lo que necesita cada comando
│   │       ├── common.sh                  # funciones comunes a los demás
│   │       ├── create-new-feature.sh      # crea la carpeta de una funcionalidad nueva (specs/001-nombre/)
│   │       ├── resolve-template.sh        # localiza la plantilla que toca usar
│   │       ├── setup-plan.sh              # prepara plan.md a partir de su plantilla
│   │       └── setup-tasks.sh             # prepara la lista de tareas
│   └── workflows/
│       ├── workflow-registry.json         # registro de los flujos automatizados instalados
│       └── speckit/
│           └── workflow.yml               # flujo automatizado «speckit»; no hace falta para los ejercicios
└── .claude/                               # carpeta de tu asistente: aquí viven sus comandos
    └── skills/
        ├── speckit-constitution/SKILL.md  # el comando /speckit-constitution
        ├── speckit-specify/SKILL.md       # el comando /speckit-specify
        └── …                              # uno por cada comando
```

Con otro asistente cambia solo la carpeta del final: `.github/skills/` (GitHub Copilot), `.cursor/skills/` (Cursor), `.gemini/commands/` (Gemini CLI), `.agents/skills/` (Codex CLI) o `.kiro/prompts/` (Kiro CLI). Todavía no existen `specs/` ni `.specify/feature.json`: aparecen con el primer `/speckit.specify`, en el [ejercicio 03](../03-reserva-salas-paso-a-paso.md). Tampoco hay carpeta `.git/`: `specify init` no crea un repositorio de Git; si quieres guardar tu trabajo, `git init` dentro de la carpeta es opcional.

## Los nueve comandos del asistente

Se escriben en el chat del asistente, abierto dentro de `prueba-sdd`, no en la terminal. Es la misma orden con tres escrituras posibles; tu asistente te mostrará una sola. Según los asistentes de ejemplo del ejercicio:

- **Con punto** (`/speckit.nombre`): Gemini CLI, Kiro CLI, opencode y Qwen Code.
- **Con guion** (`/speckit-nombre`): Claude Code, GitHub Copilot y Cursor.
- **Con dólar** (`$speckit-nombre`): Codex CLI.

| Comando | Con punto | Con guion | Con dólar | Paso del [flujo](../../docs/03-el-flujo-paso-a-paso.md) |
|---|---|---|---|---|
| `constitution` | `/speckit.constitution` | `/speckit-constitution` | `$speckit-constitution` | 0. Constitución |
| `specify` | `/speckit.specify` | `/speckit-specify` | `$speckit-specify` | 1. Especificar |
| `clarify` | `/speckit.clarify` | `/speckit-clarify` | `$speckit-clarify` | 2. Aclarar |
| `plan` | `/speckit.plan` | `/speckit-plan` | `$speckit-plan` | 3. Planificar |
| `checklist` | `/speckit.checklist` | `/speckit-checklist` | `$speckit-checklist` | 5. Analizar (Spec Kit lo sitúa tras `plan`) |
| `tasks` | `/speckit.tasks` | `/speckit-tasks` | `$speckit-tasks` | 4. Trocear en tareas |
| `analyze` | `/speckit.analyze` | `/speckit-analyze` | `$speckit-analyze` | 5. Analizar (tras `tasks`) |
| `implement` | `/speckit.implement` | `/speckit-implement` | `$speckit-implement` | 6. Implementar |
| `converge` | `/speckit.converge` | `/speckit-converge` | `$speckit-converge` | 6. Implementar (cierre: se repite con `implement` hasta converger) |

Las filas siguen el orden oficial de Spec Kit; nuestro flujo agrupa `checklist` y `analyze` en el paso 5. Dos cosas más que puedes ver: Kimi Code escribe `/skill:speckit-nombre`, y según la versión puede aparecer un décimo comando, `taskstoissues`, obsoleto y fuera del flujo, que no necesitas. La lista completa de asistentes y claves está en [Herramientas](../../docs/07-herramientas.md); el orden de uso en un proyecto real, en [«Cómo se generó»](03-reserva-salas/README.md#cómo-se-generó). No ejecutes ninguno todavía.

## Tu lista final de comprobación

Si solo has hecho la vía A, te bastan las dos primeras casillas. Con la vía B deberías poder marcar las diez.

- [ ] Tengo un documento propio con las plantillas de especificación y de lista de verificación pegadas con formato: secciones como títulos, ejemplos entre corchetes y ayudas en cursiva.
- [ ] Sé qué chat de IA autoriza la empresa (o he decidido hacer los ejercicios sin él) y solo le pego datos ficticios.
- [ ] `python3 --version` (en Windows, `python --version`) responde con Python 3.11 o superior.
- [ ] `uv --version` responde con un número de versión.
- [ ] Mi asistente de programación con IA arranca con la cuenta corporativa, responde a un saludo y tengo apuntada su clave (`claude`, `copilot`, `gemini`…).
- [ ] `specify version` muestra el panel «Specify CLI Information» con un número de versión (1.x en la fecha de este material).
- [ ] `specify check` termina con «Specify CLI is ready to use!» y la línea de mi asistente dice `available` o `IDE-based, no CLI check`.
- [ ] `specify init prueba-sdd --integration` con mi clave termina con `Project ready.` y los paneles «Next Steps» y «Enhancement Skills» (o «Enhancement Commands»).
- [ ] En `prueba-sdd` existen `.specify/` (con `memory/constitution.md`, `templates/`, `scripts/` y `workflows/`) y la carpeta de mi asistente; todavía no hay `specs/`.
- [ ] Con el asistente abierto dentro de `prueba-sdd`, al escribir `/speckit` (o `$speckit`) aparecen los nueve comandos con la escritura de mi asistente, y no he ejecutado ninguno.

## Las tres confusiones más frecuentes

**1. Probar los comandos `/speckit.*` en la terminal.** Síntoma: la terminal no los conoce y responde con un error de «no encontrado» (el texto exacto depende de tu terminal; es orientativo). Remedio: en la terminal solo van los comandos que empiezan por `specify` (`init`, `check`, `version`…); los `/speckit.*`, `/speckit-*` y `$speckit-*` se escriben en el chat del asistente. Para abrirlo, escribe su comando estando en la carpeta del proyecto (`claude`, `gemini`, `codex` o `kiro-cli`) o abre esa carpeta como proyecto en tu editor.

**2. Abrir el asistente fuera de la carpeta del proyecto.** Síntoma: al escribir `/speckit` no aparece ninguna sugerencia. Causa: los comandos viven dentro de `prueba-sdd` y se cargan al arrancar el asistente; si lo abriste en otro sitio, o antes del `init`, no los ve. Remedio: cierra el asistente (o el editor), entra con `cd prueba-sdd` y ábrelo de nuevo desde ahí.

**3. Usar `--ai` en lugar de `--integration`.** Es la bandera de muchos tutoriales antiguos: Spec Kit la declaró obsoleta en la 0.7.1 y la eliminó en la 0.10.0, así que hoy `specify init` falla con un error de opción desconocida (algo como «No such option: --ai»; orientativo). Remedio: escribe `specify init prueba-sdd --integration claude`, con la clave de tu asistente. Y al revés: si lo que da «No such option» es `--integration`, tu Spec Kit es antiguo; reinstálalo con `uv tool install --force specify-cli`.

## En tres frases

1. La vía A está lista cuando tienes tu documento con las dos plantillas pegadas (secciones, ejemplos entre corchetes y ayudas en cursiva) y sabes qué chat de IA puedes usar: para los ejercicios 01, 02, 04 y 05 no hace falta nada más.
2. La vía B está lista cuando Python 3.11 o superior, `uv`, `specify version`, `specify check` y `specify init prueba-sdd --integration` dan algo parecido a lo descrito (las salidas son orientativas: manda tu terminal y la documentación oficial) y existe `prueba-sdd/.specify/` junto a la carpeta de tu asistente.
3. Los comandos `/speckit.*` se escriben en el chat del asistente abierto dentro de la carpeta del proyecto, con `.`, `-` o `$` según tu asistente, y la bandera del `init` es `--integration`, no `--ai`.

## Siguiente paso

Si tu entorno es el de la vía B y las diez casillas están marcadas, sigue con el [ejercicio 03: ReservaSalas paso a paso](../03-reserva-salas-paso-a-paso.md); conviene haber hecho antes el [02](../02-practicar-requisitos-ears.md), que se hace en media hora. Si no vas a instalar nada, empieza por el [ejercicio 01: tu primera especificación sin código](../01-tu-primera-especificacion-sin-codigo.md). Y si alguna comprobación no sale, vuelve a los errores frecuentes del ejercicio 00 antes de seguir.

---

⬅️ [Ejercicio 00](../00-preparacion-del-entorno.md) · 🏠 [Índice de soluciones](README.md)
