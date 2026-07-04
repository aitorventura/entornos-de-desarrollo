# 📝 Actividad 4.4: Análisis estático con IntelliJ y SonarQube for IDE

!!! warning "Descarga la plantilla"
    📄 [Plantilla 4.4 — Análisis estático](plantillas/Actividad_4_4_Plantilla.docx){target="_blank" rel="noopener"}

!!! info "Objetivo"
    Usar las herramientas de análisis estático del IDE de forma crítica, no solo ejecutarlas:

    - Predecir qué avisos va a encontrar el analizador **antes** de ejecutarlo.
    - Interpretar y clasificar los avisos reales: tipo, causa y decisión justificada.
    - Comparar lo que detecta IntelliJ con lo que detecta **SonarQube for IDE**.
    - Explorar qué se puede configurar y por qué importa.

---

## Código a analizar

Copia estas dos clases en tu proyecto IntelliJ como `OrderProcessor.java` y `ReportGenerator.java`. **No las modifiques antes de ejecutar el analizador** — la idea es ver exactamente qué detecta sobre este código.

```java
// OrderProcessor.java
public class OrderProcessor {

    public double calculateTotal(String[] items, int[] quantities) {
        double total = 0;
        for (int i = 0; i <= items.length; i++) {
            total = total + (getPrice(items[i]) * quantities[i]);
        }
        return total;
    }

    public double getPrice(String item) {
        if (item == "BOOK") return 12.50;
        if (item == "PEN")  return 1.99;
        if (item == "BAG")  return 24.00;
        return 0;
    }

    public String getStatus(double total) {
        String status = null;
        if (total > 100) {
            status = "PREMIUM";
        } else if (total > 50) {
            status = "STANDARD";
        }
        return status;
    }

    public void printSummary(String[] items, int[] quantities) {
        double total = 0;
        for (int i = 0; i <= items.length; i++) {
            total = total + (getPrice(items[i]) * quantities[i]);
        }
        System.out.println("Total: " + total);
        System.out.println("Status: " + getStatus(total));
    }
}
```

```java
// ReportGenerator.java
public class ReportGenerator {

    public String generateReport(String[] data) {
        String report = "";
        for (int i = 0; i < data.length; i++) {
            report = report + data[i] + "\n";
        }
        return report;
    }

    public boolean isValid(String input) {
        if (input != null) {
            if (input.length() > 0) {
                if (!input.equals("")) {
                    return true;
                }
            }
        }
        return false;
    }

    public void processData(String[] data) {
        for (int i = 0; i < data.length; i++) {
            String line = data[i];
            if (isValid(line) == true) {
                String result = generateReport(new String[]{line});
                System.out.println(result);
            }
        }
    }

    private String formatDate(int day, int month, int year) {
        return day + "/" + month + "/" + year;
    }
}
```

---

## Contexto

Estas dos clases tienen problemas intencionados de distinta naturaleza. `OrderProcessor` tiene errores que pueden causar fallos en tiempo de ejecución. `ReportGenerator` funciona pero tiene malas prácticas y código innecesariamente complicado.

El objetivo no es que el analizador marque cero avisos. Es que **entiendas cada uno** y tomes una decisión con criterio.

---

## Paso 1 — Predice antes de ejecutar

Antes de lanzar ningún analizador, lee las dos clases con atención y responde por escrito:

1. Mira `OrderProcessor`: ¿ves alguna línea que pueda causar un error en tiempo de ejecución? ¿Cuál y por qué?
2. Mira `ReportGenerator`: ¿qué malas prácticas o código innecesariamente complicado identificas antes de ejecutar el analizador?
3. Para cada clase, escribe **al menos un aviso concreto** que esperas que aparezca. Sé específico: di qué línea, qué detectará y por qué es un problema.

Guarda estas predicciones — las vas a comparar con los resultados reales en el Paso 5.

---

## Paso 2 — Analiza con IntelliJ Inspect Code

En IntelliJ, ve a **Code → Inspect Code** (menú superior).

Se abre un diálogo con dos opciones:

- **Inspection scope**: elige *Whole project* (o el módulo concreto si el proyecto tiene varios).
- **Inspection profile**: deja *Project Default* o *Default* — no cambies nada por ahora.

Haz clic en **OK** y espera. IntelliJ analiza el código y abre el panel **Inspection Results** con los avisos agrupados por categorías (*Probable bugs*, *Code style*, *Performance*, etc.).

!!! tip "Cómo navegar"
    Despliega cada categoría. Haz clic en un aviso para ir directamente a la línea. El panel muestra la descripción del problema — léela entera antes de decidir qué hacer.

### Clasifica y decide — al menos 4 avisos

Para cada aviso que encuentres, rellena la tabla de la plantilla:

| Campo | Qué poner |
|---|---|
| **Tipo** | Bug probable / Código muerto / Mala práctica / Estilo / Complejidad |
| **Descripción** | Qué dice el aviso (copia el texto del panel) |
| **Archivo y línea** | Dónde aparece |
| **¿Por qué lo detecta?** | Explica con tus palabras qué patrón ha detectado y por qué es un problema |
| **Decisión** | Corregir / Justificar que no aplica / Desactivar la regla |
| **Razonamiento** | Por qué has tomado esa decisión |

!!! warning "Lo que no vale"
    Poner "lo he corregido" sin explicar por qué era un problema. O "no aplica" sin justificar. La decisión importa menos que el razonamiento detrás.

---

## Paso 3 — Mismo código, otra herramienta

Abre el mismo proyecto con **SonarQube for IDE** activo (el panel aparece en la parte inferior del IDE). Si no lo tienes instalado: **File → Settings → Plugins → Marketplace → SonarQube for IDE**.

Mira los avisos que genera para los mismos archivos y responde:

1. Anota **al menos 2 avisos que SonarQube for IDE detecta y que IntelliJ no había señalado** (o al revés). Si coinciden todos, compara la calidad de las explicaciones.
2. ¿Las explicaciones de SonarQube for IDE son más detalladas que las de IntelliJ? ¿En qué se nota?
3. Para uno de los avisos que aparece en ambas herramientas: ¿la descripción es la misma o cada una lo explica de forma distinta?

---

## Paso 4 — Experimenta con la configuración

Los analizadores se pueden configurar. Prueba al menos **dos** de estas acciones y documenta qué has cambiado y qué ha pasado:

- **Cambia la severidad** de una regla: en el panel *Inspection Results*, haz clic derecho sobre un aviso concreto → *Edit Inspection Settings* → cambia el nivel de una regla de Warning a Error (o viceversa). Vuelve a ejecutar con **Code → Inspect Code** y observa si el resultado cambia.
- **Excluye una carpeta**: en *Settings → Editor → Inspections*, desactiva una regla concreta. ¿Desaparece del informe?
- **Cambia el ámbito**: ejecuta Inspect Code solo sobre un archivo, luego sobre el proyecto completo. ¿Cuántos avisos más aparecen?

Para cada acción que hayas probado:

| Qué has cambiado | Resultado observado | ¿Tiene sentido en un proyecto real? |
|---|---|---|
| | | |

---

## Paso 5 — Compara predicción vs. realidad

Vuelve a las respuestas del Paso 1 y responde:

1. ¿Cuántos de tus avisos predichos han aparecido realmente? ¿Cuáles no han aparecido y por qué crees que no?
2. ¿Ha aparecido algún aviso que no esperabas? ¿Cuál te ha sorprendido más y por qué?
3. ¿Cuál de las dos clases ha generado más avisos? ¿Coincide con lo que esperabas antes de ejecutar el analizador?

---

## Preguntas de reflexión

1. Después de ver los avisos reales: ¿un analizador estático puede sustituir a una revisión manual del código, o son complementarios? Razona con un ejemplo concreto de esta actividad.
2. Si tuvieras que configurar el analizador para un equipo de 5 personas que acaba de empezar un proyecto, ¿qué tres reglas activarías como prioritarias y por qué? ¿Cuál desactivarías para no generar ruido innecesario?
3. Hay un aviso que IntelliJ señala pero que en tu código concreto no es un problema real. ¿Cómo lo justificarías ante un compañero que insiste en corregirlo?

---

## Entregable

| Qué | Cómo se evalúa |
|-----|----------------|
| Predicciones del Paso 1 (antes de ejecutar) | ¿Son razonadas o son vagas? ¿Demuestran que has leído el código? |
| Tabla de avisos clasificados (Paso 2, mín. 4) | ¿Entiendes qué detecta cada uno? ¿El razonamiento de la decisión es tuyo? |
| Comparación IntelliJ vs SonarQube for IDE (Paso 3) | ¿Has observado diferencias reales o has puesto que "son iguales"? |
| Experimentos de configuración (Paso 4) | ¿Has probado los cambios o los has descrito sin hacerlos? |
| Comparación predicción vs. realidad (Paso 5) | ¿Hay reflexión honesta sobre lo que no acertaste? |
| Respuestas a las preguntas de reflexión | ¿Razonas con ejemplos concretos de esta actividad? |

!!! warning "Corrección oral"
    En la corrección se preguntará por cualquier aviso de la tabla: qué significa, por qué lo has corregido o no, y qué pasaría si lo ignoraras. Si no puedes explicarlo, la actividad no se supera aunque la tabla esté completa.
