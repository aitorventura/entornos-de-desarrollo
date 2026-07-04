# Actividad 6.5: Diagramas de secuencia

!!! warning "Descarga la plantilla"
    📄 [Plantilla 6.5 — Diagramas de secuencia](plantillas/Actividad_6_5_Plantilla.docx){target="_blank" rel="noopener"}

## Qué vas a practicar

Elaborar diagramas de secuencia completos a partir de un enunciado: elegir los participantes, usar bien los tipos de mensaje (síncrono, asíncrono, respuesta, creación), las líneas de vida y las activaciones.

---

## Parte A — Pedido en un restaurante

Crea el diagrama de secuencia para un sistema de pedidos por Internet para un restaurante:

1. El proceso comienza con el cliente consultando el menú a través de la web.
2. Después elige los platos e introduce sus datos de pago.
3. A continuación, el sistema contacta con el banco para procesar el pago.
4. Una vez verificado, pasa la comanda a la cocina.
5. La cocina informa de cuánto tardará el pedido en función del número de comandas acumuladas.
6. Finalmente se le confirma al cliente el pedido y se le informa de cuándo podrá pasar a recogerlo.

!!! warning "Predicción antes de dibujar"
    Antes de abrir DIA, anota: ¿cuántos objetos/participantes tendrá tu diagrama? ¿Qué mensajes serán síncronos y cuáles llevarán respuesta explícita?

**Pregunta A.1.** ¿Qué tipo de mensaje has usado para la llamada al banco: síncrono o asíncrono? ¿Por qué?

**Pregunta A.2.** ¿Qué pasaría si el banco rechaza el pago? Describe (no hace falta dibujarlo) cómo cambiaría el diagrama a partir de ese punto.

---

## Parte B — Reserva de hotel

Modela el siguiente proceso de reserva en un sistema de hotel online:

1. El cliente busca disponibilidad para unas fechas.
2. El sistema consulta el inventario de habitaciones.
3. Se muestran las opciones disponibles al cliente.
4. El cliente selecciona una habitación y confirma la reserva.
5. El sistema crea una nueva reserva y la registra en la base de datos.
6. Se envía una confirmación por email al cliente.

**Pregunta B.1.** El paso 5 implica crear un objeto nuevo. ¿Qué tipo de mensaje has usado y dónde aparece el objeto `Reserva` en tu diagrama (arriba con los demás o a la altura de su creación)?

**Pregunta B.2.** El envío del email (paso 6), ¿tiene sentido que sea asíncrono? ¿Qué ganaría el sistema con ello?

---

## 📤 Entregable

Rellena la plantilla y entrégala en **PDF**:

1. Predicción de la Parte A escrita **antes** de dibujar.
2. Capturas de los dos diagramas hechos en DIA.
3. Respuestas a las preguntas A.1, A.2, B.1 y B.2.

!!! warning "Corrección oral"
    El profesor puede pedirte que recorras en voz alta cualquiera de los diagramas mensaje a mensaje. Si no puedes hacerlo, la actividad no se supera.

## ✅ Criterios de corrección

- Las líneas de vida están correctamente representadas para cada objeto.
- Los tipos de mensaje son los adecuados (síncrono, asíncrono, creación, respuesta).
- El orden cronológico es correcto de arriba abajo.
- Las activaciones aparecen cuando el objeto está procesando una acción.
