# Actividad 6.2: Diagramas de secuencia

## Objetivo

Que el alumno sea capaz de modelar el flujo de mensajes entre objetos de un sistema real, usando correctamente los tipos de mensaje, las líneas de vida y las activaciones.

## Diagrama 1: pedido en un restaurante

### Enunciado

Modela el siguiente proceso de un sistema de pedidos por internet para un restaurante:

1. El cliente consulta el menú a través de la web.
2. Elige los platos e introduce sus datos de pago.
3. El sistema contacta con el banco para procesar el pago.
4. Una vez verificado, pasa la comanda a la cocina.
5. La cocina informa de cuánto tardará el pedido según las comandas acumuladas.
6. Se confirma el pedido al cliente y se le informa de cuándo podrá pasar a recogerlo.

### Preguntas

1. ¿Qué tipo de mensaje usarías para la llamada al banco: síncrono o asíncrono? ¿Por qué?
2. ¿Hay algún objeto que se cree durante el proceso (mensaje de creación)? ¿Cuál sería?
3. ¿Qué pasaría si el banco rechaza el pago? ¿Cómo se modelaría ese camino alternativo?

---

## Diagrama 2: reserva de hotel

### Enunciado

Modela el siguiente proceso de reserva en un sistema de hotel online:

1. El cliente busca disponibilidad para unas fechas.
2. El sistema consulta el inventario de habitaciones.
3. Se muestran las opciones disponibles al cliente.
4. El cliente selecciona una habitación y confirma la reserva.
5. El sistema crea una nueva reserva y la registra en la base de datos.
6. Se envía una confirmación por email al cliente.

### Preguntas

1. ¿Cuántos objetos distintos intervienen en este proceso? Identifícalos.
2. El paso 5 implica crear una nueva reserva. ¿Qué tipo de mensaje usarías?
3. Dibuja una variante en la que no haya habitaciones disponibles. ¿Qué cambia en el diagrama?

## Criterios de evaluación

- Las líneas de vida están correctamente representadas para cada objeto.
- Los tipos de mensaje son los adecuados (síncrono, asíncrono, creación, respuesta).
- El orden cronológico es correcto de arriba abajo.
- Las activaciones aparecen cuando el objeto está procesando una acción.
