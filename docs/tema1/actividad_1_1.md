# 🧪 Actividad 1.1: Del problema al programa

!!! info "Objetivo"
    Demostrar que entiendes cómo un programa transforma **entradas en salidas**, la diferencia entre **algoritmo y programa**, y qué papel juega cada **componente del hardware** cuando un programa se ejecuta.

---

## 🔹 Parte A. Identificar el modelo Entrada → Proceso → Salida

1. Piensa en **tres situaciones cotidianas** (que se puedan relacionar con la informática) donde haya claramente entrada, proceso y salida. Los ejemplos de los apuntes no valen.

2. Para cada una, rellena esta tabla:

    | Situación | Entrada | Proceso | Salida |
    |---|---|---|---|
    | | | | |
    | | | | |
    | | | | |

3. Elige **uno** de los tres casos y dibuja el diagrama de flujo correspondiente (a mano o con una herramienta como draw.io).

4. Responde por escrito: en ese caso concreto, ¿hay algún dato que podría considerarse tanto entrada como configuración del programa? Razona la respuesta.

---

## 🔹 Parte B. Algoritmo vs. programa

Describe con tus propias palabras el **algoritmo** que resuelve uno de tus tres casos de la Parte A. No escribas código: explica los pasos en lenguaje natural, como si le explicaras a alguien cómo hacerlo.

Luego responde estas preguntas:

1. ¿Podría ejecutar el ordenador directamente el algoritmo que has descrito? ¿Por qué?
2. Si quisieras implementar ese algoritmo en dos lenguajes distintos (por ejemplo, Java y Python), ¿cambiaría el algoritmo o solo el programa? Explícalo.
3. Imagina que tu programa da un resultado incorrecto. ¿Cómo distinguirías si el error está en el algoritmo o en cómo lo has escrito en el lenguaje? ¿Qué harías para comprobarlo?

---

## 🔹 Parte C. Análisis de un programa real

Estudia este programa Java. Todavía no tienes que saber escribirlo: el objetivo es leerlo y entender qué hace.

```java
import java.util.Scanner;

public class MediaNotas {
    public static void main(String[] args) {
        Scanner teclado = new Scanner(System.in); // prepara la lectura por teclado
        int suma = 0;

        for (int i = 1; i <= 3; i++) {
            System.out.print("Introduce una nota: "); // pide al usuario un dato
            int n = teclado.nextInt();                // lee el número que escribe
            suma += n;                               // lo acumula en suma
        }

        double media = suma / 3.0;                          // calcula la media
        System.out.println("La media es: " + media);        // muestra el resultado

        teclado.close();
    }
}
```

Responde:

1. Identifica con precisión qué líneas corresponden a la **entrada**, cuáles al **proceso** y cuáles a la **salida**. Copia cada línea o bloque y etiquétala.

2. ¿Qué componente del hardware entra en juego cuando el programa ejecuta `teclado.nextInt()`? ¿Y cuando ejecuta `System.out.println`? ¿Y cuando se calcula `suma / 3.0`?

3. Mientras este programa espera a que el usuario escriba una nota, ¿qué está haciendo la CPU? ¿Por qué puede ser un problema en una aplicación más compleja con muchos usuarios a la vez?

4. **Predicción antes de ejecutar:** sin ejecutar el código, ¿qué resultado imprimirá si el usuario introduce las notas `6`, `7` y `8`? Razona el cálculo paso a paso. Si tuvieras acceso a un ordenador, comprueba si tu predicción es correcta.

5. Este programa tiene una limitación: si el usuario introduce `0`, `0` y `0`, la media será 0,0, que es un resultado válido. Pero si introduce letras en lugar de números, el programa falla. ¿En qué parte del modelo E/P/S está ese problema? ¿Cómo lo resolverías conceptualmente (sin escribir código)?

---

## 🔹 Parte D. Componentes del sistema

Para el programa `MediaNotas` de la Parte C, describe qué ocurre con cada componente del hardware cuando se ejecuta. Usa la tabla como guía, pero desarrolla cada celda con una explicación real, no con una frase genérica:

| Componente | ¿Qué hace exactamente en este programa? |
|---|---|
| 💾 Disco | |
| 🧠 RAM | |
| ⚙️ CPU | |
| 🖥️ E/S | |
| 🌐 Red | |

Para la red: este programa no la usa. Pero si quisieras que `MediaNotas` enviara la nota media a un servidor para guardarla en una base de datos, ¿en qué parte del código añadirías esa funcionalidad (entrada, proceso o salida)? Razona por qué.

---

## ✅ Entregable

!!! note "Plantilla"
    Usa la plantilla oficial para entregar esta actividad: [📄 Actividad_1_1_Plantilla.docx](plantillas/Actividad_1_1_Plantilla.docx)

Un documento (PDF o entrada en el portfolio) con:

- La tabla de los tres ejemplos E/P/S y el diagrama de uno de ellos.
- Las respuestas razonadas de la Parte B (algoritmo vs programa).
- El análisis línea a línea del programa Java con las cinco preguntas respondidas.
- La tabla de componentes con explicaciones desarrolladas.

!!! warning "Criterios de corrección"
    No se valorará rellenar las celdas con frases de una línea copiadas de los apuntes. Se espera que **apliques los conceptos a este programa concreto** y que **razones** cada respuesta. Si en una corrección oral no puedes explicar lo que has escrito, la actividad no se considera superada.
