
# 🧪 Actividad 1.4: Clasifica, compara y justifica lenguajes

!!! info "Objetivo"
    Demostrar que entiendes cómo se clasifican los lenguajes de programación y qué paradigma usa cada uno, razonando tus decisiones en lugar de memorizar definiciones.

---

## Parte A. Clasifica estos fragmentos de código

Analiza cada fragmento e indica:

- **Paradigma principal** que usa (imperativo/procedimental, orientado a objetos, funcional, lógico, orientado a eventos).
- **Una razón concreta** por la que lo has clasificado así. No vale decir solo "porque usa clases" o "porque usa funciones" — explica *qué ves en el código* que te lleva a esa conclusión.

---

**Fragmento 1**

```python
numeros = [1, 2, 3, 4, 5, 6]
pares = list(filter(lambda x: x % 2 == 0, numeros))
dobles = list(map(lambda x: x * 2, pares))
print(dobles)
```

---

**Fragmento 2**

```java
class Vehiculo {
    private String modelo;
    private int velocidad;

    public Vehiculo(String modelo) {
        this.modelo = modelo;
        this.velocidad = 0;
    }

    public void acelerar(int cantidad) {
        velocidad += cantidad;
    }

    public String getEstado() {
        return modelo + " va a " + velocidad + " km/h";
    }
}

Vehiculo v = new Vehiculo("Seat");
v.acelerar(80);
System.out.println(v.getEstado());
```

---

**Fragmento 3**

```javascript
document.getElementById("enviar").addEventListener("click", function(evento) {
    let nombre = document.getElementById("nombre").value;
    alert("Hola, " + nombre);
});
```

---

**Fragmento 4**

```c
int suma = 0;
for (int i = 1; i <= 10; i++) {
    suma += i;
}
printf("Suma: %d\n", suma);
```

---

**Fragmento 5**

!!! note "Contexto: Prolog"
    Prolog es un lenguaje del paradigma **lógico**: en lugar de decirle al ordenador *cómo* calcular algo, le describes *hechos* y *reglas*, y él deduce las respuestas. La sintaxis básica:

    - `hecho(a, b).` → declara que `a` y `b` tienen esa relación.
    - `regla(X, Z) :- condicion1(X, Y), condicion2(Y, Z).` → "X y Z cumplen la regla si existe Y tal que se cumplen las dos condiciones".
    - `?- consulta.` → pregunta al sistema si algo es cierto.

```prolog
padre(juan, maria).
padre(juan, pedro).
padre(pedro, luis).
abuelo(X, Z) :- padre(X, Y), padre(Y, Z).
```

Preguntas sobre este fragmento:

1. ¿Qué paradigma usa y qué lo diferencia de los fragmentos anteriores?
2. ¿Qué devolvería la consulta `?- abuelo(juan, _).`? Razona tu respuesta antes de buscarlo o probarlo.

---

## Parte B. Elige el lenguaje adecuado

Para cada escenario, elige el lenguaje más adecuado de la lista y justifica tu elección con al menos **dos criterios** (tipado, paradigma, ecosistema, rendimiento, portabilidad, plataforma destino…).

**Lenguajes disponibles:** C, Java, Python, JavaScript, Kotlin, SQL

| Escenario | Lenguaje elegido | Justificación (≥ 2 criterios) |
|---|---|---|
| Una app Android para registrar gastos personales | | |
| Un script que analiza un CSV con 10.000 filas de ventas y genera estadísticas | | |
| Un **driver** — programa de bajo nivel que permite al sistema operativo comunicarse con un dispositivo hardware como una tarjeta de red | | |
| Una página web con un formulario de contacto que valida los campos antes de enviarse | | |
| Una consulta a una base de datos para obtener todos los pedidos del último mes | | |
| Una aplicación de gestión de empleados para una empresa mediana | | |

!!! tip "Cómo justificar bien"
    No basta con "Python es fácil". Razona desde el problema: ¿qué limitaciones tiene el entorno? ¿qué rendimiento necesita? ¿hay librerías específicas que importan? ¿en qué plataforma se ejecutará? Dos criterios bien argumentados valen más que cinco superficiales.

---

## Parte C. Tipado fuerte vs débil — predice el resultado

Sin ejecutar el código, escribe en tu documento qué salida producirá cada línea o si dará error. Después ejecútalo y compara:

- **Python** → ve a [online-python.com](https://www.online-python.com), pega el código y pulsa el botón verde **Run**.
- **JavaScript** → abre cualquier navegador, pulsa **F12**, haz clic en la pestaña **Consola** y escribe cada línea pulsando Enter después de cada una.

**Python** (tipado fuerte y dinámico):
```python
print("5" + 5)
print(str(5) + "5")
print(True + 1)
```

**JavaScript** (tipado débil y dinámico):

!!! note "Contexto"
    En JavaScript, `[]` es un array vacío. Las operaciones entre tipos distintos intentan convertir automáticamente antes de operar. Los resultados a veces son sorprendentes.

```javascript
console.log("5" + 5);
console.log("5" - 5);
console.log(false + 1);
console.log([] + []);
```

Para cada línea responde:
- ¿Qué predijiste?
- ¿Qué salió realmente?
- Si no coincide: ¿qué regla de conversión automática crees que aplicó el lenguaje?

---

## Parte D. Reflexión final

Responde con tus propias palabras (4-6 líneas cada pregunta). No copies definiciones de los apuntes: redacta con tus palabras y apóyate en ejemplos propios si puedes.

**1.** ¿Cuál es la diferencia entre tipado **estático** y **dinámico**? Pon un ejemplo concreto de ventaja de cada uno en un proyecto real (no vale repetir los del enunciado).

**2.** Un compañero te dice: *"Python y JavaScript son lo mismo, los dos son interpretados y dinámicos."* ¿En qué tiene razón y en qué se equivoca? Pista: fíjate en los resultados de la Parte C y en la diferencia entre tipado fuerte y débil.

**3.** Imagina que te contratan para hacer una app y te dicen: *"Elige el lenguaje que quieras."* ¿Qué preguntas harías antes de decidir? Menciona al menos cuatro criterios que considerarías y explica por qué cada uno importa.

---

## Entregable

!!! note "Plantilla"
    Completa la plantilla disponible en [plantillas/Actividad_1_4_Plantilla.docx](plantillas/Actividad_1_4_Plantilla.docx) y entrégala exportada como **PDF** en el Aula Virtual.

!!! warning "Criterio de evaluación"
    Se valora el **razonamiento**, no la respuesta correcta en sí. Una respuesta equivocada bien argumentada demuestra más comprensión que una respuesta correcta sin justificación.
