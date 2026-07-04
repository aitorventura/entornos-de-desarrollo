# Actividad 6.1: ¿Qué diagrama toca?

!!! warning "Descarga la plantilla"
    📄 [Plantilla 6.1 — ¿Qué diagrama toca?](plantillas/Actividad_6_1_Plantilla.docx){target="_blank" rel="noopener"}

## Qué vas a practicar

Antes de dibujar ningún diagrama, hay que saber elegirlo. En un proyecto real nadie te dice "haz un diagrama de estados": te describen un problema y tú decides qué diagrama lo comunica mejor. Eso es exactamente lo que vas a hacer aquí.

---

## Enunciado

Para cada una de las ocho situaciones, indica en la tabla de la plantilla:

1. **Qué diagrama de comportamiento usarías** (casos de uso, secuencia, comunicación, actividad o estados).
2. Una **justificación de una o dos frases**: qué pregunta responde ese diagrama que los demás no responden igual de bien.
3. En cuatro de ellas se te pide además el **descarte**: por qué NO usarías el diagrama "hermano" que parece igual de válido.

### Las situaciones

1. El cliente de una app de reparto quiere ver, antes de aprobar el presupuesto, **qué podrá hacer cada tipo de usuario** (repartidor, cliente, administrador) con la aplicación. *(Descarta también: ¿por qué no un diagrama de actividad?)*
2. Un compañero no entiende **en qué orden se llaman los objetos** `Carrito`, `Pago` y `Stock` cuando el usuario pulsa "Comprar". *(Descarta también: ¿por qué no un diagrama de comunicación?)*
3. Hay que documentar **el ciclo de vida de una incidencia** en un sistema de soporte: abierta, asignada, en curso, resuelta, cerrada, reabierta. *(Descarta también: ¿por qué no un diagrama de actividad?)*
4. El equipo quiere ver de un vistazo **qué objetos están conectados entre sí** y cuántos mensajes cruzan cada conexión, para detectar si una clase habla con demasiadas.
5. Hay que explicar al departamento de administración **el proceso completo de matrícula** de un alumno, con sus decisiones ("¿tiene pendientes?") y sus pasos en paralelo (generar carné y enviar bienvenida a la vez). *(Descarta también: ¿por qué no un diagrama de estados?)*
6. Un desarrollador nuevo pregunta **qué hace el sistema cuando el banco tarda en responder**: quién espera, quién sigue, y qué mensaje llega primero.
7. El profesor os pide modelar **cómo cambia un semáforo inteligente**: en verde, en ámbar, en rojo, y en parpadeo nocturno a partir de las 22:00.
8. La dirección del centro quiere un esquema que un **usuario sin perfil técnico** pueda entender para validar los requisitos de la nueva app de reserva de aulas.

---

## Pregunta final

**Pregunta 1.** Las situaciones 2 y 4 podrían resolverse con los dos diagramas de interacción. Explica con tus palabras qué información se ve mejor en cada uno y por qué UML mantiene los dos si "contienen lo mismo".

---

## 📤 Entregable

Rellena la plantilla y entrégala en **PDF**:

1. La tabla con las ocho situaciones resueltas y justificadas (con los cuatro descartes).
2. La respuesta a la pregunta 1.

!!! warning "Corrección oral"
    El profesor puede cambiar un matiz de cualquier situación ("¿y si además importara el tiempo exacto de cada paso?") y pedirte que razones si tu elección cambia. Si no puedes justificarla, la actividad no se supera.

## ✅ Criterios de corrección

- El diagrama elegido es adecuado a lo que se quiere comunicar en cada situación.
- Las justificaciones hablan de qué responde el diagrama, no repiten su definición de memoria.
- Los descartes explican la diferencia real entre los dos diagramas confundibles.
