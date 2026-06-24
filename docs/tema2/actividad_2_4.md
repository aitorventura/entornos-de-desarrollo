# 🧪 Actividad 2.4: Generación de ejecutables y comparativa de entornos

## Objetivo

Demostrar que el mismo código fuente Java produce el mismo resultado en dos entornos distintos (IntelliJ IDEA y VSCodium), generar un ejecutable `.jar` y hacer una comparativa razonada de los dos IDEs trabajados en la unidad.

---

## Lo que tienes que entregar

Completa la **plantilla** con las capturas y respuestas de cada apartado, expórtala a PDF y súbela al Aula Virtual con el nombre:

```
A2-4_NombreApellido.pdf
```

!!!warning "Descarga la plantilla"
    📄 [Plantilla 2.4 — Ejecutables y comparativa](plantillas/Actividad_2_4_Plantilla.docx){target="_blank" rel="noopener"}

---

## Resumen de tareas

**A — El mismo código en dos IDEs**

Crea una clase Java `Calculadora` con métodos para suma, resta y multiplicación. Un `main` que los llame e imprima los resultados.

- Abre el proyecto en **IntelliJ IDEA** → compila y ejecuta → captura de la salida en la consola.
- Abre el mismo proyecto en **VSCodium** (sin modificar el código) → compila y ejecuta → captura de la misma salida.

Ambas capturas deben mostrar **el mismo resultado**. Razona brevemente: ¿por qué el resultado es el mismo si el IDE es diferente?

**B — Generar un `.jar` ejecutable**

Desde IntelliJ IDEA, empaqueta el proyecto como `.jar`:

- `File → Project Structure → Artifacts → JAR → From modules with dependencies`
- `Build → Build Artifacts`
- Ejecuta el `.jar` desde la terminal: `java -jar Calculadora.jar`
- Captura de la terminal con la salida correcta.

!!! warning "Error habitual: UnsupportedClassVersionError"
    Si al ejecutar el `.jar` aparece este mensaje:

    ```
    Error: Se ha producido un error de enlace al cargar la clase principal Calculadora
    java.lang.UnsupportedClassVersionError: Calculadora has been compiled
    by a more recent version of the Java Runtime (class file version 69.0),
    this version of the Java Runtime only recognizes class file versions up to 65.0
    ```

    **Qué significa:** el `.jar` se compiló con una versión de Java más moderna (en este caso Java 25, que produce class files versión 69) que la que está instalada en el sistema donde se ejecuta (Java 21, versión 65). Java es compatible hacia atrás pero no hacia delante: una JVM antigua no puede ejecutar bytecode compilado con una JVM más nueva.

    **Cómo solucionarlo:** indica a IntelliJ que compile para una versión de Java compatible con la que tienes instalada en el sistema:

    1. `File → Project Structure → Project` → cambia **Language level** a `21` (o la versión que tengas instalada).
    2. `File → Project Structure → Modules → Dependencies` → comprueba que el **Module SDK** apunta a la misma JDK.
    3. Vuelve a generar el artefacto: `Build → Build Artifacts → Rebuild`.
    4. Ejecuta de nuevo: `java -jar Calculadora.jar`.

    Para saber qué versión de Java tienes instalada en la terminal, ejecuta `java -version`.

**C — Dos lenguajes en el mismo IDE (VSCodium)**

Dentro del mismo workspace de VSCodium:

- Ya tienes el proyecto Java funcionando.
- Añade un script en **Python** o **JavaScript** que haga las mismas operaciones (suma, resta, multiplicación de dos números).
- Ejecuta ambos archivos desde el terminal integrado de VSCodium.
- Captura de las dos ejecuciones en la misma sesión del editor.

**D — Reflexión y comparativa final**

Rellena la tabla comparativa de IntelliJ IDEA vs. VSCodium que encontrarás en la plantilla (criterios: facilidad de configuración inicial, gestión de plugins/extensiones, calidad del autocompletado Java, generación de ejecutables, soporte multilenguaje, consumo de recursos…).

Responde luego por escrito: ¿cuál elegirías para un proyecto Java de tamaño medio y por qué? ¿Y si el proyecto mezcla varios lenguajes?

---

## Indicaciones importantes

- En el apartado A, el proyecto debe ser el **mismo** en los dos IDEs (misma carpeta, mismos archivos `.java`). No copies el código a mano: abre la misma carpeta en los dos programas.
- En el `.jar`, el `main` debe estar correctamente declarado en el manifest. Si falla, documenta el error y cómo lo resolviste.
- La reflexión del apartado D debe estar justificada con lo que has vivido en la unidad, no con frases genéricas.

---

## Entrega

Sube el archivo al **Aula Virtual**, apartado **Actividad 2.4**.
