# Actividad 6.4: Diagramas de actividad

## Objetivo

Que el alumno sea capaz de modelar flujos de trabajo con decisiones y procesos paralelos usando correctamente los elementos del diagrama de actividad.

## Diagrama 1: registro en una app móvil

### Enunciado

Modela el proceso de registro de un usuario en una aplicación móvil:

1. El usuario abre la app y selecciona "Registrarse".
2. Rellena el formulario de datos y lo envía.
3. El sistema valida los datos. Si hay errores, notifica al usuario y vuelve al formulario.
4. Si los datos son válidos, se activan **dos procesos en paralelo**:
   - Enviar correo de verificación.
   - Guardar los datos del usuario en la base de datos.
5. Cuando ambos procesos terminan, el sistema espera a que el usuario verifique el correo.
6. Si el correo no se verifica en el tiempo límite, se cancela el registro.
7. Si se verifica, se crea la sesión y el usuario entra en la app.

### Preguntas

1. ¿Qué elemento del diagrama usas para modelar los dos procesos en paralelo del paso 4?
2. ¿Cuántos nodos de fin hay en este diagrama? Identifica cada uno y cuándo se alcanza.
3. Si el envío del correo falla, ¿cómo lo añadirías al diagrama sin romper el flujo paralelo?

---

## Diagrama 2: compra en tienda online

### Enunciado

Modela el flujo de compra en una tienda online:

1. El cliente accede a la tienda y visualiza productos.
2. Puede agregar productos al carrito o no. Si no agrega ninguno, el proceso termina.
3. Si agrega productos, pasa a la pantalla de pago.
4. Puede elegir entre pagar con tarjeta o con PayPal.
5. Si el pago es exitoso, se confirma el pedido y el proceso termina.
6. Si el pago falla, se muestra un mensaje de error. El cliente puede intentarlo de nuevo o cancelar.

### Preguntas

1. El paso 4 tiene dos opciones de pago. ¿Usas un nodo de decisión o dos nodos separados? ¿Por qué?
2. ¿Dónde colocas el nodo de fin en el camino de cancelación? ¿Es el mismo nodo de fin que el del pedido confirmado?
3. Dibuja una variante en la que, si el pago falla tres veces seguidas, se bloquea la cuenta automáticamente. ¿Qué elemento necesitas añadir?

## Criterios de evaluación

- Los nodos de inicio, actividad, decisión, concurrencia y fin están correctamente representados.
- Las condiciones de las decisiones aparecen entre corchetes en las flechas.
- Las barras de concurrencia están bien usadas (una de apertura y otra de cierre).
- El flujo es coherente y no hay flechas sueltas ni caminos sin salida.
