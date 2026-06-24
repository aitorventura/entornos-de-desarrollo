
# 🧪 Actividad 1.3: Estructura básica de un programa Java (desde consola) + Reto

---

## Objetivos de la actividad

!!! info "Al finalizar serás capaz de…"
    - Reconocer la **estructura mínima** de un programa Java de consola.
    - Explicar el papel del método `main(String[] args)`.
    - **Compilar** y **ejecutar** programas desde terminal (Ubuntu).
    - Entender para qué sirven los **packages** y los **imports** de la librería estándar.
    - Aplicar lo aprendido en un **reto final** con dos clases en paquetes distintos.
    - Preparar un **documento con capturas** que evidencien el proceso.

---

!!! tip "¿Puedo usar interfaz gráfica?"
    Sí. Si tu VM tiene escritorio puedes crear y editar archivos con un editor gráfico como *Gedit*.
    La compilación y ejecución siempre se hacen desde **terminal**.

---

## Referencia rápida de comandos

| Comando | Qué hace |
|---|---|
| `mkdir NOMBRE` | Crea una carpeta |
| `cd NOMBRE` | Entra en una carpeta |
| `cd ../..` | Sube dos niveles (ajusta el número de `..` según necesites) |
| `ls` | Lista los archivos de la carpeta actual |
| `nano ARCHIVO.java` | Edita o crea un archivo en consola |
| `javac ARCHIVO.java` | Compila un archivo (sin package) |
| `javac -d clases RUTA.java` | Compila y deja el `.class` en la carpeta `clases/` |
| `java NombreClase` | Ejecuta si la clase **no** tiene package |
| `java -cp clases paquete.Clase` | Ejecuta si la clase **sí** tiene package |
| `sudo apt install tree` | Instala el comando `tree` para ver la estructura de carpetas |
| `tree` | Muestra la estructura de carpetas en árbol |

---

## Requisitos previos

Ubuntu con JDK instalado. Comprueba que funciona:

```bash
java -version    # debe mostrar la versión instalada
javac -version   # debe coincidir con java -version
```

> 📸 **Captura 1** — salida de ambos comandos.

---

## Entregable

!!! note "Plantilla"
    Completa la plantilla disponible en [plantillas/Actividad_1_3_Plantilla.docx](plantillas/Actividad_1_3_Plantilla.docx) y entrégala exportada como **PDF** en el Aula Virtual.

---

## 1. ¿Cómo es un programa Java por dentro?

Toda aplicación de consola en Java empieza en el método:

```java
public static void main(String[] args)
```

Cada parte tiene un significado:

| Parte | Qué significa |
|---|---|
| `public class NombreClase` | Define la clase. El archivo **debe** llamarse `NombreClase.java` |
| `public` | Visible desde fuera de la clase |
| `static` | Pertenece a la clase, no a un objeto concreto |
| `void` | No devuelve ningún valor |
| `String[] args` | Argumentos de línea de comandos (no los usamos aquí) |
| `System.out.println("…")` | Imprime texto en la consola |

---

## 2. Ejercicio 1 — Mundo

Crea, compila y ejecuta tu primer programa.

### 2.1. Crear la carpeta y el archivo

```bash
mkdir actividad_java_1
cd actividad_java_1
nano Mundo.java
```

Pega este contenido y guarda (en *nano*: `Ctrl+O`, `Enter`, `Ctrl+X`):

```{.java .copy}
public class Mundo {
    public static void main(String[] args) {
        System.out.println("¡Hola mundo!");
    }
}
```

### 2.2. Compilar y ejecutar

```bash
javac Mundo.java   # genera Mundo.class con el bytecode
java Mundo         # la JVM ejecuta la clase (sin extensión)
```

✅ Deberías ver:

```
¡Hola mundo!
```

> 📸 **Captura 2** — pantalla con compilación y ejecución.

---

## 3. Ejercicio 2 — Doce (tabla del 12 × 12)

```bash
nano Doce.java
```

```{.java .copy}
public class Doce {
    public static void main(String[] args) {
        System.out.println("Tabla del 12 (hasta 12 x 12):");
        for (int i = 1; i <= 12; i++) {
            System.out.println("12 x " + i + " = " + (12 * i));
        }
    }
}
```

```bash
javac Doce.java
java Doce
```

> 📸 **Captura 3** — salida con la tabla 12×12.

---

## 4. Variaciones guiadas

### 4.1. Doce hasta 12×10

Edita `Doce.java` para que el bucle llegue solo a 10 y vuelve a compilar y ejecutar.

> 📸 **Captura 4** — tabla del 12 hasta 10.

### 4.2. Catorce hasta 14×10

```bash
nano Catorce.java
```

```{.java .copy}
public class Catorce {
    public static void main(String[] args) {
        System.out.println("Tabla del 14 (hasta 14 x 10):");
        for (int i = 1; i <= 10; i++) {
            System.out.println("14 x " + i + " = " + (14 * i));
        }
    }
}
```

```bash
javac Catorce.java
java Catorce
```

> 📸 **Captura 5** — salida con la tabla 14×10.

---

## 5. Teoría: packages e imports

Hasta ahora todas las clases estaban "sueltas", sin carpeta lógica. Cuando un proyecto crece, las clases se agrupan en **packages** para organizarlas y evitar que los nombres choquen entre sí.

!!! info "La regla de oro"
    La sentencia `package` de un archivo Java **debe coincidir exactamente** con la ruta de carpetas donde está guardado ese archivo.

```
package org.entornos.demo;
         │    │      │
         │    │      └── carpeta demo/
         │    └── carpeta entornos/
         └── carpeta org/
```

Así queda la estructura en disco:

```
actividad_java_1_paquetes/
├── org/
│   └── entornos/
│       └── demo/
│           └── App.java        ← tiene: package org.entornos.demo;
└── clases/
    └── org/
        └── entornos/
            └── demo/
                └── App.class   ← generado por javac -d clases
```

Un **import** permite usar clases de otros packages sin escribir su nombre completo cada vez. Por ejemplo, `import java.util.ArrayList;` te permite escribir `ArrayList` en lugar de `java.util.ArrayList` en todo el código.

Para ejecutar una clase con package necesitas dos cosas:
- El **nombre completo** de la clase: `org.entornos.demo.App`
- El **classpath** (`-cp clases`): la carpeta donde están los `.class`

---

## 6. Ejercicio 3 — Package básico (`org.entornos.demo`)

### 6.1. Crear la estructura de carpetas

```bash
mkdir actividad_java_1_paquetes
cd actividad_java_1_paquetes
mkdir -p org/entornos/demo    # -p crea todas las carpetas intermedias de una vez
mkdir clases
nano org/entornos/demo/App.java
```

### 6.2. Código de `App.java`

```{.java .copy}
package org.entornos.demo;

public class App {
    public static void main(String[] args) {
        System.out.println("App con package org.entornos.demo");
    }
}
```

### 6.3. Compilar y ejecutar (desde la carpeta raíz del proyecto)

```bash
javac -d clases org/entornos/demo/App.java   # compila; guarda .class en clases/
java -cp clases org.entornos.demo.App        # ejecuta con nombre completo
```

> 📸 **Captura 6** — compilación y ejecución de `App`.

!!! tip "Ver la estructura de carpetas"
    Si tienes `tree` instalado (`sudo apt install tree`), ejecuta `tree` para ver cómo quedaron las carpetas. Si no, usa `ls` dentro de cada carpeta.

---

## 7. Ejercicio 4 — Import de la librería estándar

En el mismo package añadimos una clase que usa `ArrayList`, una lista de la librería estándar de Java.

```bash
nano org/entornos/demo/ListaNombres.java
```

```{.java .copy}
package org.entornos.demo;

import java.util.ArrayList;   // importamos ArrayList de la librería estándar

public class ListaNombres {
    public static void main(String[] args) {
        ArrayList<String> nombres = new ArrayList<String>();
        nombres.add("Ana");
        nombres.add("Luis");
        System.out.println("Nombres: " + nombres);
        System.out.println("Total: " + nombres.size());
    }
}
```

```bash
javac -d clases org/entornos/demo/ListaNombres.java
java -cp clases org.entornos.demo.ListaNombres
```

> 📸 **Captura 7** — compilación y ejecución de `ListaNombres`.

---

# Reto final

## Dos clases, packages e imports — tú te encargas de todo

> En este reto **no** se proporcionan los comandos de creación de carpetas ni de compilación/ejecución. Debes aplicar lo que has aprendido en los ejercicios anteriores.

### Antes de escribir nada, responde por escrito

1. ¿Qué línea `package` necesita cada clase según la carpeta donde estará?
2. ¿Qué clase necesita un `import` y por qué?
3. ¿En qué orden hay que compilar las dos clases? ¿Importa el orden?
4. ¿Qué comando usarás para ejecutar la aplicación final?

Escribe tus respuestas antes de tocar el teclado. Compara después con lo que realmente funciona.

### Estructura objetivo (tú la creas)

```
actividad_java_1_reto/
├── org/
│   └── entornos/
│       ├── app/      ← aquí va CalculadoraApp.java
│       └── util/     ← aquí va MatOps.java
└── clases/           ← aquí irán los .class compilados
```

### Clase 1 — `MatOps.java`

Ruta: `org/entornos/util/MatOps.java`
Añade la sentencia `package` correcta en la primera línea.

```{.java .copy}
public class MatOps {
    public static int suma(int a, int b)  { return a + b; }
    public static int mult(int a, int b)  { return a * b; }
    public static int resta(int a, int b) { return a - b; }
}
```

### Clase 2 — `CalculadoraApp.java`

Ruta: `org/entornos/app/CalculadoraApp.java`
Añade el `package` correcto y el `import` necesario para usar `MatOps`.

```{.java .copy}
public class CalculadoraApp {
    public static void main(String[] args) {
        int a = 10;
        int b = 100;
        System.out.println("Operando con " + a + " y " + b);
        System.out.println("Suma          = " + MatOps.suma(a, b));
        System.out.println("Resta         = " + MatOps.resta(b, a));
        System.out.println("Multiplicación = " + MatOps.mult(a, b));
    }
}
```

!!! warning "Errores habituales"
    - `class not found` al ejecutar → revisa el classpath (`-cp clases`) y el nombre completo de la clase.
    - Falla la compilación → comprueba que el `package` coincide exactamente con la ruta de carpetas.
    - No encuentra `MatOps` → falta el `import` o no compilaste `MatOps.java` antes de `CalculadoraApp.java`.

---

## Entrega final

!!! note "Plantilla"
    Completa la plantilla disponible en [plantillas/Actividad_1_3_Plantilla.docx](plantillas/Actividad_1_3_Plantilla.docx) y entrégala exportada como **PDF** en el Aula Virtual.

