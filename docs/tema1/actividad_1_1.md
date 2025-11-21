# 🧪 Actividad 1.1: Del problema al programa

!!! info "Objetivo"
    Comprender cómo un **programa** transforma **entradas** en **salidas** y qué papel juegan la **CPU, la RAM y la E/S**.

---

## 🔹 Parte A. Identificar EPS (Entrada → Proceso → Salida)

<div class="tabs-colored" markdown>

=== "Gupo presencial"
    1. Ponte en pareja con un compañero.  
    2. Pensad en **tres situaciones cotidianas** (que se puedan relacionar con la informática) donde haya claramente entrada, proceso y salida.  
    Ejemplos (esos no valen):  
        - Cajero automático.  
        - Reproductor de música.  
        - Calculadora del móvil.  
    3. Dibujad una tabla con columnas:  

    | Entrada | Proceso | Salida |  
    |---------|---------|--------|  

    📸 Añadid un esquema rápido (a mano o con un diagrama simple) para representar el flujo.

=== "Grupo semipresencial"
    1. Piensa en **tres situaciones cotidianas** (que se puedan relacionar con la informática) donde haya claramente entrada, proceso y salida.  
    Ejemplos (esos no valen):  
        - Cajero automático.  
        - Reproductor de música.  
        - Calculadora del móvil.  
    2. Dibuja una tabla con columnas:  

    | Entrada | Proceso | Salida |  
    |---------|---------|--------|  

    📸 Añade un esquema rápido (a mano o con un diagrama simple) para representar el flujo.

</div>

---

## 🔹 Parte B. Relacionar con componentes
Para cada caso de la tabla, responde:

- ¿Qué haría la **CPU**?  
- ¿Qué datos guardarían en la **RAM**?  
- ¿Qué papel tendría la **E/S**?  
- ¿Intervendría la **red** o el **almacenamiento**?

---

## 🔹 Parte C. Mini-reto práctico
Analiza este pequeño código en **Java** e investiga y deduce dónde estaría la **entrada, proceso y salida**:

```java
import java.util.Scanner;

public class MediaNotas {
    public static void main(String[] args) {
        Scanner teclado = new Scanner(System.in);
        int suma = 0;

        for (int i = 1; i <= 3; i++) {
            System.out.print("Introduce una nota: ");
            int n = teclado.nextInt();
            suma += n;
        }

        double media = suma / 3.0;
        System.out.println("La media es: " + media);

        teclado.close();
    }
}
```

- ¿Qué parte es **entrada**?  
- ¿Qué hace el **proceso**?  
- ¿Cuál es la **salida**?  

---

## ✅ Entregable
Un documento breve con:

- La tabla con los tres ejemplos.  
- Un diagrama sencillo de un caso.  
- Las respuestas sobre CPU, RAM, E/S, red y almacenamiento.  
- El análisis del programa en Java.  
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
   - Explica brevemente el tipo de error:  
     - Lógico  
     - Sintáctico  
     - De ejecución (runtime)

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
    _Tabla de ejemplo para la actividad 4.1._  
    _(Añade aquí el enlace cuando lo tengas disponible en el aula o en los recursos.)_

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
- Cada tabla debe contener todos los apartados indicados:  
  - Código inicial  
  - Identificación del error  
  - Proceso de depuración  
  - Capturas de pantalla  
  - Código corregido  
  - Reflexión final  


