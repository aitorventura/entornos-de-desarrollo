# Actividad 5.6: Plataforma de videojuegos

!!! warning "Descarga la plantilla"
    📄 [Plantilla 5.6 — Plataforma de videojuegos](plantillas/Actividad_5_6_Plantilla.docx){target="_blank" rel="noopener"}

## Qué vas a practicar

Este sistema añade lo que faltaba: **herencia**, una **clase asociativa**, una relación de una clase **consigo misma** y un atributo con **valor por defecto**. Es el diagrama más completo hasta ahora; léelo dos veces antes de dibujar nada.

## Enunciado

Una empresa de desarrollo de videojuegos está creando una plataforma digital en la que los usuarios pueden registrarse para comprar juegos, jugar partidas y recibir soporte técnico. Sin embargo, no todos los usuarios tienen las mismas funciones dentro del sistema.

**Usuarios en la plataforma.** Existen dos tipos de usuarios: jugadores y administradores. Los **jugadores** disfrutan de los juegos: para registrarse proporcionan un nombre de usuario, un correo electrónico y una contraseña, además de contar con un ID único. A medida que usan la plataforma su nivel aumenta. Además, pueden agregar otros jugadores a su lista de amigos. Los **administradores** no participan en las partidas ni compran juegos, pero tienen un atributo adicional llamado permisos y su función principal es gestionar los tickets de soporte.

**Juegos y catálogo.** Cada **juego** tiene un ID único, un título, el nombre de la desarrolladora, un precio, una categoría (como "Acción" o "Estrategia") y un tipo que indica si es para un jugador o multijugador. Para facilitar la organización, los juegos pueden agruparse en **catálogos**, con un ID y un nombre. Un juego puede existir sin estar dentro de ningún catálogo.

**Compras y métodos de pago.** Para acceder a un juego, un jugador debe comprarlo. Cada vez que esto ocurre, la plataforma registra una **compra** con su ID, la fecha, el monto total y el estado del pago, que puede ser "Pendiente", "Completado" o "Fallido" (por defecto, Pendiente). Para completar la compra, el jugador selecciona un **método de pago** (tarjeta, PayPal o criptomoneda) con un ID, un tipo y los datos de pago cifrados.

## Herramienta

Dibuja el diagrama en **DIA** y exporta el resultado como imagen o PDF.

---

## Preguntas de profundización

1. ¿Qué relación has usado para modelar que `Jugador` y `Administrador` son tipos de usuario? ¿Qué atributos han subido a la clase padre y cuáles se han quedado abajo? ¿Por qué?
2. La relación entre `Jugador` y `Juego` pasa por una `Compra`. ¿La has modelado como clase normal o como clase asociativa? Justifica tu elección.
3. Un jugador puede tener otros jugadores como amigos. ¿Cómo se dibuja una relación de una clase consigo misma y qué roles le has puesto a cada extremo?
4. El atributo `estado` del pago tiene un valor por defecto. ¿Cómo se escribe eso en notación UML?

---

## 📤 Entregable

Rellena la plantilla y entrégala en **PDF**:

1. Captura del diagrama completo hecho en DIA.
2. Respuestas a las cuatro preguntas de profundización.

!!! warning "Corrección oral"
    El profesor puede pedirte que expliques cualquier decisión: por qué un atributo está en el padre y no en la hija, o cómo has resuelto la compra. Si no puedes justificarlo, la actividad no se supera.

## ✅ Criterios de corrección

- La herencia está bien representada (flecha triangular hueca hacia el padre) y sin atributos repetidos en las hijas.
- La clase asociativa (si la hay) está correctamente vinculada a la relación.
- La asociación reflexiva de amigos tiene roles y multiplicidades con sentido.
- El valor por defecto usa la notación UML correcta.
- Los atributos tienen tipo de dato y visibilidad.
