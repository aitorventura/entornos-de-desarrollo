<a id="analizadores"></a>

# 🔎 3. Analizadores de código: revisión estática y configuración

![Analizadores de código](diapositivas/analizadores.pdf){ type=application/pdf style="width:100%;min-height:80vh" }

!!!info "Descarga de diapositivas"
    [Descarga las diapositivas](diapositivas/analizadores.pdf){target="_blank" rel="noopener"}

---

## 🎯 Idea clave

Un **analizador de código** es una herramienta que revisa el código para detectar:

- **errores probables** (bugs típicos),
- **malas prácticas**,
- problemas de **estilo** y **mantenibilidad**,
- y a veces problemas de **rendimiento** o **seguridad básica**,

sin ejecutar el programa. A esto se le llama **análisis estático**.

> Te ayuda a “ver” problemas antes de compilar/ejecutar y a mantener una calidad consistente en el proyecto.

---

## 🧠 ¿Qué es la revisión estática?

La **revisión estática** (static analysis) consiste en analizar el código fuente:

- leyendo estructuras (clases, métodos, variables),
- revisando patrones comunes de error,
- comprobando reglas de estilo,
- calculando métricas simples (por ejemplo, métodos demasiado largos).

```mermaid
flowchart TB
  A[Escribes código] --> B[Analizador estático]
  B --> C[Avisos: errores probables / estilo / calidad]
  C --> D[Corriges o justificas]
  D --> A
```

---

## ✅ ¿Por qué se usan en proyectos reales?

<div class="grid cards" markdown>
-   :material-shield-check-outline: **Prevención de bugs**
    - Detectan fallos típicos antes de ejecutar

-   :material-format-paint: **Estilo uniforme**
    - Todo el equipo sigue las mismas reglas

-   :material-wrench-outline: **Mantenibilidad**
    - Código más fácil de leer y modificar

-   :material-source-branch: **Trabajo en equipo**
    - Menos discusiones: “lo decide la regla”
</div>

---

## 🧾 Qué tipos de problemas detectan

### 1) Errores probables (bugs típicos)

Ejemplos:

- variables que pueden ser `null`
- condiciones redundantes
- comparaciones peligrosas
- código que nunca se ejecuta

```java
String rol = null;

// ❌ Puede lanzar NullPointerException
if (rol.equals("ADMIN")) {
    System.out.println("Es admin");
}

// ✅ Forma segura (evita NPE)
if ("ADMIN".equals(rol)) {
    System.out.println("Es admin");
}
```

---

### 2) Código muerto o innecesario

```java
int x = 10;
x = 10; // redundante
System.out.println(x);
```

Un analizador puede avisar de asignaciones redundantes, variables sin uso, etc.

---

### 3) Estilo y convenciones

Ejemplos:

- nombres mal formados,
- llaves, indentación,
- longitud de línea,
- imports innecesarios.

Esto no suele “romper” el programa, pero mejora la lectura y consistencia.

---

### 4) Complejidad y mantenibilidad

Ejemplos:

- métodos demasiado largos,
- demasiados `if`/`else`,
- duplicación de código.

!!! tip "Señal típica"
    Si un método tiene 80–100 líneas, probablemente necesita refactorización.

---

## 🧰 Herramientas habituales (Java)

En entornos Java, es común ver varias herramientas. Cada una tiene su punto fuerte, aunque hay bastante solape entre ellas:

| Herramienta | Qué detecta principalmente | Cuándo usarla |
|---|---|---|
| **IntelliJ Inspections** | NPE probables, código muerto, estilo, simplificaciones | Siempre: ya viene integrada en el IDE |
| **Checkstyle** | Convenciones de estilo: nombres, longitud de línea, imports | Cuando el equipo quiere un estilo uniforme definido en fichero de reglas |
| **PMD** | Malas prácticas: código duplicado, variables sin usar, complejidad excesiva | Cuando se quiere analizar calidad de diseño más allá del estilo |
| **SpotBugs** | Bugs típicos por patrones: comparaciones peligrosas, recursos sin cerrar, NPE | Cuando se quiere detectar errores reales, no solo estilo |

!!! info “Para el día a día”
    En clase, con **IntelliJ Inspections** y **SonarLint** tienes más que suficiente. Las otras aparecen en proyectos de empresa integradas en el pipeline de CI.

---

## 🛠️ Cómo se ven los avisos en IntelliJ

Cuando IntelliJ detecta un posible problema, lo señala de varias formas visibles sin que tengas que hacer nada:

- **Subrayado en el editor**: líneas con subrayado amarillo (warning) o rojo (error probable) directamente sobre el código.
- **Bombilla a la izquierda**: aparece al situar el cursor en una línea con aviso; haz clic para ver las opciones de solución rápida (*quick fix*).
- **Panel lateral derecho**: la barra de scroll muestra marcas de colores (rojo, amarillo) que indican en qué línea del archivo hay problemas, sin tener que desplazarte.
- **Indicador en la esquina superior derecha**: muestra el número total de problemas del archivo con un icono de estado (verde = sin avisos, amarillo/rojo = hay algo que revisar).

Para lanzar un análisis de todo el proyecto en vez de solo el archivo actual:

**Analyze → Inspect Code** → elige el ámbito (archivo, módulo o proyecto) → verás un informe con los problemas agrupados por categoría.

### Acciones típicas

- Aplicar un *quick fix* con `Alt + Enter` (Windows/Linux) o `Option + Enter` (Mac) en la línea subrayada.
- Ejecutar inspecciones del proyecto con **Analyze → Inspect Code**.
- Revisar advertencias por severidad en el panel de resultados.

!!! tip “Buena práctica”
    No aceptes *quick fixes* “a ciegas”. Entiende qué cambia y por qué. Algunos arreglos automáticos pueden alterar el comportamiento si no lees bien la sugerencia.

---

## ⚙️ Configuración: qué se puede ajustar

Los analizadores se configuran para adaptarlos al proyecto. Lo habitual:

<div class="grid cards" markdown>
-   :material-alert: **Severidad**
    - Error / Warning / Info
    - Priorizar lo importante

-   :material-filter-outline: **Reglas activas**
    - Activar/desactivar comprobaciones
    - Elegir qué reglas se aplican

-   :material-folder-remove-outline: **Exclusiones**
    - No analizar `build/`, `target/`, código generado
    - Evitar “ruido” innecesario

-   :material-file-document-outline: **Estándar del proyecto**
    - Reglas compartidas (config en repo)
    - Misma configuración para todo el equipo
</div>

---

## 🧪 Ejemplo: una regla típica y su intención

### Regla: “evitar números mágicos”

```java
// ❌ Antes: nadie sabe qué significa 8
if (password.length() < 8) {
    System.out.println("Contraseña corta");
}

// ✅ Después: intención clara
final int MIN_PASSWORD_LENGTH = 8;
if (password.length() < MIN_PASSWORD_LENGTH) {
    System.out.println("Contraseña corta");
}
```

---

## ✅ Cómo trabajar con avisos sin volverte loco

1. **Prioriza**:

    - primero errores probables,
    - luego warnings,
    - y por último estilo.

2. **Reduce ruido**:

    - excluye carpetas que no deben analizarse,
    - desactiva reglas que no aplican al proyecto (con criterio).

3. **Acordad reglas en equipo**:

    - lo ideal es que la configuración esté en el repositorio.

!!! warning "Antipatrón"
    Ignorar todos los avisos porque “molestan”.  
    Mejor tener pocos avisos bien elegidos que cien avisos inútiles.

---

---

## 🔍 SonarLint: análisis estático directamente en el IDE

En el tema de entornos de desarrollo instalamos el plugin **SonarLint** en IntelliJ. Es un analizador estático que funciona directamente dentro del editor, sin necesidad de ejecutar el proyecto.

Lo que hace SonarLint:

- marca avisos directamente en el editor (**bugs probables**, **malas prácticas** y **código mejorable**),
- propone *quick fixes* para los problemas más comunes,
- muestra una explicación del problema y por qué es un riesgo,
- y ayuda a mantener un estilo y calidad más constantes en el proyecto.

### Flujo de uso con SonarLint

```mermaid
flowchart LR
  A[Instalar plugin SonarLint en IntelliJ] --> B[Abrir un archivo .java]
  B --> C[Ver avisos subrayados en el editor]
  C --> D[Revisar el panel SonarLint en la parte inferior]
  D --> E[Decidir: corregir / refactorizar / justificar que no aplica]
```

El panel de SonarLint (pestaña inferior del IDE) muestra los avisos del archivo actual con una descripción del problema, la regla que lo detecta y una explicación de por qué es un problema real.

!!! tip “Idea importante”
    SonarLint no “arregla el programa por ti”. Te da señales para que tú decidas si corriges el problema, refactorizas, o justificas por qué en ese caso concreto no aplica. Un aviso es una pregunta, no una orden.