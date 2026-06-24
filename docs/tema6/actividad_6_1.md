# Actividad 6.1: Gestión de fincas e inmuebles

## Objetivo

Que el alumno sea capaz de identificar actores y casos de uso a partir de una descripción real de un sistema, y de representar las relaciones entre ellos usando include, extend y generalización cuando corresponda.

## Enunciado

Crea el diagrama de casos de uso de una aplicación de gestión de fincas e inmuebles con el siguiente funcionamiento:

La empresa gestora actúa como propietaria. Los inmuebles pueden ser pisos, locales o edificios (que a su vez contienen pisos y locales). La aplicación debe permitir:

- Dar de alta, modificar, dar de baja y consultar inmuebles y sus pisos/locales.
- Cualquier persona con nómina, aval bancario o contrato puede alquilar un inmueble disponible. Para cualquier operación sobre un inquilino es necesaria su identificación previa.
- Dar de alta, modificar, dar de baja y consultar inquilinos.
- El secretario puede generar recibos mensuales para cada piso o local, duplicar recibos del mes anterior e inicializar conceptos. Los recibos tienen conceptos obligatorios y opcionales.
- El secretario gestiona movimientos bancarios (gastos e ingresos) asociados a los inmuebles y genera informes para la declaración de la renta.
- La aplicación proporciona listados: inquilinos ordenados por fechas, recibos pendientes, etc.

**Los actores del sistema son: propietario, inquilino y secretario.**

## Lo que debes entregar

- Un diagrama de casos de uso para cada actor (o uno único con todos si lo prefieres).
- Respuestas a las preguntas de profundización.

## Preguntas de profundización

1. ¿Cuántos actores distintos has identificado? ¿Alguno de ellos comparte casos de uso con otro?
2. El enunciado dice que para cualquier operación sobre un inquilino es necesaria la identificación. ¿Qué relación UML usarías para modelar esto: `«include»` o `«extend»`? Justifica.
3. Generar el recibo del mes actual y duplicar el del mes anterior son dos operaciones distintas. ¿Tienen algo en común que justifique alguna relación entre ellas?
4. ¿Hay algún caso de uso que solo se ejecute bajo cierta condición? Identifícalo y explica qué relación usarías.

## Criterios de evaluación

- Los actores están correctamente identificados y diferenciados.
- Los casos de uso son verbos o frases verbales (no sustantivos).
- Las relaciones `«include»` y `«extend»` están bien aplicadas y justificadas.
- El rectángulo del sistema contiene solo los casos de uso, no los actores.
