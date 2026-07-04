# Actividad 6.3: Gestión de fincas e inmuebles

!!! warning "Descarga la plantilla"
    📄 [Plantilla 6.3 — Gestión de fincas e inmuebles](plantillas/Actividad_6_3_Plantilla.docx){target="_blank" rel="noopener"}

## Qué vas a practicar

Elaborar un diagrama de casos de uso completo a partir de una descripción real: identificar actores, extraer los casos de uso (recuerda: suelen ser los verbos del enunciado) y aplicar `«include»`, `«extend»` y generalización cuando corresponda — y solo cuando corresponda.

## Enunciado

Crea el diagrama de casos de uso de una aplicación de gestión de fincas e inmuebles que tiene el siguiente funcionamiento:

La empresa que gestiona los inmuebles lo hace en calidad de propietaria.

Cada inmueble puede ser un local (local comercial, oficina, etc.), un piso o un edificio (que a su vez tiene pisos y locales). Por lo tanto, la aplicación ha de permitir introducir nuevos inmuebles, con sus datos correspondientes (dirección, número, código postal, etc.), darlos de baja, modificar sus datos y realizar consultas sobre ellos.

El hecho de que una empresa administre un edificio no quiere decir que gestione todos sus pisos y locales, por lo que la aplicación también deberá permitir introducir nuevos pisos o locales con sus datos correspondientes (planta, letra...), darlos de baja, modificarlos y hacer consultas sobre ellos.

Cualquier persona que tenga una nómina, un aval bancario, un contrato de trabajo o venga avalado por otra persona puede alquilar el edificio completo o alguno de los pisos o locales que no estén ya alquilados, y posteriormente desalquilarlo. Por ello deberán poderse dar de alta, si son nuevos inquilinos, con sus datos correspondientes (nombre, DNI, edad, sexo, fotografía...), poder modificarlos, darlos de baja, consultar, etc. **Para la realización de cualquiera de estas operaciones es necesaria la identificación por parte del inquilino.**

Cada mes el secretario de la empresa pedirá la generación de un recibo para cada uno de los pisos y de los locales, con su número de recibo único, la fecha de emisión, la renta, el agua, la luz, la actualización del IPC anual, portería, IVA y otros conceptos, teniendo en cuenta que unos serán opcionales (solo para algunos recibos) y otros obligatorios (para todos). Para cada recibo se desea saber si está o no cobrado.

La aplicación deberá permitir la generación de recibos idénticos a los del mes anterior (a excepción de la fecha), inicializar los conceptos que se desee a una determinada cantidad, modificar recibos de meses anteriores y presentar los recibos en formato impreso (sin mostrar los conceptos con importe cero).

El secretario debe poder gestionar los movimientos bancarios asociados a cada edificio, piso o local. Un movimiento bancario siempre está asociado a un banco y a una cuenta con su saldo, y puede ser de dos tipos: un **gasto** (asociado a un inmueble, con su tipo: reparaciones, limpieza...) o un **ingreso** (asociado a un piso o local, como los recibos que se cobran a los inquilinos). Basándose en ellos, la aplicación generará los informes que faciliten la declaración de la renta.

Por último, la aplicación proporcionará listados: todos los inquilinos ordenados por fechas, inquilinos que han pagado o no en un intervalo, todos los inmuebles, los pisos y locales de cada edificio, los recibos pendientes de cobro en un intervalo, etc.

**Debes representar los diagramas de casos de uso para los actores: propietario, inquilino y secretario.**

## Herramienta

Dibuja el diagrama en **DIA** (puedes hacer un diagrama por actor o uno único con los tres) y expórtalo como imagen o PDF.

---

## Preguntas de profundización

1. ¿Algún actor comparte casos de uso con otro? Si has usado generalización entre actores, justifícala; si no, explica por qué no hace falta.
2. El enunciado dice que para cualquier operación sobre un inquilino es necesaria la identificación previa. ¿Qué relación has usado para modelarlo: `«include»` o `«extend»`? Justifica con la regla de "siempre vs a veces".
3. Generar el recibo del mes y duplicar el del mes anterior son dos operaciones distintas. ¿Tienen algo en común que justifique alguna relación entre ellas? ¿Cuál?
4. ¿Hay algún caso de uso que solo se ejecute bajo cierta condición? Identifícalo y explica qué relación has usado y hacia dónde apunta la flecha.

---

## 📤 Entregable

Rellena la plantilla y entrégala en **PDF**:

1. Captura del diagrama (o diagramas) hecho en DIA.
2. Respuestas a las cuatro preguntas de profundización.

!!! warning "Corrección oral"
    El profesor puede pedirte que defiendas cualquier include/extend de tu diagrama, o que expliques por qué algo es un caso de uso y no un paso interno. Si no puedes justificarlo, la actividad no se supera.

## ✅ Criterios de corrección

- Los actores están correctamente identificados y diferenciados.
- Los casos de uso son verbos o frases verbales, y ninguno es un paso interno del sistema.
- Las relaciones `«include»` y `«extend»` están bien aplicadas, con la flecha en la dirección correcta.
- El rectángulo del sistema contiene solo los casos de uso; los actores quedan fuera.
