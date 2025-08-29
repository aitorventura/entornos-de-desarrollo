# 🧪 Actividad 1.6: Simula una empresa y ejecuta Sprints en **Jira**

!!! info "Objetivo"
    Simular una **empresa** y aplicar **Scrum en Jira Cloud** para entregar un **incremento** verificable.

---

## 🔹 Parte A. Monta la “empresa” y prepara Jira

<div class="tabs-colored" markdown>

=== "Grupo presencial (en grupo, 2 sprints)"
    1. Formad **equipos de 3–5** personas. Elegid **nombre de empresa** y **producto** (web/app/bot).
    2. Definid **2 hitos** (uno por sprint).  
        - *Ejemplo:* Sprint 1 → “Explorar catálogo y ver detalle”; Sprint 2 → “Añadir al carrito y confirmar pedido”.
    3. En **Jira Cloud** (*Scrum administrado por el equipo*):
        - Columnas: `Por hacer → En curso → Revisar/QA → Hecho`. Elige un **WIP** por columna.
        - Cread **Épicas** (3–6) y **Historias** (8–12) con criterios *Given/When/Then*.
        - Estimad con **Story Points** y **priorizad** el Backlog (valor/risgo/dependencias).

=== "Grupo semipresencial (individual, 1 sprint)"
    1. Elige **nombre de empresa** y un **producto mínimo** (MVP) con **un único hito** alcanzable en 1 sprint.
    2. En **Jira**:
        - Columnas: `Por hacer → En curso → Revisar/QA → Hecho`. Acordad **WIP** por columna.
        - **Épicas** (1–2) y **Historias** (5–7) con criterios *Given/When/Then*.
        - Estima y ordena el **Backlog** (enfocado al hito único).

</div>

**Plantillas rápidas**  
- **Historia**  
  ```
  Como <persona>
  Quiero <acción>
  Para <beneficio>
  ```
- **Criterios**  
  ```gherkin
  Dado <contexto>
  Cuando <acción>
  Entonces <resultado medible>
  ```

---

## 🔹 Parte B. **Sprint 1** (planificación → ejecución → cierre)

1. **Sprint Planning** (Jira → *Backlog*)
    - `Crear sprint` y añadir historias hasta la **capacidad** (usa los puntos).
    - Escribe el **Objetivo de Sprint** en la cabecera (impacto para usuario).
    - Añade **Subtareas** (por ejemplo... UI/API/DB/QA) en las historias clave.
2. **Ejecución + Daily** (Jira → *Tablero*)
    - 10–15’: abre el tablero, **mueve tarjetas**, marca **impedimentos** (⚑) y ajusta el **WIP**.
3. **Cierre**
    - **Sprint review**: demo del incremento usando **Sprint report**.
    - **Retrospectiva**: 1–2 **mejoras** del proceso; crea su issue para el siguiente sprint (si aplica).

---

## 🔹 Parte C. **Sprint 2** (solo presencial)

- Refinad el **Backlog** con el feedback del Sprint 1.  
- **Planning** con nuevo **Objetivo** y capacidad realista.  
- **Ejecución + Dailies** aplicando la(s) mejora(s) de la retro.  
- **Cierre** con Review (demo + Sprint report) y Retro (nueva mejora).

> **Semipresencial (individual):** no hay Sprint 2. Aun así, incluye **lecciones aprendidas** al final del sprint único.

---
##  Roles y organización

- **Presencial:** asignad **PO**, **SM** y **Equipo**; podéis rotar entre sprints.  
- **Semipresencial (individual):** asume los tres roles y **explícita** en las actas qué decisiones tomarías como PO/SM.


## ✅ Entregable

<div class="tabs-colored" markdown>

=== "Grupo presencial"
    Dossier PDF con capturas y actas que incluya:

    1. Ficha de empresa (nombre, producto, objetivos por sprint).  
    2. Backlog (épicas, historias con criterios y estimación).  
    3. Ejecución de **2 sprints**: objetivos, tablero a mitad/fin.
    4. Una **historia ejemplo** abierta con criterios, subtareas...
    5. Actas: Planning, Dailies (resumen), Review y Retro por sprint.  
    6. Conclusiones (puntos completados) + mejoras para un hipotético Sprint 3.

=== "Grupo semipresencial"
    Dossier breve con:

    1. Ficha de empresa y **único objetivo de sprint**.  
    2. Backlog reducido (épicas/historias con criterios y puntos).  
    3. Tablero a mitad/fin. 
    4. Una **historia ejemplo** abierta con criterios, subtareas...
    5. Actas breves (Planning, 2–3 Dailies, Review, Retro).  
    6. Conclusiones y **1 mejora** aplicable a un futuro sprint.

</div>

---

## Actas (plantillas)

**Planning (por sprint)**
```
Objetivo de Sprint: <impacto para usuario>
Capacidad estimada: <puntos> | Historias: <PROY-123, PROY-124, ...>
Criterios de éxito: <métrica/umbral>
Riesgos y mitigación: <...>
```

**Daily (1 línea/persona | individual: 1–2 líneas)**
```
Ayer: <...> | Hoy: <...> | Bloqueos: <...> | Movimientos en Jira: <issue -> columna>
```

**Review**
```
Incremento demostrado: <qué se ha mostrado>
Feedback: <...>
Decisiones: <nuevas historias / cambios>
```

**Retrospectiva**
```
Funcionó bien: <...>
Para mejorar: <...>
Compromisos (próximo sprint): <tarea de mejora de proceso en Jira>
```

---

## 📏 Rúbrica (orientativa)

| Criterio | Insuficiente | Aceptable | Notable | Excelente |
|---|---|---|---|---|
| Backlog y estimación | Desordenado, sin criterios | Historias con criterios básicos | Bien priorizado y estimado | Completo, trazable por épicas/etiquetas |
| Ejecución en Jira | Pocas evidencias | Flujo básico en tablero | Flujo claro con WIP respetado | Evidencias, PR/tests y DoD consistente |
| Reuniones y actas | Incompletas | Todas presentes, simples | Claras y accionables | Guían decisiones; mejoras aplicadas |
| Informes | Faltan | Burndown o Sprint report | Ambos presentes | Uso para decidir y ajustar alcance |
| Mejora continua | No aparece | 1 mejora superficial | 1–2 mejoras aplicadas | Mejora aplicada y observada entre sprints |
