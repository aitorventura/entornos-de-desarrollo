# Actividad 4.1: Optimización básica en Java

!!! warning "Descarga la plantilla"
    📄 [Plantilla 4.1 — Optimización básica en Java](plantillas/Actividad_4_1_Plantilla.docx){target="_blank" rel="noopener"}

!!! info "Objetivo"
    Aplicar mejoras sencillas de rendimiento y demostrar que las entiendes:

    - El programa hace lo **mismo** antes y después (mismos resultados).
    - Puedes explicar **por qué** mejora, no solo que mejora.
    - Conectas cada mejora con los tipos de optimización que has visto en teoría.

---

## Instrucciones generales

Para **cada ejercicio A, B y C** sigue estos pasos en orden:

1. **Predice** — antes de ejecutar, anota qué esperas ver (¿cuál crees que será más rápido y por qué?).
2. **Ejecuta** — copia el código en IntelliJ y ejecútalo. Anota los tiempos y valores de salida.
3. **Aplica la mejora** — modifica el código donde se indica (hay un `TODO` que lo señala).
4. **Vuelve a ejecutar** — anota los nuevos tiempos. Compara con la predicción.
5. **Explica** — responde por escrito a las preguntas de cada ejercicio (ver más abajo).

!!! tip "Sobre las mediciones"
    Ejecuta cada versión **3 veces** y usa el tiempo más representativo (el más bajo o la media aproximada). Los tiempos varían entre ejecuciones por el sistema operativo, la JVM y otros procesos en segundo plano.

!!! warning "Lo que no vale"
    No basta con copiar los tiempos y escribir «es más rápido porque usa una estructura más eficiente». Tienes que explicar **qué hace internamente** cada estructura o técnica que justifique la diferencia.

---

## Ejercicio A: Búsqueda repetida (List vs HashSet)

**Situación:** buscas el mismo dato 20.000 veces dentro de una lista de 50.000 elementos.

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
        System.out.println("List.contains:  " + (t2 - t1) / 1_000_000 + " ms");

        System.out.println("Aciertos set:   " + aciertosSet);
        System.out.println("HashSet.contains: " + (t4 - t3) / 1_000_000 + " ms");
    }
}
```

### Antes de ejecutar — predice

Responde estas preguntas **sin ejecutar todavía**:

- ¿`aciertosLista` y `aciertosSet` van a ser iguales? ¿Por qué?
- ¿Cuál esperas que sea más rápido? ¿Por qué motivo?

### Trabajo a realizar

Una vez hayas ejecutado:

1. ¿Ha coincidido tu predicción con el resultado? Si no ha coincidido, ¿en qué has fallado en tu razonamiento?
2. Explica en 4–6 líneas por qué `HashSet.contains` es más rápido que `List.contains`. No uses solo la palabra «eficiente» — explica qué hace cada estructura cuando busca un elemento.
3. Clasifica esta optimización según los tipos que has visto en teoría: ¿es local o global? ¿independiente o dependiente de la máquina? Justifica la respuesta.

!!! warning "Trampa frecuente"
    Nota que el código mide el tiempo del `HashSet.contains`, no el tiempo de construir el `HashSet`. ¿Qué pasaría si también incluyeras en la medición el tiempo de `new HashSet<>(emails)`? ¿Cuándo dejaría de compensar usar un `HashSet`?

---

## Ejercicio B: Concatenación de Strings en bucle

**Situación:** construyes un texto grande sumando cadenas dentro de un bucle.

### Código

```java
public class EjercicioB {

    public static void main(String[] args) {

        // --- Antes: concatenación con + en bucle ---
        long t1 = System.nanoTime();
        String texto = "";
        for (int i = 0; i < 20_000; i++) {
            texto += "Línea " + i + "\n";    // crea un objeto String nuevo en cada vuelta
        }
        long t2 = System.nanoTime();
        System.out.println("Longitud texto: " + texto.length());
        System.out.println("Con +:          " + (t2 - t1) / 1_000_000 + " ms");

        // --- TODO: reescribe aquí el mismo resultado usando StringBuilder ---
        // Pista: StringBuilder sb = new StringBuilder();
        //        sb.append("Línea " + i + "\n");
        //        String resultado = sb.toString();
        //
        // Mide el tiempo igual que arriba y comprueba que resultado.length() es el mismo.
    }
}
```

### Antes de ejecutar — predice

- ¿Por qué crees que usar `+` dentro de un bucle puede ser más lento que `StringBuilder`?
- ¿Cuántos objetos `String` nuevos se crean aproximadamente en el primer bucle?

### Trabajo a realizar

1. Reescribe el segundo bloque usando `StringBuilder`. Verifica que `resultado.length()` coincide con `texto.length()`.
2. Anota los tiempos de ambas versiones.
3. Explica en 4–6 líneas qué hace Java internamente con `texto += "..."` en cada iteración y por qué eso genera trabajo extra.
4. ¿Es esta optimización local o global? ¿Independiente o dependiente de la máquina? Justifica.

!!! tip "Pista para la explicación"
    Los `String` en Java son inmutables: no se pueden modificar una vez creados. Cuando haces `texto += algo`, Java crea un objeto `String` nuevo con el resultado, copia el contenido antiguo y añade lo nuevo. Eso ocurre 20.000 veces. `StringBuilder` trabaja sobre un buffer interno que se amplía cuando hace falta, sin copiar el contenido entero cada vez.

---

## Ejercicio C: Cálculo repetido dentro de un bucle

**Situación:** en un bucle muy largo repites un cálculo cuyo resultado nunca cambia.

### Código

```java
public class EjercicioC {

    public static void main(String[] args) {

        int precio = 100;
        int unidades = 500_000;

        // --- Antes: cálculo repetido en cada vuelta ---
        long t1 = System.nanoTime();
        int total = 0;
        for (int i = 0; i < unidades; i++) {
            int precioConIVA = (int) (precio * 1.21); // mismo resultado siempre, se recalcula 500.000 veces
            total += precioConIVA;
        }
        long t2 = System.nanoTime();

        System.out.println("Total: " + total);
        System.out.println("Recalculando dentro: " + (t2 - t1) / 1_000_000 + " ms");

        // --- TODO: mueve el cálculo de precioConIVA FUERA del bucle y vuelve a medir ---
        // Verifica que "Total" no cambia.
    }
}
```

### Antes de ejecutar — predice

- ¿Crees que mover un cálculo tan sencillo fuera del bucle va a producir una diferencia apreciable?
- Anota tu estimación antes de medir.

### Trabajo a realizar

1. Mueve `precioConIVA` fuera del bucle. Comprueba que `Total` no varía.
2. Compara tiempos. ¿Ha coincidido con tu predicción?
3. Explica en 4–6 líneas: ¿por qué el compilador JIT de la JVM podría ya estar haciendo esta optimización automáticamente? ¿Qué implicación tiene eso para tus mediciones?
4. Clasifica la optimización (local/global, independiente/dependiente). Justifica.

!!! note "Sobre el JIT"
    La JVM incluye un compilador JIT (Just-In-Time) —un componente que detecta qué partes del código se ejecutan muchas veces y las optimiza automáticamente en tiempo de ejecución—. Es posible que en este ejercicio la diferencia de tiempos sea pequeña precisamente porque el JIT ya detecta que el cálculo no cambia. Eso no significa que sea mala práctica sacar el cálculo fuera: tu código queda más claro y no dependes de que el JIT lo detecte.

---

## Ejercicio D: Diseñar una optimización global (sin código)

Los ejercicios anteriores son optimizaciones **locales**: cambias un fragmento concreto. Este ejercicio trabaja una optimización **global**: la mejora afecta al diseño de cómo el sistema accede a los datos, y no se puede ver en un bucle `for`.

**Situación:** una aplicación muestra un catálogo de productos. La base de datos tiene 50.000 productos. Cada vez que el usuario abre la pantalla de catálogo, el programa carga los 50.000 registros en memoria y luego muestra solo los primeros 20.

Describe por escrito (8–12 líneas) cómo cambiarías este diseño. Tu respuesta debe incluir:

- Qué técnica usarías para que el sistema solo cargue lo que necesita (paginación, filtros en la consulta, límite de resultados...).
- Qué problema concreto tiene el diseño actual con la memoria y el tiempo de respuesta cuando hay 50.000 registros. ¿Qué pasaría si fueran 500.000?
- Por qué esta mejora no aparece en los tiempos de un bucle `for` local, sino en el comportamiento real de la aplicación cuando la usa un usuario.
- Si esta optimización es local o global, e independiente o dependiente de la máquina. Justifica.

!!! tip "Pista"
    La idea clave es que sea la base de datos quien filtre, no el programa. En SQL sería algo como `SELECT ... LIMIT 20 OFFSET 0`. No hace falta que escribas SQL — solo que expliques la idea con tus palabras. Lo que se valora es que razonas sobre el impacto en memoria y tiempo, no que uses terminología técnica.

---

## Pregunta de síntesis

Responde en 4–6 líneas:

De los ejercicios A, B, C y D, ¿cuál crees que tiene más impacto en una aplicación real? ¿Por qué? ¿Hay alguno que no optimizarías si el código ya es claro y va bien? Razona tu respuesta — no hay una respuesta única correcta.

---

## Entregable

Entrega un **PDF** con:

1. **Ejercicios A, B y C**: para cada uno, las predicciones previas, los tiempos medidos (antes y después) y las respuestas a las preguntas de trabajo.
2. **Ejercicio D**: la descripción escrita de 8–12 líneas.
3. **Pregunta de síntesis**: respuesta de 4–6 líneas.

!!! warning "Importante"
    Se valora la capacidad de explicar el *por qué*, no solo el *qué*. Dos resultados iguales con explicaciones distintas se corrigen de forma distinta.
