# 🧼 Actividad 4.2: Refactorización de código

!!! warning "Descarga la plantilla"
    📄 [Plantilla 4.2 — Refactorización de código](plantillas/Actividad_4_2_Plantilla.docx){target="_blank" rel="noopener"}

!!! info "Objetivo"
    Aplicar técnicas de refactorización sobre código real y demostrar que las entiendes:

    - El programa hace exactamente lo **mismo** antes y después (misma salida).
    - Puedes nombrar qué patrón has aplicado y **por qué** ese y no otro.
    - Tu explicación deja claro que has razonado tú, no que has copiado una solución.

---

## Contexto

Cuando un programa funciona, la tentación es no tocarlo. Pero el código que no se limpia se vuelve difícil de leer, de cambiar y de reutilizar — sobre todo cuando lo tiene que tocar otra persona (o tú mismo, seis meses después).

Refactorizar no es reescribir: es mejorar la estructura interna **sin alterar el resultado**. Los dos códigos de esta actividad tienen problemas evidentes. Tu trabajo es detectarlos, nombrarlos y resolverlos.

---

## Ejemplo resuelto

El siguiente ejemplo muestra el proceso completo: detectar el problema, elegir el patrón y aplicarlo.

### Versión inicial

```java
public class OrderCalculator {
    public static void main(String[] args) {
        double pricePerUnit = 50;
        int quantity = 5;
        boolean isPremiumMember = true;
        double totalPrice = 0;

        if (isPremiumMember) {
            totalPrice = pricePerUnit * quantity * 0.9;  // ← ¿qué es 0.9?
        } else {
            totalPrice = pricePerUnit * quantity;
        }

        System.out.println("Total a pagar: $" + totalPrice);
    }
}
```

### Versión refactorizada

Patrones aplicados: **Extract Method** + **Extract Constant** + **Rename**.

```java
public class OrderCalculator {

    private static final double PREMIUM_DISCOUNT_FACTOR = 0.90; // Extract Constant: nombre explícito

    public static void main(String[] args) {
        double unitPrice = 50;          // Rename: era pricePerUnit
        int units = 5;                  // Rename: era quantity
        boolean isPremium = true;       // Rename: era isPremiumMember

        double totalPrice = calculateTotalPrice(unitPrice, units, isPremium); // Extract Method
        System.out.println("Total a pagar: $" + totalPrice);
    }

    // Extract Method: la lógica de cálculo queda separada y reutilizable
    private static double calculateTotalPrice(double unitPrice, int units, boolean isPremium) {
        double total = unitPrice * units;
        if (isPremium) {
            total *= PREMIUM_DISCOUNT_FACTOR;
        }
        return total;
    }
}
```

!!! tip "Qué ha cambiado y por qué"
    - `main` solo prepara datos y llama a un método — más fácil de leer.
    - El cálculo está en un método separado — se puede probar y reutilizar.
    - `PREMIUM_DISCOUNT_FACTOR` explica qué representa el `0.9` — sin constante, no se entiende.

---

## Instrucciones

Para cada código (Código 1 y Código 2) sigue estos pasos **en orden**:

### Paso 1 — Predice antes de tocar nada

Lee el código entero una vez sin modificar nada y responde por escrito:

- ¿Qué problema principal tiene este código?
- ¿Qué patrón de refactorización crees que se podría aplicar? ¿Por qué ese?
- ¿Cuántos métodos nuevos crees que vas a necesitar crear?

Anota tus respuestas **antes** de empezar a refactorizar. Luego compararás.

### Paso 2 — Refactoriza

Aplica los patrones necesarios en IntelliJ. Usa las herramientas del IDE siempre que puedas (clic derecho → Refactor).

!!! warning "Regla fundamental"
    La salida del programa debe ser **idéntica** antes y después. Ejecuta ambas versiones y compara.

### Paso 3 — Clasifica y explica

Para **cada cambio** que hayas hecho:

- Indica qué patrón has aplicado (*Rename*, *Extract Method*, *Extract Constant*, *DRY*…).
- Explica en 1–2 líneas **por qué** ese patrón y qué problema resuelve.

!!! note "Importante"
    No basta con listar los cambios. Se valora que expliques el razonamiento: "he usado Extract Method porque el bloque de cálculo se repetía 5 veces y así puedo cambiarlo en un solo sitio".

---

## Código 1: TriangleCalculator

**Qué hace:** calcula el área de cinco triángulos.

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

### Antes de empezar — predice

Responde **sin tocar el código todavía**:

1. ¿Cuántas veces se repite exactamente el mismo bloque de código? ¿Qué cambia entre cada repetición?
2. Si mañana el cliente pide que la fórmula cambie (por ejemplo, que el área lleve dos decimales fijos), ¿cuántos sitios tendrías que modificar en la versión actual?
3. ¿Qué patrón de refactorización resuelve este problema? Anota tu respuesta antes de continuar.

### Preguntas tras refactorizar

1. ¿Ha coincidido tu predicción con lo que has acabado haciendo? Si no ha coincidido, ¿en qué has fallado el razonamiento?
2. El `0.5` de la fórmula es una constante mágica. ¿Has extraído una constante con nombre para él? Si no lo has hecho, ¿por qué has decidido dejarlo así?
3. ¿Qué pasaría si añades un sexto triángulo a tu versión refactorizada? ¿Cuántas líneas tienes que escribir? Compara con la versión original.

---

## Código 2: WeatherAnalyzer

**Qué hace:** analiza temperaturas de tres semanas: máxima, mínima, promedio y días por encima de 30 °C.

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

### Antes de empezar — predice

Responde **sin tocar el código todavía**:

1. ¿Cuántos métodos distintos crees que puedes extraer de este código? Nómbralos.
2. El umbral `30` aparece varias veces. ¿Qué patrón resuelve ese problema? ¿Por qué es un problema tenerlo repetido?
3. El código solo analiza dos semanas aunque hay datos de tres. ¿Dónde lo has notado? ¿Qué tendría que cambiar para que funcione con cualquier número de semanas?

### Preguntas tras refactorizar

1. ¿Ha coincidido el número de métodos que predijiste con los que has creado al final? Si no ha coincidido, explica por qué.
2. ¿Has usado `30` como constante con nombre o lo has dejado como número directo? Justifica tu decisión.
3. ¿Qué pasaría si el cliente pide que el umbral de "día caluroso" cambie a 28 °C? ¿Cuántos sitios tendrías que tocar en tu versión refactorizada? ¿Y en la original?
4. Tras refactorizar, ¿podrías añadir fácilmente el análisis de la semana 3 sin duplicar nada? ¿Cómo?

---

## Entregable

Rellena la plantilla y entrégala en **PDF**.

!!! warning "Lo que no vale"
    Listar cambios sin explicar por qué. "He usado Extract Method" sin decir qué problema resuelve y por qué ese patrón y no otro no suma puntos.
