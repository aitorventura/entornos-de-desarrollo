# 🐞 Actividad 3.1: Depuración con IntelliJ

!!! info "Objetivo"
    Aprender a utilizar el **depurador de IntelliJ IDEA** para:

    - Configurar y usar diferentes tipos de **puntos de interrupción (breakpoints)**.  
    - Inspeccionar el **estado del programa en tiempo de ejecución**.  
    - Modificar valores y **evaluar expresiones en tiempo real**.  
    - Rastrear errores y comprender el **flujo de llamadas** de un programa Java.

---

## 🔹 Descripción de la actividad

La depuración es una herramienta esencial en el desarrollo de software, que permite analizar el comportamiento de un programa **paso a paso**, identificar errores y comprender cómo fluye la ejecución.

En esta práctica utilizarás **IntelliJ IDEA** para explorar los distintos tipos de **breakpoints** y sus configuraciones, aplicándolos sobre varios **programas Java sencillos** que contienen errores.

A continuación se te proporcionan varios códigos.  
Cada uno tiene **al menos un error** y tu objetivo es, mediante la herramienta de depuración de IntelliJ, **encontrarlo y corregirlo**.

---

## 🔹 Trabajo a realizar con cada código

Para **cada código** deberás elaborar una **tabla** que contenga:

1. **Código inicial**  
    - Copia el código con el error tal como fue proporcionado.

2. **Identificación del error**  
    - Explica brevemente el tipo de error: lógico, sintáctico, de ejecución (runtime)...

3. **Proceso de depuración**  
    - Describe los pasos que has seguido, por ejemplo:  
        - Dónde colocaste los **puntos de interrupción**.  
        - Qué **valores de variables** observaste.  
         - Qué viste en la **pila de llamadas**.  
         - Cómo esa información te llevó a encontrar la solución.

4. **Capturas**  
    - Incluye imágenes donde se vea el uso del depurador:  
        - Breakpoints.  
        - Ventana de variables.  
        - Evaluate Expression / Watches.  
        - Cualquier configuración relevante.

5. **Código corregido**  
    - Presenta la **versión corregida** del código, sin el error.

6. **Reflexión**  
    - Resume brevemente:  
        - Qué has aprendido.  
        - Qué herramientas del depurador te han resultado más útiles.  
        - Qué dificultades has tenido y cómo las has resuelto.

!!! info "Modelo de tabla"
    En el siguiente enlace encontrarás un **ejemplo de la tabla** a rellenar por cada uno de los códigos:  
    [📄 Descargar modelo de tabla (DOCX)](recursos/tabla_act_3_1.docx){target="_blank" rel="noopener"}


---

## 🔹 Códigos a analizar

### 🅰️ Código A  
**Descripción**  
Realiza la **suma de los números del 0 al 5**.

```java
public class Main {
    public static void main(String[] args) {
        int sum = 0;
        int limit = 5;

        for (int i = 1; i < limit; i++) {
            sum += i;
        }

        System.out.println("La suma de los números es: " + sum);
    }
}
```

---

### 🅱️ Código B  
**Descripción**  
Calcula el **número de divisores** que tiene el número 10.

```java
public class Main {
    public static void main(String[] args) {
        int divisorCount = 0;
        int number = 10;

        System.out.println("Divisores de " + number + ":");
        for (int i = 10; i >= 0; i--) { 
            if (number % i == 0) { 
                divisorCount++; 
            }
        }

        System.out.println("El número " + number + " tiene " + divisorCount + " divisores.");
    }
}
```

---

### 🅾️ Código C  
**Descripción**  
Determina el **número más grande** dentro de un rango de números introducido por teclado.

```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.print("Introduce el número inicial del rango: ");
        int start = scanner.nextInt();

        System.out.print("Introduce el número final del rango: ");
        int end = scanner.nextInt();

        int max = 0; 

        for (int i = start; i <= end; i++) {
            if (i > max) {
                max = i;
            }
        }

        System.out.println("El número más grande en el rango es: " + max);
    }
}
```

---

## ✅ Entregable

- Crea un **PDF** donde incluyas las **3 tablas completas**, una por cada código (A, B y C).  

