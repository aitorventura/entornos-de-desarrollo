# Actividad 5.1: Clases y objetos en UML

!!! warning "Descarga la plantilla"
    📄 [Plantilla 5.1 — Clases y objetos en UML](plantillas/Actividad_5_1_Plantilla.docx){target="_blank" rel="noopener"}

## Qué vas a practicar

Antes de dibujar diagramas con muchas clases conectadas, hay que dominar la pieza básica: la caja de una clase con sus atributos, sus operaciones y su visibilidad. En esta actividad vas a traducir en las dos direcciones (código Java → UML y UML → código) y a modelar una clase de tu propia cosecha.

## Herramienta

Usa **DIA** para dibujar las clases. Exporta cada diagrama como imagen (`.png`) para pegarla en la plantilla.

---

## Parte A — De Java a UML

Aquí tienes una clase Java completa:

```java
public class EntradaConcierto {

    private static int entradasVendidas = 0;
    public static final double PRECIO_BASE = 25.0;

    private String codigo;
    private String comprador;
    protected boolean validada;

    public EntradaConcierto(String codigo, String comprador) {
        this.codigo = codigo;
        this.comprador = comprador;
        this.validada = false;
        entradasVendidas++;
    }

    public boolean validar() {
        validada = true;
        return validada;
    }

    private double calcularRecargo(double porcentaje) {
        return PRECIO_BASE * porcentaje / 100;
    }

    public static int getEntradasVendidas() {
        return entradasVendidas;
    }
}
```

**Paso 1.** Dibuja en DIA la caja UML equivalente a esta clase, con todos sus atributos y operaciones, respetando visibilidades, tipos, parámetros y valores de retorno.

!!! warning "Predicción antes de dibujar"
    Antes de abrir DIA, responde por escrito: ¿cuántos elementos de esta clase irán **subrayados** en el diagrama? ¿Qué símbolo de visibilidad llevará `validada`? ¿El constructor aparece en la caja de atributos o en la de operaciones?

**Pregunta A.1.** ¿Qué elementos has subrayado y por qué? ¿Ha coincidido con tu predicción?

**Pregunta A.2.** `calcularRecargo` es privado y `validar` es público. Explica con esta clase concreta (no con una definición de memoria) qué puede hacer otra clase con cada uno de los dos métodos.

---

## Parte B — De UML a Java

Esta caja UML representa una clase de un sistema de reservas:

```
                 Reserva
 ─────────────────────────────────────────
  - localizador : String
  - numPersonas : int
  - confirmada : boolean = false
 ─────────────────────────────────────────
  + Reserva(localizador : String, numPersonas : int)
  + confirmar() : void
  + getLocalizador() : String
  # calcularCoste(precioPorPersona : double) : double
```

**Paso 2.** Escribe la clase Java equivalente (solo cabeceras y atributos; los cuerpos de los métodos pueden quedar con un comentario `// TODO`).

**Pregunta B.1.** El atributo `confirmada` tiene un valor por defecto en el diagrama. ¿Cómo lo has trasladado al código Java?

**Pregunta B.2.** ¿Qué diferencia práctica hay entre el `#` de `calcularCoste` y el `-` de `localizador`? ¿Quién podrá llamar a `calcularCoste`?

---

## Parte C — Tu propia clase

**Paso 3.** Elige un objeto real de tu día a día que uses esta semana (tu bicicleta, tu cuenta de una app concreta, tu taquilla, la cafetera de tu casa...). No vale ninguno de los ejemplos de los apuntes ni de esta actividad.

Modélalo en DIA como una clase UML con:

- Al menos **4 atributos** con tipo y visibilidad razonada.
- Al menos **3 operaciones**, una de ellas con parámetros y valor de retorno.
- Al menos **1 miembro estático** que tenga sentido (piensa qué dato compartirían *todas* las instancias).

**Pregunta C.1.** Explica en 3-4 frases por qué has elegido esa visibilidad para cada atributo y qué representa exactamente tu miembro estático.

**Pregunta C.2.** Escribe dos **objetos** (instancias) concretos de tu clase con valores reales, y señala qué comparten y qué no.

---

## 📤 Entregable

Rellena la plantilla y entrégala en **PDF**:

1. Captura del diagrama de la Parte A hecho en DIA.
2. Predicción escrita **antes** de dibujar y respuestas A.1 y A.2.
3. Código Java de la Parte B y respuestas B.1 y B.2.
4. Captura del diagrama de tu clase (Parte C) y respuestas C.1 y C.2.

!!! warning "Corrección oral"
    El profesor puede pedirte que expliques cualquier decisión: por qué un elemento va subrayado, por qué una visibilidad y no otra, o cómo se traduce un elemento concreto a Java. Si no puedes explicarlo, la actividad no se supera.

## ✅ Criterios de corrección

- Los diagramas respetan la notación UML: visibilidades, tipos, subrayado de estáticos, formato `nombre : tipo`.
- La traducción UML ⇄ Java es coherente en ambas direcciones.
- La clase de la Parte C es personal y las decisiones están justificadas con argumentos propios.
- Las respuestas razonan sobre los ejemplos concretos, no repiten definiciones de los apuntes.
