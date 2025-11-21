# 🧪 Actividad 3.2: Pruebas de caja blanca

!!! info "Objetivo"
    Aplicar la técnica de **pruebas de caja blanca (camino básico)** para:

    - Analizar la **lógica interna** de un programa Java.  
    - Dibujar el **diagrama de flujo de control**.  
    - Calcular la **complejidad ciclomática**.  
    - Identificar **caminos independientes**.  
    - Diseñar y ejecutar **casos de prueba** que cubran todos los caminos.

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

1. **Paso 1 – Análisis del código**  
   Explica en detalle qué hace el programa.

2. **Paso 2 – Diagrama de flujo de control**  
   Dibuja el diagrama de flujo del programa.

3. **Paso 3 – Complejidad ciclomática**  
   Calcula la complejidad ciclomática.

4. **Paso 4 – Caminos independientes**  
   Lista los caminos independientes detectados.

5. **Paso 5 – Diseño de casos de prueba**  
   Diseña casos de prueba que cubran todos los caminos.

6. **Paso 6 – Ejecución y validación**  
   Ejecuta los casos y valida que el programa funciona según lo esperado.

---

## ✅ Entregable

Un **PDF** que incluya:

- Explicación del programa  
- Diagrama de flujo  
- Complejidad ciclomática  
- Caminos independientes  
- Casos de prueba  
- Validación final  

!!!note "Modelo"
    Puedes utilizar como modelo el ejemplo resuelto de la página anterior.
