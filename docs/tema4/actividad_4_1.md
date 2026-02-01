# ⚡ Actividad 4.1: Optimización básica en Java

!!! info "Objetivo"
    Aplicar mejoras sencillas para que un programa:

    - Vaya **más rápido** o haga **menos trabajo innecesario**.
    - Mantenga el **mismo resultado** (la optimización no cambia la funcionalidad).
    - Justifique la mejora con una comparación **antes vs después**.

---

## 🧩 Instrucciones generales

Para **cada ejercicio**:

1. Ejecuta el código tal como está y anota la salida/tiempos.
2. Aplica la mejora propuesta (o la que se pide).
3. Vuelve a ejecutar y compara.
4. Explica con 6–10 líneas:

    - qué has cambiado,
    - por qué mejora,
    - qué se mantiene igual.

!!! tip "Consejo"
    Ejecuta cada medición **3 veces** y usa un valor aproximado (los tiempos pueden variar).

---

## 🧪 Ejercicio A: Búsqueda repetida (List vs HashSet)

**Situación:** buscas muchas veces el mismo dato dentro de una lista grande.

### Código

```java
import java.util.ArrayList;
import java.util.HashSet;
import java.util.List;
import java.util.Set;

public class EjercicioA {

    public static void main(String[] args) {
        List<String> emails = new ArrayList<>();
        for (int i = 0; i < 50_000; i++) {
            emails.add("user" + i + "@mail.com");
        }

        String objetivo = "user40000@mail.com";

        // --- Antes: List.contains ---
        int aciertosLista = 0;
        long t1 = System.nanoTime();
        for (int i = 0; i < 20_000; i++) {
            if (emails.contains(objetivo)) {
                aciertosLista++;
            }
        }
        long t2 = System.nanoTime();

        // --- Después: HashSet.contains ---
        Set<String> indice = new HashSet<>(emails);

        int aciertosSet = 0;
        long t3 = System.nanoTime();
        for (int i = 0; i < 20_000; i++) {
            if (indice.contains(objetivo)) {
                aciertosSet++;
            }
        }
        long t4 = System.nanoTime();

        System.out.println("Aciertos lista: " + aciertosLista);
        System.out.println("List.contains: " + (t2 - t1) + " ns");

        System.out.println("Aciertos set: " + aciertosSet);
        System.out.println("HashSet.contains: " + (t4 - t3) + " ns");
    }
}
```

### Trabajo a realizar

- Comprueba que `aciertosLista` y `aciertosSet` salen iguales.
- Compara tiempos.
- Explica por qué `HashSet` suele ser más rápido en búsquedas repetidas.

---

## 🧪 Ejercicio B: Concatenación de Strings en bucle (String + vs StringBuilder)

**Situación:** construyes un texto grande concatenando dentro de un bucle.

### Código

```java
public class EjercicioB {

    public static void main(String[] args) {

        // --- Antes: concatenación con + en bucle ---
        long t1 = System.nanoTime();
        String texto = "";
        for (int i = 0; i < 20_000; i++) {
            texto += "Línea " + i + "\n";
        }
        long t2 = System.nanoTime();
        System.out.println("Longitud texto: " + texto.length());
        System.out.println("Con +: " + (t2 - t1) + " ns");

        // TODO: Después: reescribe usando StringBuilder
        // Pista:
        // StringBuilder sb = new StringBuilder();
        // sb.append(...);
        // String resultado = sb.toString();
    }
}
```

### Trabajo a realizar

- Reescribe el segundo bloque usando `StringBuilder`.
- Mide el tiempo y compara con el primer método.
- Explica por qué `StringBuilder` es mejor en este caso.

---

## 🧪 Ejercicio C: Trabajo repetido dentro de un bucle (mismo cálculo, muchas veces)

**Situación:** en un bucle repites un cálculo que no cambia.

### Código

```java
public class EjercicioC {

    public static void main(String[] args) {

        int precio = 100;
        int unidades = 500_000;

        // --- Antes: cálculo repetido ---
        long t1 = System.nanoTime();
        int total = 0;
        for (int i = 0; i < unidades; i++) {
            int precioConIVA = (int) (precio * 1.21); // se recalcula cada vuelta
            total += precioConIVA;
        }
        long t2 = System.nanoTime();

        System.out.println("Total: " + total);
        System.out.println("Recalcular dentro: " + (t2 - t1) + " ns");

        // TODO: Después: mueve el cálculo fuera del bucle y vuelve a medir
    }
}
```

### Trabajo a realizar

- Mueve `precioConIVA` fuera del bucle.
- Comprueba que el `Total` no cambia.
- Compara tiempos y explica la mejora.

---

## ✅ Entregable

Entrega un **PDF** con:

1. Resultados de los **3 ejercicios (A, B, C)**.
2. Para cada ejercicio:
    
    - Captura o copia de la salida (tiempos y valores clave).
    - Explicación breve (6–10 líneas): qué cambia, por qué mejora, qué se mantiene igual.

---

## 🎯 Retos extra (opcionales, sin código)

Elige **uno**, reflexiona y descríbelo (8–12 líneas): qué harías y por qué.

### Reto 1: Evitar “consulta dentro de bucle”
En una pantalla se listan pedidos y, para cada pedido, se consulta el cliente con otra consulta.  
Explica cómo reducirías el número de consultas.

### Reto 2: Cargar solo lo necesario
Tienes miles de productos y cargas todos para mostrar 20.  
Explica cómo lo cambiarías (paginación / filtros) y qué mejorarías.

### Reto 3: Reutilizar resultados
Un programa convierte el mismo texto a mayúsculas en varios sitios (mismo texto, muchas veces).  
Explica cómo evitarías repetir esa conversión.
