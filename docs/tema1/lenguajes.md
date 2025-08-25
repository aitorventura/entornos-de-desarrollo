# 📝 3. Lenguajes de programación y paradigmas
<a id="lenguajes"></a>

---

## 3.1 Criterios de clasificación de lenguajes

!!! info "Idea clave"
    Los lenguajes de programación no son todos iguales. Podemos **clasificarlos** según distintos criterios, lo que nos ayuda a entender **cómo se usan, qué tan fáciles son y para qué sirven**.

### 🔹 Según el nivel de abstracción

<div class="grid cards" markdown>
-   :material-cog: **Lenguajes de bajo nivel**  
    - 🔡 Cercanos al lenguaje máquina.  
    - 🖥️ Ejemplo: **Ensamblador**.  
    - ✅ Pros: control total del hardware.  
    - ❌ Contras: muy difíciles de aprender y mantener.  
    - ⚙️ Uso típico: sistemas embebidos, drivers, firmware.  

-   :material-laptop: **Lenguajes de alto nivel**  
    - 🧑‍💻 Cercanos al lenguaje humano.  
    - 🌍 Ejemplos: **Python, Java, C#**.  
    - ✅ Pros: fáciles de aprender, portables.  
    - ❌ Contras: menos control directo sobre el hardware.  
    - 📱 Uso típico: apps web, móviles, software de usuario.  
</div>

---

### 🔹 Según el propósito

| Tipo | Características | Ejemplos | Uso típico |
|------|-----------------|----------|------------|
| :material-application: **Generales** | Sirven para casi cualquier aplicación | Java, Python, C++ | Desarrollo de software en general |
| :material-target: **De dominio específico (DSL)** | Creado para tareas concretas | SQL, HTML/CSS, MATLAB | Bases de datos, web, cálculo científico |

---

### 🔹 Según el dominio de aplicación

<div class="grid cards" markdown>
-   :material-chip: **Sistemas**  
    - Lenguajes pensados para interactuar con hardware y SO.  
    - Ejemplos: **C, C++**.  

-   :material-web: **Aplicaciones web**  
    - Enfocados a Internet y servidores.  
    - Ejemplos: **JavaScript, PHP**.  

-   :material-database: **Datos / IA**  
    - Análisis, big data, machine learning.  
    - Ejemplos: **Python, R, Julia**.  

-   :material-cellphone: **Móviles**  
    - Para apps en Android/iOS.  
    - Ejemplos: **Kotlin, Swift**.  

-   :material-memory: **Embebidos**  
    - Para dispositivos con pocos recursos.  
    - Ejemplos: **C, Rust**.  
</div>


---

## 3.2 Tipado de lenguajes

!!! info "¿Qué es el tipado?"
    El **tipo de dato** (número, texto, booleano, etc.) define qué operaciones se pueden hacer.  
    Según el lenguaje, los **tipos se controlan de formas distintas**, lo que afecta a la seguridad, flexibilidad y facilidad de programación.

---

### 🔹 Según el **momento** en que se comprueban

<div class="grid cards" markdown>
-   :material-shield-check: **Estático**  
    - El compilador revisa los tipos **antes de ejecutar**.  
    - Ejemplos: **Java, C, Rust**.  
    - ✅ Ventaja: detecta muchos errores en la fase de compilación → más seguro.  
    - ❌ Inconveniente: más estricto, hay que declarar todo con detalle.  

-   :material-play: **Dinámico**  
    - Los tipos se verifican **mientras se ejecuta**.  
    - Ejemplos: **Python, JavaScript, Ruby**.  
    - ✅ Ventaja: más flexible y rápido de escribir (menos código).  
    - ❌ Inconveniente: errores de tipos pueden aparecer en **tiempo de ejecución**.  
</div>

---

### 🔹 Según la **rigidez** en el uso de tipos

| Tipo | Descripción | Ejemplo | Resultado |
|------|-------------|---------|-----------|
| :material-lock: **Fuerte** | No permite mezclar tipos sin conversión explícita. | `Python: "3" + 2` | ❌ Error |
| :material-link: **Débil** | Hace conversiones automáticas (a veces inesperadas). | `JavaScript: "3" + 2` | `"32"` |

!!! warning "Atención"
    Un lenguaje de tipado **débil** puede producir resultados extraños sin avisar, lo que genera **bugs difíciles de detectar**.  

---

### 🔹 Inferencia de tipos

Algunos lenguajes **deducen automáticamente** el tipo de una variable según el valor que se le asigna.

```kotlin
// Kotlin
val x = 5        // El compilador entiende que x es un Int
val nombre = "Ana" // El compilador entiende que es un String
```

- ✅ Ventaja: ahorra escritura y mantiene seguridad de tipos.  
- ❌ Inconveniente: a veces el tipo deducido no es el esperado si no se tiene cuidado.  


---

## 3.3 Paradigmas de programación

!!! info "Idea clave"
    Un **paradigma** es un **estilo de programación**, es decir, la manera en que se organiza y estructura el código.  
    👉 Un mismo lenguaje puede soportar **varios paradigmas**.

<div class="grid cards" markdown>

-   :material-code-braces: **Imperativo / Procedimental**  
    - 📜 El programa es una **secuencia de instrucciones** paso a paso.  
    - 🔧 Uso típico: algoritmos simples, sistemas básicos.  
    - 🖥️ Ejemplo: **C**.  

-   :material-cube: **Orientado a Objetos (POO)**  
    - 📦 Código organizado en **clases y objetos**.  
    - 🔄 Cada objeto tiene **atributos (datos)** y **métodos (acciones)**.  
    - 🖥️ Ejemplo: **Java, C++**.  

-   :material-function-variant: **Funcional**  
    - ➕ Se centra en **funciones puras** (sin efectos secundarios).  
    - 🔄 Evita modificar datos directamente.  
    - 🖥️ Ejemplo: **Haskell, Scala, Elixir**.  

-   :material-lightbulb-on-outline: **Lógico**  
    - 📐 Basado en **reglas y hechos**.  
    - 🤖 El programa **deduce soluciones** automáticamente.  
    - 🖥️ Ejemplo: **Prolog**.  

-   :material-mouse: **Orientado a eventos**  
    - 🖱️ El flujo depende de **eventos externos** (clics, señales…).  
    - 🌐 Muy común en interfaces gráficas y la web.  
    - 🖥️ Ejemplo: **JavaScript en navegadores**.  

-   :material-sync: **Reactivo**  
    - ⚡ Pensado para **datos en tiempo real y asincronía**.  
    - 🔄 Se adapta a flujos de información continuos.  
    - 🖥️ Ejemplo: **RxJava, frameworks modernos (Angular, React)**.  
</div>


---

## 3.4 Ecosistemas y estándares

Los lenguajes suelen estar regulados por **organismos y estándares**:

- **ISO C/C++** → definen cómo deben funcionar los compiladores.  
- **ECMA** → regula JavaScript (ECMAScript).  
- **PEPs (Python Enhancement Proposals)** → propuestas de mejora en Python.  
- **JSRs (Java Specification Requests)** → definen cómo evoluciona Java.  

---

## 3.5 Elección del lenguaje según escenario

| Escenario | Lenguajes típicos | Razón |
|-----------|------------------|-------|
| **Sistemas operativos / drivers** | C, C++ | Control cercano al hardware |
| **Web (frontend)** | JavaScript, TypeScript | Se ejecuta en navegadores |
| **Web (backend)** | Python, Java, Node.js | Gran ecosistema y frameworks |
| **Móviles** | Kotlin (Android), Swift (iOS) | Integración nativa |
| **Datos / IA** | Python, R | Librerías para análisis y ML |
| **Embebidos / IoT** | C, Rust | Bajo consumo, eficiencia |

---

## 3.6 Casos comparativos breves

!!! abstract "Lenguaje C"
    - 🏷️ **Nivel**: medio-bajo.  
    - 🛡️ **Tipado**: estático y fuerte.  
    - 🧩 **Paradigma**: procedimental.  
    - ⚙️ **Usos típicos**: sistemas operativos, drivers, software embebido.  

---

!!! abstract "Java"
    - 🏷️ **Nivel**: alto.  
    - 🛡️ **Tipado**: estático y fuerte.  
    - 🧩 **Paradigma**: orientado a objetos.  
    - 📱 **Usos típicos**: aplicaciones empresariales, Android, sistemas distribuidos.  

---

!!! abstract "Python"
    - 🏷️ **Nivel**: alto.  
    - 🛡️ **Tipado**: dinámico y fuerte.  
    - 🧩 **Paradigma**: multiparadigma (imperativo, POO, funcional).  
    - 🤖 **Usos típicos**: ciencia de datos, IA, scripting, desarrollo web.  

---

!!! abstract "JavaScript"
    - 🏷️ **Nivel**: alto.  
    - 🛡️ **Tipado**: dinámico y débil.  
    - 🧩 **Paradigma**: orientado a eventos, funcional.  
    - 🌐 **Usos típicos**: frontend web, backend (Node.js), apps híbridas.  

---

!!! abstract "Rust"
    - 🏷️ **Nivel**: medio-alto.  
    - 🛡️ **Tipado**: estático y fuerte.  
    - 🧩 **Paradigma**: multiparadigma.  
    - ⚡ **Usos típicos**: sistemas de alto rendimiento, programación segura, embebidos.  

---

!!! abstract "Kotlin"
    - 🏷️ **Nivel**: alto.  
    - 🛡️ **Tipado**: estático, con inferencia.  
    - 🧩 **Paradigma**: orientado a objetos + funcional.  
    - 📱 **Usos típicos**: Android, aplicaciones multiplataforma, backend.  
