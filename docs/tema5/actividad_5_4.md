# Actividad 5.4: Series de televisión

!!! warning "Descarga la plantilla"
    📄 [Plantilla 5.4 — Series de televisión](plantillas/Actividad_5_4_Plantilla.docx){target="_blank" rel="noopener"}

## Qué vas a practicar

Primer diagrama completo a partir de una especificación: identificar clases, atributos, relaciones y multiplicidades a partir de una descripción en lenguaje natural, y representarlo todo correctamente en UML. Aplica la técnica de [la teoría](notacion-y-especificaciones.md): sustantivos → clases, datos → atributos, "está compuesto de" → relación.

## Enunciado

El sistema que se debe desarrollar tiene como objetivo gestionar una plataforma de series de televisión, proporcionando información detallada sobre las series, temporadas, capítulos, actores y fans que interactúan con ellas.

El sistema debe permitir registrar varias **series** de televisión, las cuales tienen un título, un género y un número de temporadas asociadas. Cada serie puede contener varias **temporadas**, cada una con un número y una fecha de estreno. A su vez, cada temporada se divide en varios **capítulos**, las unidades básicas de contenido: cada uno tiene una duración, un título y una fecha de estreno.

Los **actores** son una parte fundamental del sistema. Un actor puede participar en diferentes series, interpretando un personaje en particular. Los actores son independientes de las series: una serie puede existir sin tener actores asociados, y un actor puede estar involucrado en diversas producciones. De cada actor se registra el nombre y la fecha de nacimiento.

Por otro lado, los **fans** son usuarios registrados que siguen las series. Se almacena su DNI, nombre y fecha de nacimiento. Un fan puede seguir varias series al mismo tiempo, y puede dejar de seguir alguna si ya no le interesa. Una serie puede ser seguida por muchos fans.

La información debe gestionarse de manera que, si se elimina una serie o una temporada, todos los elementos que la componen se eliminen también.

## Herramienta

Dibuja el diagrama en **DIA** y exporta el resultado como imagen o PDF.

---

## Preguntas de profundización

1. ¿Qué tipo de relación has usado entre `Serie` y `Temporada`? ¿Y entre `Temporada` y `Capitulo`? Justifica con la frase del enunciado que lo indica.
2. ¿Qué relación tiene `Actor` con `Serie`? ¿Por qué no es composición ni agregación... o sí es una de las dos? Argumenta.
3. Si un fan puede seguir varias series y una serie puede tener varios fans, ¿qué multiplicidad corresponde a cada extremo? ¿Haría falta una clase asociativa en algún caso? Razona tu respuesta.
4. ¿Has añadido roles a las relaciones? Escribe qué nombre de atributo tendría cada extremo si esto se tradujera a Java.

---

## 📤 Entregable

Rellena la plantilla y entrégala en **PDF**:

1. Captura del diagrama completo hecho en DIA.
2. Respuestas a las cuatro preguntas de profundización.

!!! warning "Corrección oral"
    El profesor puede pedirte que expliques cualquier relación, multiplicidad o atributo de tu diagrama. Si no puedes justificarlo con el enunciado en la mano, la actividad no se supera.

## ✅ Criterios de corrección

- Las clases tienen los atributos correctos con su tipo de dato y una visibilidad adecuada.
- Las relaciones son del tipo correcto y los rombos están en el lado del "todo".
- Las multiplicidades reflejan lo que dice el enunciado.
- Los roles siguen la convención de Java (minúscula, plural si corresponde).
- Ningún atributo repite información que ya aporta una relación.
