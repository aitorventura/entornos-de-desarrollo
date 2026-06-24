# Actividad 5.2: Series de televisión

## Objetivo

Que el alumno demuestre que es capaz de identificar clases, relaciones y multiplicidades a partir de una descripción en lenguaje natural, y de representarlas correctamente en un diagrama de clases UML.

## Enunciado

El sistema que se debe desarrollar tiene como objetivo gestionar una plataforma de series de televisión.

- El sistema registra **series de televisión**, que tienen un título, un género y un número de temporadas.
- Cada **serie** contiene varias **temporadas**, cada una con un número y una fecha de estreno. Las temporadas no pueden existir sin su serie.
- Cada **temporada** está dividida en varios **capítulos**. Cada capítulo tiene una duración, un título y una fecha de estreno. Los capítulos no pueden existir sin su temporada.
- Los **actores** pueden participar en diferentes series interpretando un personaje. Un actor puede estar en varias series y una serie puede tener varios actores. Los actores son independientes de las series (pueden existir aunque ninguna serie los referencie).
- Los **fans** son usuarios registrados. Se almacena su DNI, nombre y fecha de nacimiento. Un fan puede seguir varias series, y una serie puede ser seguida por muchos fans. Un fan puede dejar de seguir una serie.

## Lo que debes entregar

- El diagrama de clases en DIA (exportado como imagen o PDF).
- Justificación escrita de las decisiones tomadas (ver preguntas de profundización).

## Preguntas de profundización

1. ¿Qué tipo de relación has usado entre `Serie` y `Temporada`? ¿Y entre `Temporada` y `Capítulo`? Justifica por qué es esa y no la otra opción.
2. ¿Qué relación tiene `Actor` con `Serie`? ¿Por qué no es composición ni agregación?
3. Si un fan puede seguir varias series y una serie puede tener varios fans, ¿qué multiplicidad corresponde a cada extremo? ¿Hace falta una clase asociativa en algún caso? Razona tu respuesta.
4. ¿Has añadido roles a las relaciones? Escribe qué nombre de atributo tendría cada extremo en Java.

## Criterios de evaluación

- Las clases tienen los atributos correctos con el tipo de dato y la visibilidad adecuada.
- Las relaciones son del tipo correcto (composición, agregación, asociación) y los rombos están en el lado del todo.
- Las multiplicidades reflejan lo que dice el enunciado.
- Los roles están presentes y siguen la convención de Java (minúscula, plural si corresponde).
- Los atributos no se repiten dentro de las clases si ya están en una relación.
