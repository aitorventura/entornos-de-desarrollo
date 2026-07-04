# Actividad 5.5: Gestión de biblioteca

!!! warning "Descarga la plantilla"
    📄 [Plantilla 5.5 — Gestión de biblioteca](plantillas/Actividad_5_5_Plantilla.docx){target="_blank" rel="noopener"}

## Qué vas a practicar

Este enunciado esconde la decisión más delicada del tema: distinguir **composición** de **agregación** en un caso donde ambas parecen razonables. Además tendrás que decidir en qué clase colocas cada operación, algo que el enunciado no te da resuelto.

## Enunciado

Una biblioteca desea mejorar su sistema de gestión de préstamos mediante la digitalización de la información sobre sus usuarios y los libros que presta.

El sistema constará de una **biblioteca** que representa el espacio donde se almacenan los libros. Cada biblioteca tendrá un nombre y una dirección, y en su catálogo habrá una lista de libros disponibles para préstamo. Los libros, sin embargo, no dependen exclusivamente de una biblioteca: pueden trasladarse entre distintas sucursales o incluso ser donados.

Cada **libro** tiene un identificador único (ISBN), un título, el nombre de su autor y un indicador de si está disponible para préstamo. Los libros están formados por **páginas** (mínimo 40), que son parte integral del libro. Cada página tiene un número y el contenido del texto impreso.

Existen **usuarios** que pueden solicitar libros en préstamo, identificados por su DNI, nombre completo y teléfono. Un usuario solo podrá tener un libro prestado a la vez, y al devolverlo el libro volverá a estar disponible.

El sistema debe permitir: verificar la disponibilidad de un libro, buscar por ISBN, obtener la información de un libro, agregar un libro y ver el historial de préstamos de un usuario.

## Herramienta

Dibuja el diagrama en **DIA** y exporta el resultado como imagen o PDF.

---

## Preguntas de profundización

1. La biblioteca tiene libros, pero los libros pueden existir fuera de ella. ¿Qué relación has usado: composición o agregación? ¿Y entre libro y páginas? Justifica cada decisión con la frase del enunciado que la respalda.
2. El enunciado pide varias operaciones (buscar por ISBN, verificar disponibilidad, ver historial...). Indica en qué clase has colocado cada una y por qué ahí y no en otra.
3. Para representar que un usuario solo puede tener un libro prestado a la vez, ¿qué multiplicidad has puesto en cada extremo de la relación?
4. ¿Hace falta una clase `Prestamo` o basta con la relación entre `Usuario` y `Libro`? Argumenta tu decisión pensando en el "historial de préstamos" que pide el enunciado.

---

## 📤 Entregable

Rellena la plantilla y entrégala en **PDF**:

1. Captura del diagrama completo hecho en DIA.
2. Respuestas a las cuatro preguntas de profundización.

!!! warning "Corrección oral"
    El profesor puede pedirte que defiendas tu elección entre composición y agregación, o la ubicación de cualquier operación. Si no puedes justificarlo, la actividad no se supera.

## ✅ Criterios de corrección

- La distinción composición/agregación está bien aplicada y justificada con el enunciado.
- Las operaciones están en la clase correcta, con parámetros y tipo de retorno razonables.
- Las multiplicidades reflejan las restricciones del enunciado (incluido el mínimo de páginas).
- Los atributos tienen tipo de dato y visibilidad.
