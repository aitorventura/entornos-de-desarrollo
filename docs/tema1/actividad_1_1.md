# 🧪 Actividad 1.1: Del problema al programa

!!! info "Objetivo"
    Comprender cómo un **programa** transforma **entradas** en **salidas** y qué papel juegan la **CPU, la RAM y la E/S**.

---

## 🔹 Parte A. Identificar EPS (Entrada → Proceso → Salida)

<div class="tabs-colored" markdown>

=== "Gupo presencial"
    1. Ponte en pareja con un compañero.  
    2. Pensad en **tres situaciones cotidianas** donde haya claramente entrada, proceso y salida.  
    Ejemplos (esos no valen):  
        - Cajero automático.  
        - Reproductor de música.  
        - Calculadora del móvil.  
    3. Dibujad una tabla con columnas:  

    | Entrada | Proceso | Salida |  
    |---------|---------|--------|  

    📸 Añadid un esquema rápido (a mano o con un diagrama simple) para representar el flujo.

=== "Grupo semipresencial"
    1. Piensa en **tres situaciones cotidianas** donde haya claramente entrada, proceso y salida.  
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
