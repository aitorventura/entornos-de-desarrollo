# Actividad 6.6: Diagramas de comunicación

!!! warning "Descarga la plantilla"
    📄 [Plantilla 6.6 — Diagramas de comunicación](plantillas/Actividad_6_6_Plantilla.docx){target="_blank" rel="noopener"}

## Qué vas a practicar

Los diagramas de comunicación por las dos vías: traduciendo un diagrama de secuencia que ya tienes (la información es la misma, cambia el énfasis) y elaborando dos desde cero, con la numeración jerárquica de mensajes como protagonista.

## Requisitos previos

- El diagrama de secuencia del restaurante de la actividad 6.5 terminado.

---

## Parte A — Traducción: el restaurante como comunicación

**Paso 1.** Traduce tu diagrama de secuencia del restaurante (actividad 6.5, Parte A) a un diagrama de comunicación siguiendo los tres pasos de [la teoría](interaccion.md#33-de-secuencia-a-comunicacion-y-vuelta): coloca los objetos, une con canales las parejas que se hablan y numera los mensajes en el orden en que ocurrían.

**Pregunta A.1.** ¿Cuántos canales de comunicación tiene tu diagrama? ¿Coincide con el número de parejas de objetos que se enviaban mensajes en el de secuencia?

**Pregunta A.2.** Con los dos diagramas delante: ¿cuál enseñarías para explicar *el orden* del proceso y cuál para detectar *qué objeto acumula más conexiones*? ¿Por qué?

---

## Parte B — Gestión de pedidos en una tienda online

Una tienda en línea de tecnología necesita mejorar su sistema de gestión de pedidos. El proceso involucra a:

- **Cliente**: realiza pedidos y consulta su estado.
- **Sistema de Pedidos**: registra el pedido y lo gestiona.
- **Administrador**: aprueba o rechaza pedidos según disponibilidad.
- **Sistema de Inventario**: verifica el stock de productos.
- **Sistema de Pagos**: procesa el pago del cliente.

Modela con un diagrama de comunicación el proceso completo desde que el cliente hace un pedido hasta que se confirma o rechaza.

**Pregunta B.1.** Si el mensaje con el que el Sistema de Pedidos consulta el stock es el `2:`, y esa consulta desencadena una respuesta interna del Sistema de Inventario, ¿qué número le corresponde? Explica la regla de los subniveles.

**Pregunta B.2.** ¿Qué papel juega el Administrador en tu diagrama: recibe mensajes, los envía, o ambas cosas? ¿En qué momento del flujo interviene?

---

## Parte C — Sistema de envíos express

Una empresa de envíos express ha digitalizado su logística. El proceso involucra a:

- **Cliente**: solicita el envío de un paquete y consulta su estado.
- **Sistema de Gestión de Envíos**: registra la solicitud y organiza la entrega.
- **Repartidor**: recoge y entrega el paquete.
- **Sistema de Almacén**: gestiona la clasificación y almacenamiento de los paquetes.
- **Sistema de Notificaciones**: envía actualizaciones al cliente sobre el estado del envío.

Modela el proceso desde que el cliente solicita el envío hasta que el paquete es entregado.

**Pregunta C.1.** El Sistema de Notificaciones envía mensajes al cliente en varios momentos del proceso. ¿Cómo se refleja eso en un diagrama de comunicación (canales y numeración)?

**Pregunta C.2.** ¿Qué ventaja tiene el diagrama de comunicación en este caso concreto frente al de secuencia? Piensa en cuántos objetos hay y quién habla con quién.

---

## 📤 Entregable

Rellena la plantilla y entrégala en **PDF**:

1. Captura del diagrama de comunicación del restaurante (Parte A).
2. Capturas de los diagramas de las Partes B y C hechos en DIA.
3. Respuestas a las preguntas A.1, A.2, B.1, B.2, C.1 y C.2.

!!! warning "Corrección oral"
    El profesor puede pedirte que reconstruyas el orden del proceso leyendo solo la numeración de tu diagrama, o que traduzcas un trozo a secuencia. Si no puedes hacerlo, la actividad no se supera.

## ✅ Criterios de corrección

- El diagrama de la Parte A contiene exactamente los mismos mensajes que el de secuencia original.
- Los objetos están conectados mediante canales y los mensajes tienen dirección (flecha) y nombre de operación.
- La numeración es coherente con el flujo y los subniveles se usan correctamente.
