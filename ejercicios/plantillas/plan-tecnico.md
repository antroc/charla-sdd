# Plantilla: plan técnico

> *Qué es: **cómo** vamos a construir lo que pide la especificación (tecnología, estructura, datos, contratos y riesgos); sale de la especificación, nunca al revés. · Para quién: lo escribe quien construye (con el asistente de IA) y lo revisa alguien con experiencia técnica; negocio solo necesita leer el resumen y la comprobación contra la constitución. · Consejo: si una sección no aplica, bórrala; un plan corto que se lee entero vale más que uno largo que nadie abre.*

> [!TIP]
> Copia este fichero junto a la especificación, renómbralo `plan.md`, rellena los corchetes y borra este aviso; el título pasa a ser `# Plan técnico: [nombre de la funcionalidad]`.
>
> Con Spec Kit, `/speckit.plan` genera su equivalente (más `research.md`, `data-model.md`, `contracts/` y `quickstart.md`) a partir de la especificación y de la constitución. Esta plantilla sirve para trabajar sin herramientas o para revisar lo que el asistente de IA haya generado; aquí resumimos esos ficheros de apoyo en secciones de este mismo documento.
>
> Aquí sí se habla de tecnología. Pero cada decisión tiene que responder a algo que pide la especificación o la constitución; si no, sobra.
>
> Las ayudas de cada sección van en cursiva, en una cita bajo su título. Bórralas cuando el documento esté listo.

**Carpeta/rama:** `[001-reserva-salas]` · **Fecha:** [AAAA-MM-DD] · **Especificación:** [`spec.md` en esta misma carpeta] · **Entrada:** [especificación de ReservaSalas, aprobada por la responsable de Oficina]

## Resumen

> *Qué se escribe: en 3-5 líneas, el requisito principal y el enfoque técnico elegido. · Para quién: para todo el mundo. · Consejo: que un manager lo entienda sin ayuda.*

[Aplicación web sencilla para ver salas libres, reservar y cancelar. Una sola aplicación en Python con páginas HTML generadas en el servidor y una base de datos en un fichero; sin interfaz compleja y sin más servicio externo que el correo corporativo para los avisos, porque la constitución pide sencillez y la primera versión la usarán unas 200 personas con unas decenas de reservas al día.]

## Contexto técnico

> *Qué se escribe: la ficha técnica del proyecto (lenguaje, dependencias, almacenamiento, pruebas, plataforma, tipo, rendimiento, restricciones y escala); lo que aún no sepas, márcalo NECESITA ACLARACIÓN. · Para quién: para quien construye y para quien mantenga el sistema después. · Consejo: copia aquí los objetivos de rendimiento de los criterios de éxito (CE-004, «menos de 2 segundos») para no perderlos de vista.*

- **Lenguaje y versión:** [Python 3.12]
- **Dependencias principales:** [FastAPI con Uvicorn (servidor) y Jinja2 (plantillas HTML)]
- **Almacenamiento:** [SQLite en un fichero local]
- **Pruebas:** [pytest y httpx (cliente de pruebas de FastAPI)]
- **Servicios externos:** [solo el servidor de correo corporativo, para los avisos (RF-011)]
- **Plataforma de destino:** [servidor Linux interno de la empresa]
- **Tipo de proyecto:** [aplicación web, un solo proyecto]
- **Objetivos de rendimiento:** [listado de disponibilidad en menos de 2 segundos (CE-004)]
- **Restricciones:** [solo red interna; sin integración con el calendario corporativo en la primera versión]
- **Escala y alcance:** [12 salas, unas 200 personas, unas decenas de reservas al día]

## Comprobación contra la constitución

> *Qué se escribe: principio por principio, si el plan lo cumple y cómo. Es una puerta de calidad: si algo no cumple, no se pasa al paso siguiente; o se cambia el plan o se justifica en «Registro de complejidad». · Para quién: para quien revisa, técnico o no; negocio puede leer esta tabla y decir «esto no es lo que acordamos». · Consejo: hazla antes de decidir la tecnología y repítela cuando el diseño esté cerrado.*

| Principio | ¿Cumple? | Cómo |
|---|---|---|
| [1. Sencillez primero] | [Sí] | [Un solo proyecto, sin interfaz aparte, sin colas; el único servicio externo es el correo corporativo.] |
| [2. Accesible y en castellano] | [Sí] | [Páginas HTML simples, textos en castellano, formularios usables con teclado.] |
| [3. Pruebas antes de dar algo por hecho] | [Sí] | [Cada historia empieza con sus pruebas en pytest.] |
| [4. Datos mínimos] | [Sí] | [El modelo solo guarda nombre, correo y reservas.] |
| [5. Transparencia] | [Sí] | [Toda reserva tiene una persona responsable y se muestra en el listado.] |

## Decisiones y alternativas

> *Qué se escribe: cada decisión técnica importante, con su justificación y las alternativas que se descartaron (en Spec Kit, research.md). · Para quién: para quien dentro de un año pregunte «¿por qué no usamos X?». · Consejo: tres o cuatro decisiones bien explicadas valen más que diez sin motivo.*

| Decisión | Justificación | Alternativas consideradas |
|---|---|---|
| [SQLite en fichero] | [Volumen pequeño, sin instalación aparte, cumple «sencillez primero».] | [Base de datos en servidor: más potente, pero añade instalación y mantenimiento que no hacen falta.] |
| [HTML generado en el servidor] | [Evita un segundo proyecto de interfaz y herramientas extra.] | [Aplicación de una sola página con un framework de interfaz: descartada por complejidad.] |
| [Correo por el servidor corporativo] | [Cumple los avisos por correo (RF-011) con un sistema que ya existe en la empresa, sin servicios de terceros; en pruebas se simula.] | [Servicio de correo en la nube: datos de personas fuera de la empresa.] |
| [...] | [...] | [...] |

## Estructura del proyecto

> *Qué se escribe: qué carpetas y ficheros existirán. · Para quién: para el asistente de IA y para quien abra el repositorio. · Consejo: rutas reales, no «aquí iría la lógica».*

### Documentación (de esta funcionalidad)

> *Qué se escribe: lo que Spec Kit deja en specs/001-nombre/. · Consejo: sin herramientas, puedes tener solo spec.md, plan.md y tasks.md.*

```text
specs/001-reserva-salas/
├── spec.md              # especificación
├── plan.md              # este fichero
├── research.md          # decisiones y alternativas (aquí resumidas)
├── data-model.md        # modelo de datos (aquí resumido)
├── contracts/           # contratos (aquí resumidos)
├── quickstart.md        # cómo arrancar (aquí resumido)
├── checklists/          # requirements.md (automática) y listas por tema
└── tasks.md             # lo genera el paso siguiente, no este
```

### Código fuente (raíz del repositorio)

> *Consejo: elige una estructura, escribe las rutas reales y borra lo que no uses. La solución del ejercicio 03 usa esta misma estructura, algo más completa; cualquiera de las dos vale.*

```text
reserva-salas/
├── pyproject.toml           # [dependencias: fastapi, uvicorn, jinja2; desarrollo: pytest, httpx]
├── README.md                # [guía de arranque rápido]
├── datos/salas.sql          # [las 12 salas con planta y aforo]
├── src/reservasalas/
│   ├── app.py               # [crea la aplicación y registra las rutas]
│   ├── db.py                # [conexión SQLite, creación de tablas, carga de salas]
│   ├── modelos.py           # [Sala, Reserva, Persona]
│   ├── textos.py            # [todos los mensajes en castellano]
│   ├── servicios/           # [disponibilidad.py: salas libres · reservas.py: solapamientos, límites, permisos · correo.py: avisos]
│   ├── rutas/               # [api.py: operaciones · paginas.py: páginas HTML]
│   └── plantillas/          # [páginas HTML: base.html, disponibilidad.html, mis_reservas.html…]
└── tests/
    ├── conftest.py          # [base de datos temporal, cliente de pruebas, correo simulado]
    ├── unitarias/           # [reglas de negocio]
    ├── contrato/            # [cada operación de la API]
    └── integracion/         # [recorridos completos por historia]
```

**Decisión de estructura:** [Un solo proyecto, porque no hay interfaz separada ni aplicación móvil.]

## Modelo de datos

> *Qué se escribe: las entidades de la especificación, ya con sus campos, tipos y reglas (en Spec Kit, data-model.md). · Para quién: quien construye. · Consejo: cada regla de aquí debe venir de un requisito; cítalo.*

- **Sala:** [nombre (único), planta (1 a 3), aforo, estado (disponible o en mantenimiento, por RF-007)].
- **Reserva:** [sala, persona, inicio, fin, motivo opcional; regla: no puede solapar otra de la misma sala (RF-005)].
- **Persona:** [nombre, correo corporativo (único), rol (empleado o administración, por RF-009 y RF-010)].

## Contratos

> *Qué se escribe: qué «puertas» ofrece el sistema (rutas o pantallas), qué reciben y qué devuelven (en Spec Kit, la carpeta contracts/). · Para quién: quien construye y quien escribe pruebas. · Consejo: en un proyecto pequeño basta una línea por contrato; comprueba que cada requisito de la especificación aparece en alguna fila.*

| Operación | Entrada | Salida | Requisitos que cubre |
|---|---|---|---|
| [Listar salas y disponibilidad] | [fecha, hora de inicio, hora de fin] | [salas libres con planta y aforo] | [RF-001, RF-002] |
| [Crear reserva] | [sala, inicio, fin, motivo opcional] | [confirmación con sala, fecha y hora (y correo de aviso), o motivo del rechazo] | [RF-003, RF-005, RF-006, RF-007, RF-011] |
| [Cancelar o modificar reserva] | [identificador de la reserva y, si se modifica, la nueva franja] | [confirmación, o motivo del rechazo] | [RF-010, RF-0xx] |
| [Mis reservas] | [persona] | [lista de reservas futuras] | [RF-0xx] |
| [Marcar sala en mantenimiento (solo administración)] | [sala, nuevo estado] | [confirmación] | [RF-009] |

## Riesgos

> *Qué se escribe: qué puede salir mal técnicamente y qué haremos. · Para quién: quien construye y quien decide. · Consejo: un riesgo sin medida es solo una preocupación.*

- [Dos reservas simultáneas de la misma sala → comprobar el solapamiento al guardar, no solo al mostrar.]
- [El fichero de datos se pierde → copia de seguridad diaria; el volumen es pequeño.]
- [El servidor de correo no responde → la reserva se guarda igual y el fallo queda anotado en el registro de la aplicación.]

## Arranque rápido

> *Qué se escribe: los comandos para instalar, arrancar y probar (en Spec Kit, quickstart.md). · Para quién: cualquiera que quiera verlo funcionar. · Consejo: pruébalos tú en una carpeta limpia antes de darlos por buenos.*

```bash
# Ejemplo de ReservaSalas: sustituye estos comandos por los de tu proyecto.
uv venv && source .venv/bin/activate   # crear y activar el entorno
uv pip install -e ".[dev]"             # instalar las dependencias
uvicorn reservasalas.app:app --reload  # arrancar; después, abre la dirección que indique en el navegador
pytest                                 # ejecutar las pruebas
```

## Registro de complejidad

> *Qué se escribe: solo las desviaciones que haya encontrado la comprobación contra la constitución. · Consejo: si queda vacío, mejor.*

| Desviación | Por qué es necesaria | Alternativa más simple descartada porque |
|---|---|---|
| [Ninguna] | [...] | [...] |

> *Volver al [índice de plantillas](README.md). Borra esta línea cuando copies la plantilla.*
