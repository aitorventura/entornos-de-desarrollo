# 🐞 Actividad 3.1: Depuración con IntelliJ

!!! info "Objetivo"
    Utilizar el **depurador de IntelliJ IDEA** para localizar y corregir errores en tres programas Java. En cada uno trabajarás con una técnica distinta:

    - **Código A** — breakpoint de línea + avance paso a paso (Step Over).
    - **Código B** — breakpoint de excepción para capturar un error en tiempo de ejecución.
    - **Código C** — breakpoint condicional + Watch + Evaluate Expression.

---

## Lo que tienes que entregar

Completa la **plantilla** con los apartados de cada código, expórtala a PDF y súbela al Aula Virtual con el nombre:

```
A3-1_NombreApellido.pdf
```

!!! warning "Descarga la plantilla"
    📄 [Plantilla 3.1 — Depuración con IntelliJ](plantillas/Actividad_3_1_Plantilla.docx){target="_blank" rel="noopener"}

---

## Resumen de la actividad

Se te proporcionan tres programas Java con errores. Para cada uno tendrás que:

| Código | Descripción | Técnica obligatoria |
|--------|-------------|---------------------|
| A | Suma de números del 0 al 5 | Breakpoint de línea + Step Over |
| B | Divisores del número 10 | Exception Breakpoint (`ArithmeticException`) |
| C | Máximo de un rango introducido por teclado | Breakpoint condicional + Watch + Evaluate Expression |

Para cada código, la plantilla te pide que completes estos apartados **en orden**:

1. **Predicción** — antes de ejecutar, escribe qué crees que imprimirá el programa y qué tipo de error esperas encontrar.
2. **Código inicial** — copia el código con el error tal como se proporciona aquí.
3. **Identificación del error** — tipo de error (lógico, sintáctico, en tiempo de ejecución…) y dónde está.
4. **Proceso de depuración** — describe los pasos que has seguido con la técnica asignada: dónde colocaste el breakpoint, qué valores observaste, qué viste en la pila de llamadas o en la ventana de variables, cómo llegaste a la solución.
5. **Capturas** — imágenes del depurador en funcionamiento (breakpoint activo, ventana de variables, Watch, Evaluate Expression, o lo que hayas usado en ese código concreto).
6. **Código corregido** — versión final sin el error.
7. **Reflexión** — responde en 3-5 frases a las preguntas que encontrarás en la plantilla para ese código.

---

## Códigos a analizar

### 🅰️ Código A

**Descripción:** realiza la suma de los números del 0 al 5.

**Técnica obligatoria:** coloca un **breakpoint de línea** dentro del bucle y avanza con **Step Over** (`F8`) observando cómo cambian `i` y `sum` en cada iteración. No saltes directamente al resultado.

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

**Descripción:** calcula el número de divisores que tiene el número 10.

**Técnica obligatoria:** antes de ejecutar el programa, configura un **Exception Breakpoint** para `ArithmeticException` (`Run → View Breakpoints → + → Java Exception Breakpoints`). Cuando el programa se detenga en la excepción, examina la pila de llamadas y los valores de las variables en ese momento.

!!! warning "Este programa lanza una excepción al ejecutarse"
    Si lo ejecutas directamente (sin depurador o sin el exception breakpoint), verás un `ArithmeticException: / by zero` y el programa se detiene. Eso es exactamente lo que necesitas capturar con el depurador: configura el breakpoint **antes** de lanzarlo.

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

**Descripción:** determina el número más grande dentro de un rango introducido por teclado.

**Técnica obligatoria:** usa un **breakpoint condicional** (clic derecho sobre el breakpoint → *Edit Breakpoint* → añade una condición). Añade también al menos una variable a **Watches** y usa **Evaluate Expression** para comprobar el valor de una expresión durante la pausa.

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

!!! tip "Pista para el breakpoint condicional"
    Prueba el programa con un rango donde el error sea evidente (por ejemplo, `-5` a `-1`). Eso te ayudará a saber qué condición poner en el breakpoint para detener la ejecución justo cuando el error aparece.

---

## Indicaciones importantes

- Las capturas deben mostrar tu **nombre de usuario del sistema** o el nombre del proyecto. No sirven capturas genéricas descargadas de internet.
- Describe lo que **tú observaste** en el depurador: qué valores aparecieron en pantalla, en qué línea se detuvo, qué mostraba la pila de llamadas. No lo que "debería" mostrar en general.
- El apartado de predicción debe rellenarse **antes** de ejecutar el programa. Si la predicción era incorrecta, explica en la reflexión por qué te equivocaste.
- No uses IA para redactar las reflexiones. En la corrección se puede preguntar qué viste exactamente en tu pantalla.

---

## Entrega

Sube el archivo al **Aula Virtual**, apartado **Actividad 3.1**.
