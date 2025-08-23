<a id="codigo"></a>

# 💻 2. Código fuente, objeto y ejecutable

---

## 2.1 Del código fuente al binario: ¿cómo llega un programa a la CPU?

!!! info "Idea básica"
    Un ordenador **solo entiende ceros y unos (binario)**.  
    Los lenguajes que usamos para programar (C, Java, Python…) deben traducirse hasta llegar a ese formato.  
    Según el lenguaje, este “viaje” puede ser:  

    - **Compilado** (todo antes de ejecutar).  
    - **Interpretado** (línea a línea en el momento).  
    - **Híbrido con máquina virtual y JIT** (un punto intermedio).  

<div class="tabs-colored" markdown>

=== "⚡ Lenguaje compilado (C, C++)"
    ```mermaid
    flowchart LR
    SRC["✍️ Código fuente (.c, .cpp)"] --> COMP["⚙️ Compilador"]
    COMP --> OBJ["📄 Código objeto (.o, .obj)"]
    OBJ --> LINK["🔗 Enlazador"]
    LINK --> EXE["▶️ Ejecutable (.exe, ELF)"]
    ```
    - El código se traduce **antes de ejecutarse**.  
    - Resultado: un **ejecutable independiente** que la CPU entiende directamente.  
    - Ejemplo: programas de escritorio o videojuegos en C++.

=== "📝 Lenguaje interpretado (Python, JS)"
    ```mermaid
    flowchart LR
    SRC["✍️ Código fuente (.py, .js)"] --> INT["👩‍💻 Intérprete"]
    INT --> RUN["▶️ Ejecución directa"]
    ```
    - El código se lee **línea a línea** en tiempo real.  
    - No se genera un ejecutable clásico.  
    - Ejemplo: scripts de Python, páginas web con JavaScript.

=== "⏱️ Híbrido con VM (Java, C#)"
    ```mermaid
    flowchart LR
    SRC["✍️ Código fuente"] --> COMP["⚙️ Compilador"]
    COMP --> BYTE["📄 Bytecode (Java .class, C# CIL)"]
    BYTE --> VM["⚙️ Máquina Virtual (JVM / CLR)"]
    VM --> JIT["⏱️ Compilación JIT"]
    JIT --> RUN["▶️ Ejecución en CPU"]
    ```
    - El compilador genera un **bytecode intermedio**.  
    - Ese bytecode se ejecuta dentro de una **máquina virtual**.  
    - La VM usa **JIT** para traducir lo más usado a binario real en tiempo de ejecución.  
    - Ejemplo: aplicaciones Android (Java/Kotlin).

</div>

---

## 2.2 Compilación, ensamblado y enlazado (en compilados)

- **Compilación** → traduce el código fuente a **código objeto** (binario incompleto).  
- **Ensamblado** → organiza esas instrucciones en código máquina real.  
- **Enlazado (link)** → une todo (archivos objeto + librerías) para obtener el **ejecutable final**.

!!! note "Enlazado estático vs dinámico"
    - :material-package: **Estático** → el ejecutable incluye todo. Más grande, pero no necesita librerías externas.  
    - :material-link: **Dinámico** → el ejecutable depende de librerías externas (`.dll`, `.so`). Más ligero, pero puede fallar si faltan.  

---

## 2.3 Diferencia entre **código objeto** y **ejecutable**

<div class="tabs-colored" markdown>

=== "📄 Código objeto"
    - Archivo **intermedio** tras compilar.  
    - Tiene instrucciones en binario, pero con **marcas y símbolos sin resolver**.  
    - Ejemplo: `programa.o` (Linux), `programa.obj` (Windows).  
    - ⚠️ **No puede ejecutarse directamente**.

=== "▶️ Código binario ejecutable"
    - Archivo **final** que puedes abrir (`.exe`, ELF, Mach-O).  
    - Ya tiene todas las direcciones resueltas y librerías enlazadas.  
    - Ejemplo: `notepad.exe` en Windows, `/bin/ls` en Linux.  
    - ✅ **La CPU lo entiende directamente**.

</div>

---

## 2.4 Ejecutable y dependencias

!!! info "Ejecutable"
    Un ejecutable puede necesitar: 
     
    - Librerías (`libc.so`, `msvcrt.dll`).  
    - Archivos de configuración.  
    - Recursos extra (imágenes, sonidos, bases de datos…).  

!!! warning "Error común"
    Creer que un `.exe` lo tiene **todo dentro**.  
    En realidad, muchos programas fallan si falta una librería externa.

---

## 2.5 Interpretado vs compilado vs JIT (resumen general)

| Tipo | Cómo funciona | Ejemplo | Pros | Contras |
|------|---------------|---------|------|---------|
| **Interpretado** | El intérprete lee y ejecuta el código **línea a línea**, en tiempo real. | Python, JavaScript | + **Flexible**: se puede probar y modificar fácilmente sin recompilar. <br> + **Multiplataforma**: el mismo script puede correr en Windows, Linux o macOS siempre que haya intérprete. | – **Más lento**: porque cada instrucción se traduce al vuelo, no está preprocesada. <br> – **Depende del intérprete**: sin él, el programa no puede ejecutarse. |
| **Compilado** | Se traduce **todo el programa** de una vez a código máquina antes de ejecutarlo. | C, C++ | + **Muy rápido**: la CPU ejecuta directamente el binario, sin pasos intermedios. <br> + **Optimizable**: el compilador puede aplicar mejoras (optimizaciones) en el binario. | – **Menos flexible**: cualquier cambio en el código obliga a recompilar. <br> – **Menos portable**: el binario generado suele funcionar solo en un sistema o arquitectura concreta. |
| **JIT (Just-in-time)** | El programa se compila primero a un **código intermedio (bytecode)** y, en tiempo de ejecución, la máquina virtual traduce “al vuelo” las partes más usadas a binario. | Java (JVM), C# (.NET) | + **Equilibrio**: combina la portabilidad del bytecode con la velocidad del binario. <br> + **Adaptable**: el JIT optimiza según cómo se ejecuta el programa en cada máquina. | – **Más complejo**: necesita tanto un compilador como una máquina virtual. <br> – **Inicio más lento**: al principio puede tardar más porque compila sobre la marcha. |


---

## 2.6 Código intermedio y máquinas virtuales

!!! info "Idea clave"
    Algunos lenguajes (Java, C#) no generan binario directo, sino un **código intermedio**.  
    Ese código se ejecuta dentro de una **máquina virtual (VM)**.

<div class="tabs-colored" markdown>

=== "☕ Java"
    - El compilador genera **bytecode** (`.class`).  
    - La **JVM** lo ejecuta.  
    - Para acelerar, usa **JIT** que convierte a binario solo lo más repetido.

=== "🔷 C#"
    - El compilador genera **CIL** (Common Intermediate Language).  
    - La **CLR** lo ejecuta.  
    - También usa **JIT** para mejorar rendimiento.

</div>

!!! tip "AOT (Ahead-of-Time)"
    Significa compilar **antes de ejecutar**, evitando JIT.  
    Ejemplo: GraalVM para Java.  

---

## 2.7 Empaquetado y distribución

Un programa no siempre llega como un único archivo:

- :material-archive: **Instaladores** → `.exe`, `.msi` (Windows), `.deb`, `.rpm` (Linux).  
- :material-package-variant: **Bundling** → programa + dependencias (ej.: apps portables, Electron).  
- :material-docker: **Contenedores** → incluyen programa + librerías + mini SO (ej.: Docker).  

!!! example "Ejemplo cotidiano"
    - 🎮 Videojuego en PC → instalador clásico.  
    - 📱 App Android → archivo `.apk`.  
    - 🌐 Servicio web → contenedor Docker.

---
