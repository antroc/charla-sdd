# Solución del ejercicio 00: preparación del entorno

> **Para quién:** quien haya preparado la vía A o la vía B · **Tiempo de lectura:** ~6 min · **Nivel:** 🟡 intermedio

Esta solución describe qué debe quedar al terminar el [ejercicio 00](../../00-preparacion-del-entorno.md). No reproduce salidas literales de una versión de Spec Kit ni la configuración interna de un asistente concreto.

## Mínimo esperado

### Vía A

- Un documento o editor donde trabajar.
- Las plantillas de especificación y lista de verificación disponibles.
- La decisión de trabajar sin IA o con un chat expresamente autorizado.

### Vía B

- Git, Python 3.11 o superior y `uv` disponibles.
- Spec Kit instalado y respondiendo.
- Un proyecto `prueba-sdd` creado mediante la selección interactiva del asistente.
- El proyecto abierto en cualquier asistente compatible.
- Las nueve acciones del flujo localizadas: `constitution`, `specify`, `clarify`, `plan`, `checklist`, `tasks`, `analyze`, `implement` y `converge`.
- Un primer commit de Git, salvo que hayas decidido conscientemente no usar control de versiones.

## Criterios de corrección

| Comprobación | Correcto | No se exige |
|---|---|---|
| Herramientas base | Los comandos de versión responden | Una versión exacta salvo Python 3.11 o superior |
| Spec Kit | `specify version` y `specify check` terminan sin errores bloqueantes | Una salida idéntica a la de esta solución |
| Proyecto | Existe la infraestructura de Spec Kit | Una carpeta interna concreta del asistente |
| Integración | El asistente puede localizar las acciones SDD | Un prefijo concreto, una clave o una sintaxis determinada |
| Git | Hay un punto de partida versionado | Un proveedor remoto concreto |
| Seguridad | Solo se han usado datos ficticios | Datos reales para «hacerlo más realista» |

Un aviso sobre una herramienta opcional no invalida el ejercicio. Sí lo invalida que el asistente elegido no pueda trabajar dentro del proyecto o que las acciones SDD no estén disponibles por ningún medio.

## Solución razonada

### 1. Herramientas base

Una comprobación válida puede verse así:

```bash
git --version
python3 --version
uv --version
```

En Windows, Python puede responder con `python --version`. Lo importante es que Git y `uv` estén disponibles y que Python sea 3.11 o superior.

### 2. Spec Kit

```bash
uv tool install specify-cli
specify version
specify check
```

La instalación es correcta si `specify version` devuelve información de la herramienta y `specify check` no muestra errores que impidan usar el asistente elegido. El texto, los colores y la lista exacta pueden variar entre versiones.

### 3. Proyecto de prueba

```bash
specify init prueba-sdd
cd prueba-sdd
```

Durante el proceso se selecciona el asistente disponible y el tipo de scripts recomendado para el sistema operativo. La respuesta correcta no incluye una clave de integración escrita en el ejercicio: esa elección pertenece al entorno local de cada persona.

Al terminar debe existir una carpeta con:

```text
prueba-sdd/
├── infraestructura de Spec Kit
├── plantillas y scripts auxiliares
└── configuración generada para el asistente elegido
```

No se valida el nombre de la carpeta de configuración del asistente, porque cambia entre productos y versiones.

### 4. Acciones disponibles

Dentro del proyecto, el asistente debe poder ofrecer o ejecutar las acciones equivalentes a:

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

Pueden aparecer como comandos, *skills*, agentes, menús o instrucciones. La forma no importa; sí importa que puedan producir los artefactos correspondientes.

### 5. Punto de partida con Git

```bash
git init
git add -A
git commit -m "Preparar proyecto SDD"
```

El objetivo es poder comparar después qué cambia en cada etapa. No hace falta publicar el repositorio.

## Alternativas válidas

- Usar `pipx` u otro mecanismo corporativo en lugar de `uv`, siempre que `specify` quede disponible.
- Trabajar solo con las plantillas si no tienes permisos para instalar herramientas.
- Usar un editor, una herramienta de terminal o un agente remoto compatible.
- Crear el proyecto en un repositorio ya existente, después de guardar un commit limpio y revisar qué ficheros añade Spec Kit.
- No usar IA en los ejercicios sin código.

No es una alternativa válida copiar una configuración de otro asistente y esperar que funcione sin adaptarla al entorno local.

## Errores frecuentes

| Error | Por qué importa | Corrección |
|---|---|---|
| Documentar `--integration` con una clave concreta | Convierte el ejercicio en una receta para una sola herramienta | Usa la selección interactiva |
| Validar `.claude`, `.github`, `.cursor` u otra carpeta | Es un detalle de implementación de la integración | Valida que existan las acciones, no la ruta |
| Exigir `/`, `$` o una ortografía concreta | La sintaxis cambia entre asistentes | Nombra la acción SDD de forma neutral |
| Copiar una salida completa de `specify check` | Se queda obsoleta con facilidad | Describe solo las señales observables |
| Pegar datos reales en el proyecto de prueba | Introduce un riesgo innecesario | Usa nombres y cifras ficticios |

## En tres frases

1. La vía A necesita plantillas; la vía B añade Spec Kit y cualquier asistente compatible.
2. El entorno se considera correcto por lo que permite hacer, no por sus carpetas ni por la sintaxis de una marca.
3. Git y los datos ficticios hacen el ejercicio repetible y seguro.

## Volver al ejercicio

Vuelve a [Preparación del entorno](../../00-preparacion-del-entorno.md) o continúa con [Tu primera especificación sin código](../../01-tu-primera-especificacion-sin-codigo.md).

---

🏠 [Índice de soluciones](../README.md)
