# Actividad 5.3: Plataforma de videojuegos

## Objetivo

Que el alumno sea capaz de modelar un sistema con herencia, relaciones de varios tipos y clases asociativas a partir de una especificación detallada.

## Enunciado

Una empresa de desarrollo de videojuegos está creando una plataforma digital.

**Usuarios**

Hay dos tipos de usuario: **jugadores** y **administradores**, que comparten: nombre de usuario, correo electrónico, contraseña e ID único.

- Los **jugadores** tienen además un nivel y una lista de amigos (otros jugadores). Pueden comprar juegos y jugar partidas.
- Los **administradores** tienen un campo `permisos`. No participan en partidas ni compran juegos; su función es gestionar los tickets de soporte.

**Juegos y catálogo**

- Cada **juego** tiene: ID, título, nombre de la desarrolladora, precio, categoría y tipo (un jugador o multijugador).
- Los juegos pueden agruparse en **catálogos**, que tienen un ID y un nombre. Un juego puede existir sin estar en ningún catálogo.

**Compras**

- Cuando un jugador compra un juego se registra una **compra** con: ID, fecha, monto total y estado del pago (Pendiente por defecto, Completado o Fallido).
- Cada compra lleva asociado un **método de pago** con: ID, tipo (tarjeta, PayPal, criptomoneda) y datos de pago cifrados.

## Lo que debes entregar

- El diagrama de clases en DIA (exportado como imagen o PDF).
- Respuestas a las preguntas de profundización.

## Preguntas de profundización

1. ¿Qué relación usas para modelar que `Jugador` y `Administrador` son tipos de usuario? ¿Cómo se representa en UML?
2. La relación entre `Jugador` y `Juego` pasa por una `Compra`. ¿Es `Compra` una clase normal o una clase asociativa? Justifica tu respuesta.
3. Un jugador puede tener otros jugadores como amigos. ¿Cómo se modela una relación de una clase consigo misma?
4. ¿Qué pasa con el atributo `estado` del pago que tiene un valor por defecto? ¿Cómo se representa en UML?

## Criterios de evaluación

- La herencia está bien representada con flecha triangular hueca.
- La clase asociativa (si la hay) está correctamente vinculada a la relación.
- Las multiplicidades son correctas en todos los extremos.
- Los atributos tienen tipo de dato y visibilidad.
