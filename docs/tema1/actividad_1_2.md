# 🧪 Actividad 1.2: Compilar e interpretar programas

---

## 🎯 Objetivo de la actividad

!!! info "Qué vas a aprender"
    - **Compilar** y **ejecutar** programas en **C** y **Java**.  
    - **Interpretar** un script en **Python**.  
    - Conocer y usar compiladores e intérpretes: `gcc` (C), `python3` (Python), `javac/java` (Java).  
    - Documentar el proceso con **capturas de pantalla** y una **reflexión personal**.  

---

## 📸 Entregables esperados (antes de empezar)

Para que no se te olvide, durante toda la actividad debes guardar estas **capturas de pantalla**:

1. 📥 Instalación de cada herramienta (`gcc`, `python3`, `java`).  
2. 📄 Archivos creados (`ejemploC.c`, `ejemploPython.py`, `Ejemplo.java`).  
3. 🖥️ Código fuente abierto en el editor (nano).  
4. ⚙️ Compilación en C y Java (comando + resultado).  
5. ▶️ Ejecución de los tres programas en terminal (C, Python, Java).  
6. 📂 Vista de la carpeta `ejemploscodigo` mostrando los ejecutables generados.  
7. 📝 Documento final con tu **explicación** y una **conclusión personal** sobre las diferencias entre **compilar** e **interpretar**.

---

## 🛠️ Herramientas necesarias

- Máquina virtual con **Ubuntu Server** instalada.  
- **Compilador C (gcc/MinGW)**.  
- **Python 3**.  
- **JDK (Java Development Kit)**.

!!! tip "Recuerda"
    En el Aula Virtual tienes un tutorial para crear la máquina virtual en Ubuntu.  
    Si ya la tienes lista, puedes continuar directamente.

---

## 🔹 Paso 1. Crear los programas de ejemplo

Primero, crea la carpeta de trabajo y los archivos vacíos:

```{.bash .copy}
mkdir ejemploscodigo
cd ejemploscodigo
touch ejemploC.c ejemploPython.py ejemploJava.java
```

Ahora edita cada archivo con `nano` u otro editor y pega el código:

<div class="tabs-colored" markdown>

=== "👨‍💻 Programa en C"
```{.c .copy}
/* Programa: Suma de dos números */
#include <stdio.h>

int main() {
    int n1, n2, suma;

    printf("\n Introduzca primer numero (entero): ");
    scanf("%d", &n1);

    printf("\n Introduzca segundo numero (entero): ");
    scanf("%d", &n2);

    suma = n1 + n2;
    printf("\n La suma es: %d\n", suma);

    // Pausa
    printf("\n Presione Enter para salir...");
    getchar(); 
    getchar(); 
    
    return 0;
}
```

=== "🐍 Programa en Python"
```{.python .copy}
# Programa: Suma de dos números 
n1 = int(input("Ingrese primer número: ")) 
n2 = int(input("Ingrese segundo número: ")) 
suma = n1 + n2 
print("La suma es:", suma) 
```

=== "☕ Programa en Java"
```{.java .copy}
import java.util.Scanner;

public class Ejemplo {
    public static void main(String[] args) {
        int n1, n2, suma;
        Scanner teclado = new Scanner(System.in);
        
        System.out.print("Introduce primer numero entero: "); 
        n1 = teclado.nextInt();
        
        System.out.print("Introduce segundo numero entero: "); 
        n2 = teclado.nextInt();
        
        suma = n1 + n2;
        System.out.println("La suma es: " + suma); 

        teclado.close(); 
    }
}
```
</div>

📸 **Capturas aquí:**  
- Vista de la carpeta `ejemploscodigo` con los tres archivos.  
- Cada archivo abierto en nano mostrando el código escrito.  

---

## 🔹 Paso 2. Instalar compiladores e intérpretes

### a) Instalar compilador C (gcc)

```{.bash .copy}
sudo apt update
sudo apt upgrade
sudo apt install gcc
```

### b) Instalar Python

```{.bash .copy}
python3 --version
sudo apt install python3
```

### c) Instalar JDK (Java Development Kit)

```{.bash .copy}
sudo apt search openjdk
sudo apt install openjdk-17-jdk
java -version
```

📸 **Capturas aquí:**  
- Pantalla de instalación de cada herramienta (gcc, python3, java).  
- Comando `--version` mostrando que funcionan correctamente.  

---

## 🔹 Paso 3. Compilar e interpretar programas

### a) Programa en C

```{.bash .copy}
gcc ejemploC.c -o ejemploC.exe
./ejemploC.exe
```

📸 **Capturas aquí:**  
- Comando de compilación (`gcc`) y ejecutable generado.  
- Ejecución del programa mostrando la suma en terminal.  

---

### b) Programa en Python

```{.bash .copy}
python3 ejemploPython.py
```

📸 **Capturas aquí:**  
- Ejecución del script en terminal pidiendo datos y mostrando resultado.  

---

### c) Programa en Java

⚠️ Recuerda: el archivo debe llamarse como la clase pública (`Ejemplo`).  

```{.bash .copy}
mv ejemploJava.java Ejemplo.java
javac Ejemplo.java
ls   # aparece Ejemplo.class (bytecode)
java Ejemplo
```

📸 **Capturas aquí:**  
- Comando `javac` y el archivo `Ejemplo.class` generado.  
- Ejecución del programa con `java Ejemplo` mostrando la suma.  

---

## ✅ Entregables finales

El resultado debe ser un **documento único en PDF o Word** con:

1. Capturas de instalación de cada lenguaje (gcc, python3, java).  
2. Código escrito en C, Python y Java.  
3. Ejecución en terminal de los tres programas.  
4. Explicación breve de los pasos seguidos.  
5. Conclusión personal: **diferencias entre compilar (C, Java) e interpretar (Python)**.

