# 🧪 Actividad 3.2: Pruebas de caja blanca

!!! warning "Descarga la plantilla"
    📄 [Plantilla 3.2 — Pruebas de caja blanca](plantillas/Actividad_3_2_Plantilla.docx){target="_blank" rel="noopener"}

!!! info "Objetivo"
    Aplicar la técnica de **pruebas de caja blanca (camino básico)** para analizar un programa Java paso a paso:
    dibujar el diagrama de flujo, calcular la complejidad ciclomática, identificar los caminos independientes
    y diseñar casos de prueba que los cubran todos.

Esta actividad sigue exactamente los mismos pasos del ejemplo resuelto de la sección anterior.
Si en algún paso te atascas, revisa ese ejemplo antes de preguntar.

---

## 🔹 Código base a analizar

```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner teclado = new Scanner(System.in);
        int n, suma = 0, conta = 0, suma2 = 0, total_num = 0;
        double media;

        System.out.println("Introduce n: (0 para acabar)");
        n = teclado.nextInt();

        while (n != 0) {
            if (n >= 20 && n <= 50) {
                suma += n;
                conta++;
            } else {
                suma2 += n;
            }
            total_num++;
            n = teclado.nextInt();
        }

        if (conta == 0) {
            media = 0;
        } else {
            media = (double) suma / conta;
        }

        System.out.println("La media es " + media + ", has introducido " 
                + total_num + " números, y suma2 vale " + suma2);
    }
}
```

---

## 🔹 Pasos de análisis (camino básico)

### Paso 1 — Análisis del código

Lee el código con calma e identifica:

- ¿Qué datos de entrada pide?
- ¿Cuándo termina de pedir datos?
- ¿Qué calcula o clasifica con cada número introducido?
- ¿Qué muestra al final?

Escribe una explicación en texto libre (3–5 líneas) que responda a estas preguntas.
No hace falta que sea técnica: bastará con que alguien que no sepa Java entienda qué hace el programa.

!!! tip "Pista"
    El programa calcula varias cosas a la vez con cada número que introduces.
    Fíjate bien en las dos estructuras de control que tiene: un bucle y dos condicionales.
    Cada una hace una cosa diferente.

---

### Paso 2 — Diagrama de flujo de control

Dibuja el **grafo de flujo de control** del programa. No es un diagrama de flujo genérico:
en este grafo cada **nodo** representa un bloque de instrucciones secuenciales,
y cada **arista** representa una transferencia de control (bifurcación, bucle o continuación).

Numera los nodos de 1 en adelante. Dibuja el grafo a mano o con cualquier herramienta (draw.io, papel...).

!!! tip "Cómo identificar los nodos"
    Cada vez que el código se bifurca (`if`, `while`) o vuelve a un punto anterior (fin del bucle),
    empieza un nodo nuevo. Las instrucciones que se ejecutan siempre juntas (sin ninguna bifurcación)
    forman un único nodo.

!!! warning "Cuidado con el bucle"
    El bucle `while` crea un nodo de condición que tiene dos aristas de salida:
    una cuando la condición es verdadera (entra en el cuerpo) y otra cuando es falsa (sale del bucle).
    Además, el final del cuerpo del bucle tiene una arista de vuelta hacia ese nodo de condición.

---

### Paso 3 — Complejidad ciclomática

Con el grafo dibujado, calcula la **complejidad ciclomática** usando la fórmula:

**M = E − N + 2**

donde **E** es el número de aristas y **N** el número de nodos.

Cuenta las aristas y los nodos del grafo que acabas de dibujar y aplica la fórmula.
El resultado te indica cuántos caminos independientes tiene el programa
y, por tanto, cuántos casos de prueba necesitas como mínimo.

!!! note "Sobre los nodos de decisión"
    También puedes calcularlo como **M = número de condiciones + 1**,
    contando cada `if` y cada `while` del código. Ambas fórmulas deben dar el mismo resultado.

---

### Paso 4 — Caminos independientes

Lista todos los caminos independientes que has encontrado.
Escríbelos indicando la secuencia de nodos que recorre cada uno (por ejemplo: `1 → 2 → 3 → 7 → 8`).

Para cada camino, describe en una frase qué situación representa:
¿qué tipo de datos de entrada provoca que el programa recorra ese camino?

!!! tip "¿Cuántos caminos hay?"
    El número de caminos es igual a la complejidad ciclomática que calculaste en el paso anterior.
    Si te salen más o menos, revisa el grafo.

---

### Paso 5 — Diseño de casos de prueba

Para cada camino independiente, diseña un caso de prueba concreto:

| Camino | Descripción | Entrada | Salida esperada |
|--------|-------------|---------|-----------------|
| C1     |             |         |                 |
| C2     |             |         |                 |
| ...    |             |         |                 |

La **entrada** son los números que introducirías por teclado (recuerda que el 0 termina la entrada).
La **salida esperada** es lo que el programa debería imprimir si funciona correctamente.

Calcula la salida esperada a mano antes de ejecutar el programa.

!!! warning "Calcula antes de ejecutar"
    Si ejecutas primero y apuntas lo que sale, no estás probando: estás copiando.
    El punto de los casos de prueba es saber de antemano qué debería salir y luego comprobar que coincide.

---

### Paso 6 — Ejecución y validación

Ejecuta el programa con cada caso de prueba que has diseñado y anota la salida real.
Compara con la salida esperada del paso anterior:

- Si coinciden → el programa pasa esa prueba. ✅
- Si no coinciden → hay un fallo en el código (o en tu cálculo esperado). 🔴

Documenta los resultados en una tabla similar a la del paso 5, añadiendo una columna de resultado.

---

## ✅ Entregable

Un **PDF** que incluya, en orden:

1. Explicación del programa (Paso 1)
2. Diagrama de flujo de control con los nodos numerados (Paso 2)
3. Cálculo de la complejidad ciclomática con la fórmula aplicada (Paso 3)
4. Lista de caminos independientes con descripción (Paso 4)
5. Tabla de casos de prueba (Paso 5)
6. Resultados de la ejecución y validación (Paso 6)

!!! note "Referencia"
    Puedes usar como guía el [ejemplo resuelto de la sección anterior](casos.md).
    El proceso es exactamente el mismo, aplicado a un código diferente.
