# 📝 3. Lenguajes de programación y paradigmas
<a id="lenguajes"></a>

![Diapositivas](diapositivas/lenguajes.pdf){ type=application/pdf style="width:100%;min-height:80vh" }

!!!info "Descarga de diapositivas"
    [Descarga las diapositivas](diapositivas/lenguajes.pptx){target="_blank" rel="noopener"}

---

## 3.1 Criterios de clasificación de lenguajes

Hay cientos de lenguajes de programación. Para orientarse en ese ecosistema, los clasificamos según distintos criterios: qué tan cerca están del hardware, para qué están pensados o qué estilo de código producen. Conocer estas categorías te ayuda a entender por qué Python se usa en ciencia de datos y no en drivers, o por qué JavaScript vive en el navegador y C no.

### Nivel de abstracción

El nivel de abstracción indica qué tan lejos está el lenguaje del hardware real. Un lenguaje de **bajo nivel** habla casi en el idioma de la CPU: pocas palabras, muchos detalles, control total. Un lenguaje de **alto nivel** habla más cerca del idioma humano y deja que el compilador o intérprete se ocupe de los detalles del hardware.

Piénsalo así: darle instrucciones en ensamblador a un ordenador es como construir una silla especificando cada clavo y cada corte de madera. Programar en Python es como pedirle a un carpintero que te haga una silla: tú describes lo que quieres y él resuelve los detalles.

<div class="tabs-colored" markdown>

=== "⚙️ Bajo nivel"
    Los lenguajes de bajo nivel trabajan directamente con los registros y la memoria del procesador. El programador controla exactamente qué hace la CPU en cada momento, lo que da un rendimiento máximo pero exige conocer bien el hardware.

    - **Ejemplo principal:** Ensamblador (*Assembly*) — cada instrucción corresponde casi literalmente a una operación del procesador.
    - **Cuándo se usan:** drivers de hardware, firmware de microcontroladores, partes críticas de sistemas operativos.
    - **Por qué no se usan para todo:** son muy difíciles de escribir, leer y mantener. Un programa simple puede ocupar cientos de líneas.

=== "🧑‍💻 Alto nivel"
    Los lenguajes de alto nivel abstraen el hardware: tú escribes lógica, y el compilador o intérprete la convierte en instrucciones para la CPU. El código es más legible y portable — el mismo programa puede correr en Windows, Linux y macOS sin cambiarlo.

    - **Ejemplos:** Python, Java, JavaScript, C#, Kotlin.
    - **Cuándo se usan:** aplicaciones web, apps móviles, herramientas de análisis de datos, casi todo el software de usuario.
    - **Por qué no lo controlan todo:** al abstraer el hardware, cedes algo de control y rendimiento. No es un problema para la mayoría de los proyectos.

</div>

!!! note "¿Y C?"
    C ocupa una posición intermedia: es más legible que el ensamblador, pero sigue dando acceso directo a memoria y punteros. Por eso se usa tanto en sistemas operativos (Linux está escrito en C) y en dispositivos con pocos recursos.

---

### Propósito y dominio de aplicación

Algunos lenguajes son de **propósito general**: sirven para casi cualquier tipo de programa. Otros son de **dominio específico** (*Domain-Specific Language*, DSL): se diseñaron para resolver un problema concreto y no tienen sentido fuera de ese contexto.

| Tipo | Descripción | Ejemplos | Cuándo usarlo |
|------|-------------|----------|---------------|
| **Propósito general** | Sirven para casi cualquier aplicación | Java, Python, C++ | Cuando el proyecto no encaja en un dominio específico |
| **Dominio específico (DSL)** | Creados para una tarea muy concreta | SQL (bases de datos), HTML/CSS (web), MATLAB (cálculo numérico) | Cuando el problema encaja exactamente en su área |

Dentro de los lenguajes de propósito general, la comunidad suele asociar cada uno con un área donde destaca:

| Área | Lenguajes habituales | Por qué |
|------|----------------------|---------|
| **Sistemas operativos y drivers** | C, C++, Rust | Acceso directo al hardware, sin VM |
| **Aplicaciones web** | JavaScript, PHP, Python, Java | Grandes ecosistemas de frameworks web |
| **Datos e inteligencia artificial** | Python, R, Julia | Librerías especializadas (NumPy, pandas, TensorFlow) |
| **Aplicaciones móviles** | Kotlin (Android), Swift (iOS) | Integración nativa con cada plataforma |
| **Dispositivos embebidos e IoT** | C, Rust | Bajo consumo de memoria y energía |

---

## 3.2 Tipado de lenguajes

El **tipo de dato** define qué clase de valor almacena una variable (número entero, texto, booleano…) y qué operaciones se pueden hacer con ella. Los lenguajes difieren en cuándo comprueban esos tipos y qué tan estrictos son al respecto. Estas diferencias afectan directamente a cuántos errores detectas en compilación y cuántos llegan a producción.

### Cuándo se comprueban los tipos

<div class="tabs-colored" markdown>

=== "🔒 Tipado estático"
    El compilador revisa que los tipos sean correctos **antes de ejecutar el programa**. Si intentas sumar un número con un texto, el compilador lo detecta y no deja compilar.

    ```java
    // Java — tipado estático
    int edad = 25;
    String nombre = "Ana";
    int resultado = edad + nombre;  // ❌ Error en compilación: tipos incompatibles
    ```

    El error aparece mientras desarrollas, no cuando el programa está en manos del usuario.

    **Lenguajes:** Java, C, C++, Rust, Kotlin, TypeScript.

=== "🔓 Tipado dinámico"
    Los tipos se comprueban **mientras el programa se ejecuta**. Puedes asignar cualquier valor a cualquier variable sin declarar su tipo, lo que hace el código más corto y flexible.

    ```python
    # Python — tipado dinámico
    x = 5        # x es un entero
    x = "hola"   # ahora x es un string; Python no protesta
    ```

    La contrapartida es que los errores de tipo pueden aparecer en producción, cuando el programa ya está en uso.

    **Lenguajes:** Python, JavaScript, Ruby, PHP.

</div>

### Cuánta libertad dan con los tipos

Estático o dinámico describe *cuándo* se comprueban los tipos. Fuerte o débil describe *cuánto* permite el lenguaje mezclarlos:

| | **Fuerte** | **Débil** |
|---|---|---|
| **Qué hace** | No mezcla tipos sin conversión explícita | Convierte tipos automáticamente |
| **Ventaja** | Menos errores silenciosos | Código más corto |
| **Riesgo** | Más verboso al escribir | Resultados inesperados difíciles de detectar |
| **Ejemplo** | Python, Java | JavaScript, PHP |

<div class="tabs-colored" markdown>

=== "🐍 Python — fuerte"
    ```python
    # Python no convierte tipos distintos automáticamente
    resultado = "3" + 2   # TypeError: no puedes sumar str e int directamente

    # Hay que ser explícito:
    resultado = int("3") + 2   # → 5
    ```
    El error aparece de inmediato y dice exactamente qué ocurrió. Nada de sorpresas.

=== "🌐 JavaScript — débil"
    ```javascript
    console.log("3" + 2);   // "32"  → convierte el 2 a string y concatena
    console.log("3" - 2);   // 1     → aquí sí convierte "3" a número
    console.log(true + 1);  // 2     → true se convierte en 1
    console.log([] + []);   // ""    → dos arrays vacíos suman una cadena vacía
    ```
    Las conversiones automáticas parecen cómodas, pero producen comportamientos que ningún programador espera de forma intuitiva. Son una fuente clásica de bugs difíciles de encontrar.

</div>

!!! warning "Débil no significa malo"
    Un tipado débil no hace al lenguaje peor, pero sí exige más cuidado. JavaScript tiene tipado débil porque en sus primeros años se priorizó la facilidad de uso en el navegador. TypeScript nació precisamente para añadirle tipado estático encima.

### Inferencia de tipos

Algunos lenguajes con tipado estático pueden **deducir el tipo automáticamente** según el valor que asignas. Así mantienes la seguridad de un tipado estático sin tener que escribir el tipo en cada variable.

```kotlin
// Kotlin — el compilador deduce el tipo, no hace falta declararlo
val edad = 25         // el compilador sabe que es Int
val nombre = "Ana"    // el compilador sabe que es String
val precio = 9.99     // el compilador sabe que es Double
```

El resultado es código más limpio que Java clásico, pero con las mismas garantías de seguridad en compilación.

---

## 3.3 Paradigmas de programación

Un **paradigma** es una forma de pensar y organizar el código. No es una característica técnica del lenguaje, sino un estilo: define cómo describes lo que el programa tiene que hacer. La misma tarea —filtrar una lista, gestionar usuarios, manejar un clic— se puede escribir de formas muy distintas según el paradigma.

La mayoría de los lenguajes modernos soportan varios paradigmas a la vez. Java empezó siendo puramente orientado a objetos y fue incorporando elementos funcionales. Python es multiparadigma desde el principio.

<div class="tabs-colored" markdown>

=== "📜 Imperativo / Procedimental"
    Es el estilo más cercano a cómo funciona la CPU: una lista de instrucciones que se ejecutan en orden, una detrás de otra. Describes exactamente *cómo* tiene que hacer el trabajo el programa, paso a paso.

    ```c
    // C — estilo imperativo: le dices al programa qué hacer en cada paso
    int suma = 0;
    for (int i = 1; i <= 10; i++) {
        suma += i;    // acumula el valor en cada iteración
    }
    printf("Suma: %d\n", suma);
    ```

    **Para qué sirve:** algoritmos directos, sistemas con hardware cercano, cualquier lógica donde el orden importa explícitamente.
    **Lenguajes:** C, Pascal. También presente en Python, Java y casi todos los demás.

=== "📦 Orientado a objetos (POO)"
    El código se organiza en **clases** —moldes que definen estructura y comportamiento— y **objetos** —instancias concretas de esas clases—. Cada objeto tiene sus propios datos y las operaciones que puede hacer con ellos.

    ```java
    // La clase es el molde
    class Coche {
        String marca;
        int velocidad;

        void acelerar(int incremento) {
            velocidad += incremento;   // modifica el estado del propio objeto
        }
    }

    // Los objetos son los coches concretos, cada uno con su propio estado
    Coche miCoche = new Coche();
    miCoche.marca = "Toyota";
    miCoche.acelerar(50);   // solo afecta a miCoche, no a otros objetos Coche
    ```

    **Para qué sirve:** modelar problemas donde hay entidades con estado propio (usuarios, productos, vehículos…). Es el paradigma dominante en el desarrollo de software empresarial.
    **Lenguajes:** Java, C++, C#, Kotlin, Python.

=== "➕ Funcional"
    En lugar de describir *cómo* hacer algo paso a paso, describes *qué* quieres obtener aplicando funciones. Las funciones son puras —dado el mismo input, siempre producen el mismo output— y no modifican datos externos.

    ```java
    // Imperativo: describes el cómo
    List<Integer> pares = new ArrayList<>();
    for (int n : numeros) {
        if (n % 2 == 0) pares.add(n);
    }

    // Funcional (Java con streams): describes el qué
    List<Integer> pares = numeros.stream()
        .filter(n -> n % 2 == 0)   // filtra los que cumplan la condición
        .collect(Collectors.toList());
    ```

    **Para qué sirve:** transformaciones de datos, procesamiento en paralelo, código más predecible porque no hay estado que cambie inesperadamente.
    **Lenguajes:** Haskell, Scala, Elixir. También en Python, Java (streams), JavaScript (map/filter/reduce).

=== "📐 Lógico"
    No describes ni *cómo* hacerlo ni *qué* transformar: describes **hechos** y **reglas**, y el motor del lenguaje deduce la respuesta por sí solo.

    ```prolog
    % Hechos: quién es humano
    humano(socrates).
    humano(platon).

    % Regla: todo humano es mortal
    mortal(X) :- humano(X).
    ```

    Si preguntas `?- mortal(socrates).` el sistema responde `true` sin que hayas escrito ningún bucle ni condición. Simplemente aplicó la regla.

    **Para qué sirve:** sistemas expertos, inteligencia artificial clásica, resolución de problemas con restricciones (horarios, configuraciones).
    **Lenguajes:** Prolog. Es el menos común en el día a día, pero conceptualmente muy diferente a los demás.

=== "🖱️ Orientado a eventos"
    El programa no se ejecuta de arriba a abajo. Registra **manejadores** —funciones que esperan a que ocurra algo— y queda a la espera. Cuando llega el evento (un clic, un mensaje, una respuesta de red), se ejecuta el manejador correspondiente.

    ```javascript
    // Este código no hace nada hasta que el usuario haga clic
    document.getElementById("boton").addEventListener("click", function() {
        alert("¡Botón pulsado!");
    });
    // El navegador sigue funcionando con normalidad
    // hasta que ocurra el evento
    ```

    **Para qué sirve:** interfaces gráficas, aplicaciones web en el navegador, cualquier sistema que responda a acciones del usuario o del entorno.
    **Lenguajes:** JavaScript en el navegador es el ejemplo más claro. También presente en frameworks de escritorio y móviles.

=== "⚡ Reactivo"
    El programa funciona con **flujos de datos**: en lugar de pedir un valor cuando lo necesitas, te *suscribes* a él y recibes actualizaciones automáticamente cada vez que cambia.

    La analogía más sencilla es una hoja de cálculo: cuando cambias el valor de una celda, todas las celdas que dependen de ella se actualizan solas. No tienes que ir a refrescarlas manualmente.

    ```javascript
    // Ejemplo conceptual: suscripción a un flujo de datos
    // Cada vez que el usuario escribe en el buscador, se lanza una búsqueda automáticamente
    busqueda$.subscribe(termino => {
        buscarResultados(termino);   // se ejecuta solo cuando cambia el valor
    });
    ```

    **Para qué sirve:** aplicaciones con datos en tiempo real (chats, paneles de monitorización, resultados en vivo). Algunos frameworks modernos de frontend aplican este principio para actualizar la interfaz automáticamente cuando cambian los datos subyacentes.

    **Lenguajes y herramientas:** es un estilo, no un lenguaje. Se puede aplicar en JavaScript, Java o Python usando librerías específicas. En DAW/DAM lo encontrarás más adelante cuando trabajes con frameworks frontend.

</div>

---

## 3.4 Ecosistemas y estándares

Los lenguajes no los inventa una sola empresa y punto. Muchos evolucionan a través de **organismos y procesos formales** que garantizan que distintos compiladores e intérpretes se comporten igual.

¿Por qué importa? Si no hubiera estándar para C, el código que compilas con `gcc` podría no funcionar con `clang`. Con el estándar, el comportamiento está definido y cualquier compilador que lo siga produce el mismo resultado.

| Lenguaje | Organismo / proceso | Qué regula |
|---|---|---|
| **C / C++** | ISO (International Organization for Standardization) | Comportamiento de los compiladores. El estándar más usado hoy es C++20. |
| **JavaScript** | ECMA International → especificación **ECMAScript** (ES) | La sintaxis y el comportamiento del lenguaje. ECMAScript es el nombre formal del estándar; cada año sale una versión nueva (ES2015, ES2022…). |
| **Python** | **PEPs** (Python Enhancement Proposals) — propuestas públicas de mejora | Cualquiera puede proponer un PEP; la comunidad debate y un comité decide si se acepta. Así entró en Python la sintaxis de f-strings o el operador `:=`. |
| **Java** | **JSRs** (Java Specification Requests) a través del JCP (Java Community Process) | Cómo evoluciona la plataforma Java. Empresas y desarrolladores participan votando y revisando propuestas. |

!!! note "El ecosistema también importa"
    Un lenguaje no es solo su sintaxis. El **ecosistema** —librerías, frameworks, comunidad, documentación, herramientas— es muchas veces más decisivo que el lenguaje en sí. Python en ciencia de datos tiene NumPy, pandas y TensorFlow. JavaScript en frontend tiene React, Vue y Angular. Aprender el lenguaje es la mitad; el ecosistema es la otra mitad.

---

## 3.5 Elección del lenguaje según el proyecto

Elegir un lenguaje no es cuestión de cuál te gusta más. Depende del entorno donde va a correr el programa, qué rendimiento necesitas, qué librerías existen y qué sabe el equipo. En la práctica, muchos proyectos mezclan más de un lenguaje: un backend en Java, un frontend en JavaScript, scripts de automatización en Python.

| Escenario | Lenguajes habituales | Razón principal |
|-----------|----------------------|-----------------|
| **Sistemas operativos y drivers** | C, C++, Rust | Control directo del hardware, sin capa intermedia |
| **Web — frontend (navegador)** | JavaScript, TypeScript | Es el único lenguaje que ejecutan los navegadores de forma nativa |
| **Web — backend (servidor)** | Python, Java, Node.js, PHP | Grandes ecosistemas de frameworks web |
| **Aplicaciones móviles** | Kotlin (Android), Swift (iOS) | Integración nativa con el SDK de cada plataforma |
| **Datos e inteligencia artificial** | Python, R | Librerías maduras para análisis y aprendizaje automático |
| **Embebidos e IoT** | C, Rust | Bajo consumo de memoria, sin necesidad de VM |

!!! tip "Tu caso concreto"
    **DAW** → trabajarás sobre todo con JavaScript en frontend y Java, Python o PHP en backend.  
    **DAM** → trabajarás principalmente con Kotlin para Android.

---

## 3.6 Perfil de los lenguajes más comunes

Esta tabla resume los lenguajes que aparecerán con más frecuencia en el módulo. Úsala como referencia rápida, no como una clasificación definitiva: muchos lenguajes evolucionan y amplían su ámbito con el tiempo.

| Lenguaje | Nivel | Tipado | Paradigma principal | Uso típico |
|---|---|---|---|---|
| **C** | Medio-bajo | Estático, fuerte | Procedimental | SO, drivers, firmware, embebidos |
| **Java** | Alto | Estático, fuerte | Orientado a objetos | Apps empresariales, Android, backend |
| **Python** | Alto | Dinámico, fuerte | Multiparadigma | Datos, IA, scripting, web |
| **JavaScript** | Alto | Dinámico, débil | Eventos, funcional | Frontend web, backend (Node.js) |
| **Kotlin** | Alto | Estático, con inferencia | OO + funcional | Android, apps multiplataforma |
| **Rust** | Medio-alto | Estático, fuerte | Multiparadigma | Sistemas de alto rendimiento, embebidos |
