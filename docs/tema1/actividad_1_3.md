# 🧪 Actividad 1.3: Estructura básica de un programa Java (desde consola) + **Reto**

---

## 🎯 Objetivos de la actividad

!!! info "Al finalizar serás capaz de…"
    - Reconocer la **estructura mínima** de un programa Java de consola.
    - Explicar el papel del método **`main(String[] args)`**.
    - **Compilar** y **ejecutar** programas desde **terminal** (Ubuntu).
    - Comprender lo esencial de **paquetes** (`package`) e **imports** de la **librería estándar**.
    - Aplicar lo aprendido en un **reto final** con dos clases en paquetes distintos.
    - Preparar un **documento con capturas** que evidencien el proceso.

---

!!! tip "🖱️ ¿Puedo usar interfaz gráfica?"
    Sí. Si tu VM tiene escritorio, **puedes crear/editar archivos con el explorador y un editor gráfico** (por ejemplo, *Gedit*).
    La compilación/ejecución seguirá haciéndose en **terminal**.

---

### 📚 Referencia mínima de comandos que se van a utilizar

```text
mkdir NOMBRE_CARPETA     → crea carpetas
cd NOMBRE_CARPETA        → entra en una carpeta
cd ..                    → sube a la carpeta anterior
ls                       → lista archivos de la carpeta actual
nano ARCHIVO.java        → edita/crea un archivo en consola
javac ARCHIVO.java       → compila un archivo
javac -d clases RUTA.java→ compila y deja .class en la carpeta "clases"
java NombreClase         → ejecuta si NO tiene package
java -cp clases paquete.Clase  → ejecuta si SÍ tiene package
```

---

## 🔧 Requisitos previos

- Ubuntu con **JDK** instalado (incluye `javac` y `java`).
- Editor de consola opcional: `nano` o `vim`.

```bash
java -version
javac -version
```

---

## 📦 Entregables (léelos **ANTES** de empezar)

1. **Captura 1** – Comprobación de `java` y `javac` en la terminal.  
2. **Captura 2** – Creación, **compilación** y **ejecución** de `Mundo.java`.  
3. **Captura 3** – Ejecución de **Doce.java** (tabla 12×12).  
4. **Captura 4** – Ejecución de **Doce.java** modificada (12×10).  
5. **Captura 5** – Ejecución de **Catorce.java** (14×10).  
6. **Captura 6** – Compilación y ejecución de **App.java** con **package** `org.entornos.demo`.  
7. **Captura 7** – Compilación y ejecución de **ListaNombres.java** con **import** de la librería estándar.  
8. **Reto – Capturas**:  
   - **R1**: contenido de *MatOps.java* y *CalculadoraApp.java* con tus líneas **`package`** e **`import`**.  
   - **R2**: compilación de *MatOps.java* y *CalculadoraApp.java*.  
   - **R3**: ejecución correcta de `org.entornos.app.CalculadoraApp`.  
   - **R4**: estructura de carpetas del reto (puedes usar `ls` en cada carpeta o `tree` si lo tienes).  
9. **Conclusión breve** – 6–10 líneas: qué has aprendido, dificultades y dudas.

> **Entrega**: un único **PDF** con todas las capturas y comentarios.

---

## 1) 📘 ¿Cómo es un programa Java por dentro?

Toda aplicación de consola en Java **empieza** en el método:

```java
public static void main(String[] args)
```

- `public class NombreClase` → Define la **clase**. El archivo debe llamarse **NombreClase.java**.  
- `{ … }` → Delimitan el **bloque** de la clase y del método.  
- `public static void main(String[] args)` → Punto de **entrada** del programa.  
  - `public`: visible desde fuera.  
  - `static`: pertenece a la clase, no a un objeto.  
  - `void`: no devuelve valor.  
  - `String[] args`: parámetros de **línea de comandos** (no los usamos aquí).  
- `System.out.println("…")` → Imprime texto en la **consola**.

---

## 2) ✍️ Ejercicio 1 — **Mundo**

Crea, compila y ejecuta tu primer programa.

### 2.1. Crear la carpeta y el archivo

```bash
mkdir actividad_java_1
cd actividad_java_1
nano Mundo.java
```

Pega este contenido y **guarda** (en *nano*: `Ctrl+O`, `Enter`, `Ctrl+X`):

```{.java .copy}
public class Mundo {
    public static void main(String[] args) {
        System.out.println("¡Hola mundo!");
    }
}
```

### 2.2. Compilar y ejecutar

```bash
javac Mundo.java
java Mundo
```

✅ **Deberías ver:**

```
¡Hola mundo!
```

> 📸 **Captura 2** – pantalla con compilación y ejecución.

---

## 3) ✍️ Ejercicio 2 — **Doce** (tabla del 12 × 12)

Crea un programa que imprima la **tabla del 12** hasta 12×12.

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

Compila y ejecuta:

```bash
javac Doce.java
java Doce
```

> 📸 **Captura 3** – salida con la tabla 12×12.

---

## 4) 🔧 Variaciones guiadas

### 4.1. *Doce* hasta 12×10
Edita **Doce.java** para que llegue solo a **10** y vuelve a compilar/ejecutar:

```bash
javac Doce.java
java Doce
```

> 📸 **Captura 4** – tabla del 12 **hasta 10**.

### 4.2. *Catorce* hasta 14×10
Crea un nuevo archivo **Catorce.java** (igual que Doce, pero con **14**):

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

Compila y ejecuta:

```bash
javac Catorce.java
java Catorce
```

> 📸 **Captura 5** – salida con la tabla 14×10.

---

## 5) 🧭 Teoría esencial sobre **packages** e **imports**

!!! tip "Idea clave"
    - Un **package** es un **nombre de carpeta** que agrupa clases relacionadas.  
      `package a.b.c;` ⇒ la clase está dentro de `a/b/c/`  
    - Un **import** permite usar **clases** de otros packages (por ejemplo, de la **librería estándar** de Java).

- **Regla 1:** La **primera línea** del archivo puede ser `package …;` y **debe coincidir** con las carpetas donde guardas el `.java`.  
- **Regla 2:** Para ejecutar una clase con package, debes indicar el **nombre completo** (por ejemplo, `org.entornos.demo.App`) y usar `-cp` (classpath) para decir dónde están las clases compiladas.

---

## 6) ✅ Ejercicio 3 — **Package básico** (`org.entornos.demo`)

Vamos a crear una clase con **package** paso a paso, usando **comandos simples**.

### 6.1. Crear la estructura de carpetas

```bash
mkdir actividad_java_1_paquetes
cd actividad_java_1_paquetes

mkdir org
cd org
mkdir entornos
cd entornos
mkdir demo
cd demo
nano App.java
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

### 6.3. Volver al directorio base y compilar/ejecutar

```bash
cd ..
cd ..
cd ..
mkdir clases
javac -d clases org/entornos/demo/App.java
java -cp clases org.entornos.demo.App
```

> 📸 **Captura 6** – muestra la compilación y la ejecución de `App`.
>
> 💡 **Opcional:** si tienes `tree`, puedes mostrar la estructura de carpetas.

---

## 7) ✅ Ejercicio 4 — **Import** de la librería estándar

Ahora, en el **mismo package**, creamos otra clase que **importe** una clase de la librería estándar (`java.util.ArrayList`).

### 7.1. Crear el archivo

```bash
cd org
cd entornos
cd demo
nano ListaNombres.java
```

### 7.2. Código de `ListaNombres.java`

```{.java .copy}
package org.entornos.demo;

import java.util.ArrayList;

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

### 7.3. Compilar y ejecutar

```bash
cd ..
cd ..
cd ..
javac -d clases org/entornos/demo/ListaNombres.java
java -cp clases org.entornos.demo.ListaNombres
```

> 📸 **Captura 7** – compilación y ejecución de `ListaNombres`.

---

# 🧪 Reto final (dentro de la Actividad 1.3)
## Dos clases, **packages** e **imports** — *tú te encargas de la estructura y los comandos*

> **Importante:** En este reto **no** se proporcionan comandos (`mkdir`, `javac`, `java`, etc.).  
> Debes crear carpetas, escribir los `package` e `import`, **compilar** y **ejecutar** como ya aprendiste arriba.

### 🎯 Objetivo del reto
- Colocar clases en **paquetes** correctos creando su **estructura de carpetas**.
- Escribir las sentencias **`package`** e **`import`** necesarias.
- Compilar y ejecutar desde terminal usando **classpath** correctamente.

### 🗂️ Estructura objetivo (tú la creas)
```
actividad_java_1_reto/
├── org/
│   └── entornos/
│       ├── app/      (CalculadoraApp.java)
│       └── util/     (MatOps.java)
└── clases/           (salida de compilación .class)
```

### 🧩 Clase 1 (librería): `MatOps.java`
**Ruta sugerida**: `org/entornos/util/MatOps.java`  
👉 Añade **arriba** la sentencia `package …` correcta.

```{.java .copy}
public class MatOps {
    public static int suma(int a, int b) { return a + b; }
    public static int mult(int a, int b) { return a * b; }
    public static int resta(int a, int b) { return a - b; }
}
```

### 🚀 Clase 2 (app): `CalculadoraApp.java`
**Ruta sugerida**: `org/entornos/app/CalculadoraApp.java`  
👉 Añade **arriba** el `package …` correcto e **importa** `MatOps`.

```{.java .copy}
public class CalculadoraApp {
    public static void main(String[] args) {
        int a = 10;
        int b = 100;
        System.out.println("Operando con " + a + " y " + b);
        System.out.println("Suma = " + MatOps.suma(a, b));
        System.out.println("Resta = " + MatOps.resta(b, a));
        System.out.println("Multiplicación = " + MatOps.mult(a, b));
    }
}
```

### ✅ Lo que debes hacer tú
1. Crear la **estructura de carpetas** indicada.  
2. Escribir los **`package`** correctos en los dos archivos.  
3. Escribir el **`import`** necesario en `CalculadoraApp.java`.  
4. Compilar ambas clases dejando los `.class` en `clases/`.  
5. Ejecutar la aplicación (`org.entornos.app.CalculadoraApp`).  
6. Capturar **R1–R4** (ver Entregables arriba).

!!! warning "Errores comunes"
    - *`class not found`* al ejecutar → revisa **classpath** y el **nombre cualificado**.  
    - Falla la compilación → comprueba que el **package coincide con la ruta** de carpetas.  
    - No encuentra `MatOps` → falta el **import** o no has compilado en el orden correcto.

---

## 📝 Entrega final
Sube a Aules un **PDF único** con:  
- Las **capturas 1–7** de los ejercicios guiados.  
- Las **capturas R1–R4** del reto final.  
- Una **conclusión** (6–10 líneas) explicando qué aprendiste, dificultades y dudas.
