# 🧼 Actividad 4.2: Refactorización y documentación básica de código 

!!! info "Objetivo"
    Mejorar la **estructura y calidad** del código sin cambiar su funcionamiento, trabajando:

    - **Refactorización**: limpiar, ordenar y reducir duplicación.  
    - **Documentación básica**: añadir comentarios **breves y útiles** para que el código se entienda mejor.  

---

## 🔹 Contexto

El código limpio y bien estructurado es más fácil de **leer**, **mantener** y **ampliar**.  
La refactorización te permite mejorar el diseño interno del código **sin alterar su comportamiento**.  
Además, una documentación básica (comentarios claros y puntuales) facilita que otras personas entiendan rápido:

- qué hace cada parte importante,
- por qué se ha tomado una decisión,
- y cómo modificarlo sin romperlo.

---

## 🧠 Ejemplo resuelto (refactorización paso a paso)

El siguiente ejemplo muestra cómo refactorizar un programa sencillo sin cambiar su funcionamiento.

### 🧱 Versión inicial

```java
public class OrderCalculator {
    public static void main(String[] args) {
        double pricePerUnit = 50;
        int quantity = 5;
        boolean isPremiumMember = true;
        double totalPrice = 0;

        if (isPremiumMember) {
            totalPrice = pricePerUnit * quantity * 0.9;
        } else {
            totalPrice = pricePerUnit * quantity;
        }

        System.out.println("Total a pagar: $" + totalPrice);
    }
}
```

---

### ✅ Versión refactorizada (resultado final)

Refactors aplicados:

- **Extract Method** (separamos el cálculo en un método).
- **Extract Constant** (quitamos valores “mágicos”).
- **Rename** (nombres más claros).
- Pequeños ajustes para simplificar el cálculo.

```java
public class OrderCalculator {

    // Constantes con significado (evitan valores mágicos)
    private static final double PREMIUM_DISCOUNT_FACTOR = 0.90;

    public static void main(String[] args) {
        double unitPrice = 50;
        int units = 5;
        boolean isPremium = true;

        double totalPrice = calculateTotalPrice(unitPrice, units, isPremium);
        System.out.println("Total a pagar: $" + totalPrice);
    }

    // Método pequeño y reutilizable: calcula el total con/sin descuento
    private static double calculateTotalPrice(double unitPrice, int units, boolean isPremium) {
        double total = unitPrice * units;
        if (isPremium) {
            total *= PREMIUM_DISCOUNT_FACTOR;
        }
        return total;
    }
}
```

!!! tip "Qué mejora este cambio"
    - El `main` queda más limpio: solo prepara datos y llama a un método.
    - El cálculo está en un método reutilizable y fácil de probar.
    - La constante hace que el descuento sea explícito y fácil de cambiar.


---

## 🧩 Qué tienes que hacer

Para **cada código** (Código 1 y Código 2):

### 1) Refactorización
- Analiza el código y detecta problemas típicos:
  
    - repetición de bloques,
    - nombres poco claros,
    - métodos demasiado largos,
    - constantes “mágicas” (por ejemplo, `0.5` o `30` sin explicación),
    - lógica mezclada (cálculos + salida por pantalla en el mismo sitio).

- Refactoriza **sin cambiar la funcionalidad** (misma salida o resultado lógico).

### 2) Explicación del proceso
- Describe los pasos que has seguido durante la refactorización.
- Justifica los cambios: por qué es mejor ahora (legibilidad, reutilización, mantenimiento).

### 3) Javadoc en los métodos extraídos

Después de refactorizar, añade **Javadoc** a los métodos públicos que hayas creado con Extract Method:

- una frase que explique **qué hace** el método,
- `@param` para cada parámetro (si los tiene),
- `@return` si devuelve un valor,
- `@throws` si puede lanzar una excepción.

!!! tip “Regla práctica”
    Documenta lo que el método **promete**: qué recibe, qué devuelve y en qué condiciones falla. No comentes lo que ya dice el nombre del método.

---

## ✅ Entregable

Debes entregar un **informe en PDF** donde, para cada código, incluyas:

1. **Cambios realizados**
   
    - Lista de refactors aplicados (por ejemplo: *Extract Method*, *Rename*, *Extract Constant*, reducir duplicación…).

2. **Código final refactorizado**

    - Pegado completo y con Javadoc en los métodos públicos extraídos.

3. **Explicación**

    - 8–15 líneas explicando qué has hecho y por qué.

---

## 🧾 Sugerencia de estructura para tu informe

??? tip "Abrir plantilla"
    ### Código X
    **Problemas detectados**

    - ...
    - ...

    **Cambios realizados**

    - ...
    - ...

    **Código final (refactorizado + Javadoc en métodos públicos)**

    ```java
    // tu código aquí
    ```

    **Explicación**

    - ...

---

## 🧩 Código 1: TriangleCalculator

**Objetivo del programa:** calcular el área de varios triángulos.

```java
public class TriangleCalculator {
    public static void main(String[] args) {
        // Cálculo del área del primer triángulo
        int base1 = 5;
        int height1 = 8;
        double area1 = 0.5 * base1 * height1;
        System.out.println("Área del triángulo 1: " + area1);

        // Cálculo del área del segundo triángulo
        int base2 = 7;
        int height2 = 10;
        double area2 = 0.5 * base2 * height2;
        System.out.println("Área del triángulo 2: " + area2);

        // Cálculo del área del tercer triángulo
        int base3 = 4;
        int height3 = 6;
        double area3 = 0.5 * base3 * height3;
        System.out.println("Área del triángulo 3: " + area3);

        // Cálculo del área del cuarto triángulo
        int base4 = 9;
        int height4 = 12;
        double area4 = 0.5 * base4 * height4;
        System.out.println("Área del triángulo 4: " + area4);

        // Cálculo del área del quinto triángulo
        int base5 = 3;
        int height5 = 5;
        double area5 = 0.5 * base5 * height5;
        System.out.println("Área del triángulo 5: " + area5);
    }
}
```

---

## 🧩 Código 2: WeatherAnalyzer

**Objetivo del programa:** analizar temperaturas (máxima, mínima, promedio y días > 30ºC) por semanas.

```java
public class WeatherAnalyzer {
    public static void main(String[] args) {
        double[] temperaturesSemana1 = {28.5, 32.1, 30.0, 29.8, 33.2, 31.5, 27.9};
        double[] temperaturesSemana2 = {27.3, 31.0, 29.5, 28.7, 32.1, 30.8, 26.9};
        double[] temperaturesSemana3 = {29.1, 33.2, 31.5, 30.9, 34.0, 32.3, 28.7};
        String[] days = {"Lunes", "Martes", "Miércoles", "Jueves", "Viernes", "Sábado", "Domingo"};

        System.out.println("Análisis de temperaturas de la semana 1:");

        // Encontrar la temperatura máxima semana 1
        double maxTemp = temperaturesSemana1[0];
        String maxDay = days[0];
        for (int i = 1; i < temperaturesSemana1.length; i++) {
            if (temperaturesSemana1[i] > maxTemp) {
                maxTemp = temperaturesSemana1[i];
                maxDay = days[i];
            }
        }
        System.out.println("Temperatura máxima: " + maxTemp + "°C el " + maxDay);

        // Encontrar la temperatura mínima semana 1
        double minTemp = temperaturesSemana1[0];
        String minDay = days[0];
        for (int i = 1; i < temperaturesSemana1.length; i++) {
            if (temperaturesSemana1[i] < minTemp) {
                minTemp = temperaturesSemana1[i];
                minDay = days[i];
            }
        }
        System.out.println("Temperatura mínima: " + minTemp + "°C el " + minDay);

        // Calcular la temperatura promedio semana 1
        double sum = 0;
        for (int i = 0; i < temperaturesSemana1.length; i++) {
            sum += temperaturesSemana1[i];
        }
        double average = sum / temperaturesSemana1.length;
        System.out.println("Temperatura promedio: " + average + "°C");

        // Contar días calurosos (más de 30°C) semana 1
        int hotDays = 0;
        for (int i = 0; i < temperaturesSemana1.length; i++) {
            if (temperaturesSemana1[i] > 30) {
                hotDays++;
            }
        }
        System.out.println("Días con temperatura superior a 30°C: " + hotDays);

        System.out.println("\nAnálisis de temperaturas de la semana 2:");

        // Encontrar la temperatura máxima semana 2
        maxTemp = temperaturesSemana2[0];
        maxDay = days[0];
        for (int i = 1; i < temperaturesSemana2.length; i++) {
            if (temperaturesSemana2[i] > maxTemp) {
                maxTemp = temperaturesSemana2[i];
                maxDay = days[i];
            }
        }
        System.out.println("Temperatura máxima: " + maxTemp + "°C el " + maxDay);

        // Encontrar la temperatura mínima semana 2
        minTemp = temperaturesSemana2[0];
        minDay = days[0];
        for (int i = 1; i < temperaturesSemana2.length; i++) {
            if (temperaturesSemana2[i] < minTemp) {
                minTemp = temperaturesSemana2[i];
                minDay = days[i];
            }
        }
        System.out.println("Temperatura mínima: " + minTemp + "°C el " + minDay);

        // Calcular la temperatura promedio semana 2
        sum = 0;
        for (int i = 0; i < temperaturesSemana2.length; i++) {
            sum += temperaturesSemana2[i];
        }
        average = sum / temperaturesSemana2.length;
        System.out.println("Temperatura promedio: " + average + "°C");

        // Contar días calurosos (más de 30°C) semana 2
        hotDays = 0;
        for (int i = 0; i < temperaturesSemana2.length; i++) {
            if (temperaturesSemana2[i] > 30) {
                hotDays++;
            }
        }
        System.out.println("Días con temperatura superior a 30°C: " + hotDays);

        // ... (El mismo proceso se repetiría para la semana 3)
    }
}
```

