# 🧪 Actividad 1.7: Simula una empresa y ejecuta Sprints en Jira

!!! info "Objetivo"
    Aplicar **Scrum real** en Jira Cloud: crear un producto ficticio, organizar el trabajo en historias de usuario y ejecutar uno o dos sprints completos con sus reuniones y actas.

---

## Parte A. Monta la "empresa" y prepara Jira

<div class="tabs-colored" markdown>

=== "Presencial (grupos de 3–5, 2 sprints)"

    **1. Define la empresa**

    - Elegid nombre de empresa y producto (app, web o bot).
    - Definid **dos hitos**, uno por sprint. Por ejemplo:
        - Sprint 1 → "El usuario puede explorar el catálogo y ver el detalle de un producto."
        - Sprint 2 → "El usuario puede añadir al carrito y confirmar un pedido."

    **2. Configura Jira Cloud** (*proyecto Scrum administrado por el equipo*)

    - Columnas del tablero: `Por hacer → En curso → Revisar/QA → Hecho`
    - Establece un límite **WIP** para cada columna (cuántas tarjetas pueden estar a la vez).
    - Cread **Épicas** (3–6 agrupaciones grandes) e **Historias** (8–12) con criterios de aceptación en formato *Given / When / Then*.
    - Estimad con **Story Points** y priorizad el Backlog (tened en cuenta valor para el usuario, riesgo y dependencias entre historias).

=== "Semipresencial (individual, 1 sprint)"

    **1. Define la empresa**

    - Elige nombre de empresa y un producto mínimo viable (**MVP**) con un único hito alcanzable en un sprint.

    **2. Configura Jira Cloud**

    - Columnas: `Por hacer → En curso → Revisar/QA → Hecho` con límites WIP.
    - **Épicas** (1–2) e **Historias** (5–7) con criterios *Given / When / Then*.
    - Estima y ordena el Backlog pensando solo en el hito único.

</div>

!!! tip "Plantilla para historias de usuario"
    ```
    Como <tipo de usuario>
    quiero <acción que realiza>
    para <beneficio que obtiene>
    ```
    Criterios de aceptación:
    ```
    Dado que <contexto de partida>
    Cuando <acción del usuario>
    Entonces <resultado observable y medible>
    ```

---

## Parte B. Sprint 1 — planificación, ejecución y cierre

### Sprint Planning
- En Jira → *Backlog*: crea el sprint y arrastra historias hasta llenar la **capacidad del equipo** (suma de puntos).
- Escribe el **Objetivo de Sprint** en la cabecera: una frase que describa el valor que aporta al usuario al final del sprint.
- En las historias más importantes, añade **subtareas** técnicas (UI, API, base de datos, pruebas).

### Ejecución y Dailies
- Cada sesión de trabajo (o día): abre el tablero, mueve las tarjetas según el estado real, señala **impedimentos** con la bandera (⚑) y ajusta el WIP si es necesario.
- Registra un acta de Daily por cada sesión (ver plantilla más abajo).

### Cierre del sprint
- **Sprint Review**: haz una demo del incremento conseguido. Usa el **Sprint Report** de Jira como evidencia.
- **Retrospectiva**: identifica 1–2 mejoras del proceso. Si hay Sprint 2, crea un issue en Jira con cada mejora para no olvidarla.

---

## Parte C. Sprint 2 (solo presencial)

- Refinad el Backlog con el feedback recibido en la Review del Sprint 1.
- Nuevo Planning con objetivo realista y capacidad revisada.
- Aplicad durante la ejecución al menos una de las mejoras de la retrospectiva anterior.
- Cierre con Review (demo + Sprint Report) y Retrospectiva (¿se aplicó la mejora? ¿qué se haría diferente en un Sprint 3?).

!!! note "Semipresencial"
    No hay Sprint 2. En su lugar, incluye al final del sprint único una sección de **lecciones aprendidas**: qué cambiarías si lo repitieras.

---

## Roles

<div class="tabs-colored" markdown>

=== "Presencial"
    Asignad los roles al inicio: **Product Owner** (decide qué se hace y en qué orden), **Scrum Master** (facilita las reuniones y elimina obstáculos) y **Equipo de desarrollo** (construye el incremento). Podéis rotarlos entre sprints.

=== "Semipresencial"
    Asumes los tres roles tú solo. En las actas, indica explícitamente qué decisiones tomas como PO (priorización) y cuáles como SM (proceso), para demostrar que distingues los dos sombreros.

</div>

---

## Actas — plantillas de referencia

Estas plantillas están incluidas en el documento de entrega. Úsalas como guía mínima; puedes ampliarlas.

**Planning** (una por sprint)
```
Objetivo de sprint: <impacto para el usuario>
Capacidad: <puntos totales> | Historias incluidas: <PROY-001, PROY-002, ...>
Criterios de éxito: <cómo sabréis que el objetivo se ha cumplido>
Riesgos identificados: <...>
```

**Daily** (una por sesión de trabajo)
```
Ayer: <qué se avanzó>  |  Hoy: <qué se va a hacer>  |  Bloqueos: <...>
Movimientos en Jira: <historia → columna nueva>
```

**Review**
```
Incremento demostrado: <qué se mostró>
Feedback recibido: <...>
Decisiones: <historias nuevas, cambios de prioridad>
```

**Retrospectiva**
```
Qué fue bien: <...>
Qué mejorar: <...>
Compromiso para el siguiente sprint: <issue de Jira creado>
```

---

## Entregable

!!! note "Plantilla"
    Completa la plantilla disponible en [plantillas/Actividad_1_7_Plantilla.docx](plantillas/Actividad_1_7_Plantilla.docx) y entrégala exportada como **PDF** en el Aula Virtual.

!!! warning "Criterio de evaluación"
    Las capturas deben ser reales (tablero de Jira con tarjetas movidas, Sprint Report con datos). Un Backlog vacío o con historias sin criterios de aceptación no demuestra que se ha ejecutado el sprint.

---

## Rúbrica orientativa

| Criterio | Insuficiente | Aceptable | Notable | Excelente |
|---|---|---|---|---|
| Backlog y estimación | Sin criterios ni puntos | Historias con criterios básicos | Bien priorizado y estimado | Completo, trazable por épicas |
| Ejecución en Jira | Pocas evidencias | Flujo básico en tablero | WIP respetado, impedimentos marcados | Evidencias claras de cada sesión |
| Reuniones y actas | Incompletas o vacías | Todas presentes con lo mínimo | Claras y con decisiones reales | Las actas guían el sprint siguiente |
| Informes Jira | No hay | Sprint Report presente | Sprint Report + comentarios | Se usó para decidir ajustes de alcance |
| Mejora continua | No aparece | 1 mejora mencionada | 1–2 mejoras aplicadas | Mejora aplicada y evaluada |
