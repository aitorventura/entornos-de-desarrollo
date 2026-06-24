# Actividad 6.3: Diagramas de comunicación

## Objetivo

Que el alumno sea capaz de representar las interacciones entre objetos usando diagramas de comunicación, numerando los mensajes correctamente y comparando el resultado con el diagrama de secuencia equivalente.

## Diagrama 1: gestión de pedidos en tienda online

### Enunciado

Una tienda online de tecnología tiene el siguiente flujo de gestión de pedidos. Los actores son:

- **Cliente**: realiza pedidos y consulta su estado.
- **Sistema de pedidos**: registra y gestiona el pedido.
- **Administrador**: aprueba o rechaza pedidos según disponibilidad.
- **Sistema de inventario**: verifica el stock de productos.
- **Sistema de pagos**: procesa el pago del cliente.

Modela el proceso completo desde que el cliente hace un pedido hasta que se confirma o rechaza.

### Preguntas

1. ¿Cuántos canales de comunicación distintos hay en tu diagrama?
2. ¿Qué diferencia visual hay entre tu diagrama de comunicación y un diagrama de secuencia del mismo proceso?
3. Numera los mensajes correctamente. Si el sistema de inventario envía un subnivel de respuesta al sistema de pedidos, ¿qué número le pondrías si el mensaje principal es el `2`?

---

## Diagrama 2: sistema de envíos express

### Enunciado

Una empresa de envíos express tiene el siguiente proceso. Los actores son:

- **Cliente**: solicita el envío y consulta su estado.
- **Sistema de gestión de envíos**: registra la solicitud y organiza la entrega.
- **Repartidor**: recoge y entrega el paquete.
- **Sistema de almacén**: clasifica y almacena los paquetes.
- **Sistema de notificaciones**: envía actualizaciones al cliente.

Modela el proceso desde que el cliente solicita el envío hasta que el paquete es entregado.

### Preguntas

1. El sistema de notificaciones envía mensajes al cliente en varios momentos del proceso. ¿Cómo lo representas en el diagrama?
2. ¿Qué ventaja tiene usar un diagrama de comunicación en este caso frente a uno de secuencia?

## Criterios de evaluación

- Los objetos están identificados y conectados mediante canales de comunicación.
- Los mensajes están numerados y tienen la dirección correcta (flecha).
- Los subniveles de numeración son coherentes con el flujo.
