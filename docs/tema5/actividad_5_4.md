# Actividad 5.4: Gestión de biblioteca

## Objetivo

Que el alumno sea capaz de distinguir entre composición y agregación en un caso real y de modelar correctamente operaciones en las clases.

## Enunciado

Una biblioteca quiere digitalizar su sistema de gestión de préstamos.

- La **biblioteca** tiene un nombre y una dirección. Su catálogo contiene una lista de libros, pero los libros no dependen exclusivamente de ella (pueden trasladarse entre sucursales).
- Cada **libro** tiene un ISBN, un título, un autor y un indicador de si está disponible. Los libros están formados por **páginas** (mínimo 40). Cada página tiene un número y el contenido del texto. Las páginas son parte integral del libro.
- Los **usuarios** tienen DNI, nombre completo y teléfono. Un usuario solo puede tener un libro prestado a la vez.
- El sistema debe permitir: verificar disponibilidad, buscar por ISBN, obtener información de un libro, agregar un libro y ver el historial de préstamos de un usuario.

## Lo que debes entregar

- El diagrama de clases en DIA.
- Respuestas a las preguntas de profundización.

## Preguntas de profundización

1. La biblioteca tiene libros, pero los libros pueden existir fuera de ella. ¿Qué relación usas: composición o agregación? ¿Y entre libro y páginas? Justifica cada decisión.
2. El enunciado menciona varias operaciones del sistema (buscar por ISBN, verificar disponibilidad…). ¿En qué clase las colocas? ¿Por qué?
3. Para representar que un usuario solo puede tener un libro prestado a la vez, ¿qué multiplicidad pones en la relación? ¿Y en el otro extremo?
4. ¿Hace falta una clase `Prestamo` o con la relación entre `Usuario` y `Libro` es suficiente? Argumenta tu decisión.

## Criterios de evaluación

- La distinción composición/agregación está bien aplicada y justificada.
- Las operaciones están en la clase correcta con la firma adecuada.
- Las multiplicidades reflejan las restricciones del enunciado.
- Los atributos tienen tipo de dato y visibilidad.
