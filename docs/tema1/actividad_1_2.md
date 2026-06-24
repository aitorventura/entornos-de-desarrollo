# 🧪 Actividad 1.2: De código fuente a ejecutable

!!! info "Objetivo"
    Compilar e interpretar programas en C, Python y Java desde la terminal, observando qué archivos se generan en cada paso y entendiendo por qué el proceso es distinto en cada lenguaje.

---

## Antes de empezar

Necesitas una máquina virtual con **Ubuntu** (Desktop o Server). Si usas una instancia EC2 en AWS, tendrá que ser Server.

!!! tip "Ayuda para crear la máquina virtual"
    En el Aula Virtual tienes un tutorial para instalarla. Si ya la tienes lista, continúa directamente.

Instala las tres herramientas necesarias desde el terminal:

```bash
# Actualiza la lista de paquetes disponibles antes de instalar
sudo apt update

# Instala el compilador de C (gcc = GNU Compiler Collection)
sudo apt install -y gcc

# Comprueba que gcc se instaló correctamente (-y acepta la instalación sin preguntar)
gcc --version

# Comprueba la versión de Python (suele venir preinstalado en Ubuntu)
python3 --version

# Instala el JDK de Java (Java Development Kit: incluye javac y java)
sudo apt install -y openjdk-17-jdk

# Confirma que Java está disponible
java -version
```

📸 **Captura**: salida de `gcc --version`, `python3 --version` y `java -version` para confirmar que todo está instalado.

---

## 🔹 Parte A — C: compilar y analizar el proceso

Crea la carpeta de trabajo y entra en ella:

```bash
mkdir actividad12   # crea la carpeta donde guardarás todos los archivos
cd actividad12      # entra en la carpeta (cd = change directory)
```

Crea el archivo `suma.c` con este contenido:

```c
#include <stdio.h>

int main() {
    int a, b;
    printf("Introduce dos números: ");
    scanf("%d %d", &a, &b);
    printf("La suma es: %d\n", a + b);
    return 0;
}
```

### Predice antes de compilar

Antes de ejecutar el comando de compilación, anota en tu documento:

> ¿Qué archivos esperas que aparezcan en la carpeta después de compilar? ¿Solo el ejecutable, o también algo más?

Ahora compila y comprueba:

```bash
gcc suma.c -o suma   # compila suma.c y genera el ejecutable llamado "suma" (-o = output)
ls -lh               # lista los archivos con tamaño legible (-l = detalle, -h = tamaño en KB/MB)
```

📸 **Captura**: contenido de la carpeta tras compilar.

!!! warning "¿Coincidió tu predicción?"
    Escribe en tu documento si acertaste o no. Si solo ves el ejecutable, busca en los apuntes por qué no se ve el código objeto (`.o`) cuando se compila directamente con `gcc -o`.

Ejecuta el programa:

```bash
./suma   # ./ indica que el ejecutable está en la carpeta actual (no en el PATH del sistema)
```

📸 **Captura**: ejecución mostrando la suma.

### Pregunta de análisis — C

Mueve el ejecutable a otra carpeta vacía e intenta ejecutarlo desde ahí:

```bash
mkdir /tmp/prueba_c        # crea una carpeta temporal vacía fuera de tu proyecto
cp suma /tmp/prueba_c/     # copia solo el ejecutable (sin el .c ni ningún otro archivo)
cd /tmp/prueba_c/          # entra en la carpeta vacía
./suma                     # intenta ejecutar
```

> ¿Funciona? ¿Qué significa eso sobre las dependencias del ejecutable? ¿Habría funcionado igual si el programa usase una librería de terceros enlazada dinámicamente?

---

## 🔹 Parte B — Python: interpretado, sin compilación previa

Vuelve a la carpeta de trabajo y crea `suma.py`:

```python
a = int(input("Introduce el primer número: "))
b = int(input("Introduce el segundo número: "))
print("La suma es:", a + b)
```

### Predice antes de ejecutar

> Con C, compilar generó un ejecutable. Con Python no hay comando de compilación. ¿Qué crees que ocurre internamente cuando ejecutas `python3 suma.py`? ¿Genera algún archivo nuevo?

Vuelve primero a la carpeta de trabajo y ejecuta:

```bash
cd ~/actividad12     # vuelve a tu carpeta de trabajo
python3 suma.py      # arranca el intérprete de Python y ejecuta el script directamente
ls -lha              # lista todos los archivos incluyendo ocultos (-a = all); fíjate si aparece algo nuevo
```

📸 **Captura**: ejecución del script y contenido de la carpeta después.

### Pregunta de análisis — Python

> Si llevas `suma.py` a un ordenador sin Python instalado, ¿puedes ejecutarlo? Compara con lo que pasaría con el ejecutable `suma` de C. ¿Cuál depende del sistema y cuál del intérprete?

---

## 🔹 Parte C — Java: compilación en dos pasos

Crea el archivo `Suma.java` (el nombre del archivo **debe coincidir** con la clase pública):

```java
import java.util.Scanner;

public class Suma {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        System.out.print("Introduce el primer número: ");
        int a = sc.nextInt();
        System.out.print("Introduce el segundo número: ");
        int b = sc.nextInt();
        System.out.println("La suma es: " + (a + b));
        sc.close();
    }
}
```

### Predice antes de compilar

> En Java el proceso tiene dos pasos. ¿Qué archivo crees que generará `javac`? ¿Será directamente un ejecutable como en C, o algo diferente?

Compila y comprueba:

```bash
javac Suma.java   # compila el .java y genera Suma.class con el bytecode
ls -lh            # observa qué archivo nuevo aparece y cuánto pesa
```

📸 **Captura**: archivo(s) generados tras `javac`.

Ejecuta:

```bash
java Suma   # arranca la JVM y le indica el nombre de la clase (sin extensión)
```

📸 **Captura**: ejecución mostrando la suma.

### Detecta el error

El siguiente comando parece correcto pero falla. Ejecútalo y explica por qué da error:

```bash
java Suma.class
```

> Escribe en tu documento el mensaje de error que aparece y, con tus propias palabras, por qué ocurre. ¿Qué espera `java` exactamente?

### La prueba WORA

Java promete que el mismo `.class` funciona en cualquier máquina con JVM instalada. Compruébalo:

```bash
mkdir /tmp/prueba_java          # crea una carpeta temporal vacía
cp Suma.class /tmp/prueba_java/ # copia solo el bytecode (sin el .java ni el código fuente)
cd /tmp/prueba_java/            # entra en la carpeta; aquí solo está el .class
ls                              # confirma que solo tienes el .class
java Suma                       # la JVM lo ejecuta; no necesita el .java para nada
```

📸 **Captura**: ejecución del `.class` desde la carpeta sin el código fuente.

> ¿Ha funcionado? ¿Qué demuestra esto sobre la diferencia entre el `.java` y el `.class`? ¿Por qué no funciona lo mismo con el ejecutable de C si cambias de sistema operativo (por ejemplo, de Linux a Windows)?

---

## 🔹 Parte D — Comparativa y distribución

Responde en tu documento con tus propias palabras (3-5 líneas por pregunta):

**1.** Has visto que C genera un ejecutable, Python no genera nada visible y Java genera un `.class`. Explica qué ventaja e inconveniente tiene cada enfoque para el desarrollador que tiene que hacer cambios frecuentes en el código.

**2.** Un compañero dice: *"Python es más lento que C porque no compila"*. ¿En qué tiene razón y en qué se equivoca? Busca qué son los archivos `.pyc` de Python y cómo encajan en esta discusión.

**3.** Imagina que tienes que entregar tu programa de suma a tres usuarios distintos que no saben programar. Rellena la tabla:

| | Usuario recibe… | Usuario necesita tener instalado… |
|---|---|---|
| **C** | | |
| **Python** | | |
| **Java** | | |

**4.** Vuelve a la carpeta de trabajo y ejecuta `ls -lh` (lista archivos con tamaño). Tienes `suma` (C), `suma.py` (Python) y `Suma.class` (Java). Si tu empresa quisiera distribuir estas tres versiones a clientes, ¿qué método de empaquetado usarías para cada una (instalador, bundle, contenedor)? Justifica al menos dos de las tres elecciones.

---

## ✅ Entregable

Un documento PDF o Word con:

1. Capturas de instalación de las tres herramientas.
2. Capturas de compilación y ejecución de cada programa (C, Python, Java).
3. La captura de la prueba WORA (`.class` ejecutado sin el `.java`).
4. La tabla de distribución (pregunta 3).
5. Respuestas a las cuatro preguntas de análisis y comparativa.

!!! note "Plantilla"
    Tienes disponible una plantilla para entregar en [plantillas/Actividad_1_2_Plantilla.docx](plantillas/Actividad_1_2_Plantilla.docx).
