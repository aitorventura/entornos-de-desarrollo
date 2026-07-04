# Actividad 5.2: ¿Qué relación es?

!!! warning "Descarga la plantilla"
    📄 [Plantilla 5.2 — ¿Qué relación es?](plantillas/Actividad_5_2_Plantilla.docx){target="_blank" rel="noopener"}

## Qué vas a practicar

Saber dibujar una composición no sirve de nada si no sabes *cuándo* toca usarla. En esta actividad no tienes que dibujar ningún diagrama completo: solo leer situaciones y decidir, con criterio, qué relación une cada pareja de clases. Es exactamente la decisión que tendrás que tomar una y otra vez en las actividades siguientes.

---

## Enunciado

Para cada una de las diez situaciones, indica en la tabla de la plantilla:

1. El **tipo de relación** (asociación unidireccional o bidireccional, agregación, composición, generalización/herencia, realización, dependencia o clase asociativa).
2. **Dónde va el símbolo**: en qué extremo se dibuja el rombo, la flecha o el triángulo.
3. La **multiplicidad** de cada extremo (cuando tenga sentido).
4. Una **justificación de una o dos frases** apoyada en el enunciado, no en la intuición.

### Las situaciones

1. Un `Edificio` está formado por `Habitacion`. Si el edificio se derriba, sus habitaciones desaparecen con él.
2. Un `Equipo` de baloncesto tiene una plantilla de `Jugador`. Un jugador puede ser traspasado a otro equipo, o quedarse sin equipo, y sigue existiendo.
3. La clase `GeneradorInforme` tiene un método `exportarPdf(pedido : Pedido)` que recibe el pedido, lo convierte y no lo guarda en ningún atributo.
4. Una `Moto` es un tipo de `Vehiculo`, del que toma la matrícula y el método `arrancar()`.
5. La clase `ReproductorMp3` se compromete a ofrecer las operaciones que declara `Reproducible` (`play()`, `pause()`, `stop()`), cada una con su propia implementación.
6. Un `Medico` atiende a muchos `Paciente` y un paciente puede ser atendido por varios médicos. De cada atención concreta interesa guardar la fecha y el diagnóstico.
7. En una red social, un `Usuario` puede bloquear a otros `Usuario`.
8. La app `Biblioteca` guarda la lista de sus `Libro` para poder buscarlos. Los libros no necesitan saber en qué app están.
9. Cada `Pais` tiene exactamente una `Ciudad` como capital. Una ciudad puede no ser capital de nada, pero nunca de dos países.
10. Un `CarritoCompra` contiene `LineaCarrito`. Al vaciar o eliminar el carrito, sus líneas dejan de existir.

### El descarte, tan importante como el acierto

**Pregunta 1.** En las situaciones **1** y **2**, ambas huelen a "todo y sus partes". Explica qué palabra o idea concreta del enunciado te ha hecho elegir una relación distinta en cada caso.

**Pregunta 2.** En la situación **3**, ¿por qué no es una asociación? ¿Qué tendría que cambiar en el enunciado para que lo fuera?

**Pregunta 3.** En la situación **6**, ¿por qué no basta con una asociación muchos-a-muchos normal? ¿Dónde guardarías la fecha y el diagnóstico si no existiera la clase asociativa?

**Pregunta 4.** En la situación **9**, un compañero propone composición "porque un país *tiene* una capital". Explícale en 2-3 frases por qué se equivoca.

### Tus propios ejemplos

**Paso final.** Inventa **dos situaciones propias**, de tu entorno o de tus aficiones, que no aparezcan en los apuntes ni en esta actividad:

- Una que sea claramente una **composición**.
- Otra que sea claramente una **dependencia**.

Redacta cada una en 2-3 frases (como las situaciones de arriba) e indica su solución.

---

## 📤 Entregable

Rellena la plantilla y entrégala en **PDF**:

1. La tabla con las diez situaciones resueltas y justificadas.
2. Las respuestas a las preguntas 1-4.
3. Tus dos situaciones inventadas con su solución.

!!! warning "Corrección oral"
    El profesor puede cambiar un detalle de cualquier situación ("¿y si el jugador no pudiera existir sin equipo?") y pedirte que razones en voz alta cómo cambiaría la relación. Si no puedes hacerlo, la actividad no se supera.

## ✅ Criterios de corrección

- El tipo de relación es correcto y el símbolo está situado en el extremo que toca.
- Las multiplicidades reflejan lo que dice cada enunciado, no un genérico `*` a todo.
- Las justificaciones citan la pista concreta del enunciado (vida ligada, "es un tipo de", uso breve...).
- Los dos ejemplos propios son originales y están bien clasificados.
