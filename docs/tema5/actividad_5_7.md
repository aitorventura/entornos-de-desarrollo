# Actividad 5.7: Clínica veterinaria

!!! warning "Descarga la plantilla"
    📄 [Plantilla 5.7 — Clínica veterinaria](plantillas/Actividad_5_7_Plantilla.docx){target="_blank" rel="noopener"}

## Qué vas a practicar

El diagrama final del tema: un sistema con una decena de clases, **dos jerarquías de herencia** distintas, agregación, asociaciones muchos-a-muchos y operaciones con parámetros y retorno. Nada que no hayas hecho ya en las actividades anteriores, pero todo a la vez. Aquí el enunciado no te dice qué relación es cada una: esa decisión es tuya.

## Enunciado

Una cadena de clínicas veterinarias quiere informatizar su gestión y te pide el diagrama de clases del sistema.

De cada **clínica** se guarda un identificador, su nombre y su dirección, y debe poder registrarse en el sistema. La clínica mantiene el registro de sus **clientes** (una clínica atiende a uno o más clientes, y cada cliente pertenece a una única clínica). De cada cliente interesa su identificador, su nombre completo, su DNI y su teléfono, y también debe poder registrarse.

En las clínicas trabaja personal contratado. De todo **trabajador** se guarda su identificador de empleado, su nombre, su DNI y su teléfono, y el sistema permite registrarlo. Hay tres perfiles: los **veterinarios**, de los que interesa además su especialidad; los **auxiliares**, con su licencia sanitaria; y los **administrativos**, con su nivel de acceso al sistema.

Cada cliente es dueño de una o varias mascotas. De cada **animal** se registra su nombre, su especie, su raza, su fecha de nacimiento y su peso; el sistema permite registrar un animal y consultar sus datos a partir de su identificador. Cada animal pertenece a un único dueño.

La actividad diaria gira en torno a las **consultas**. Cada consulta tiene una fecha y hora, un diagnóstico y unas observaciones. Una consulta la realiza exactamente un veterinario a exactamente un animal; un veterinario realiza muchas consultas a lo largo del tiempo, y un animal puede acumular muchas consultas. El sistema debe permitir programar una consulta (indicando el animal, el veterinario y la fecha) y registrar el diagnóstico.

Cada animal tiene exactamente una **ficha médica**, desde la que se puede generar un informe. La ficha médica reúne los **tratamientos** que ha recibido el animal (uno o más); un tratamiento puede consultarse con independencia de la ficha que lo agrupa. De cada tratamiento se guarda su descripción y su fecha de aplicación, y en cada consulta se puede prescribir uno o varios tratamientos (un mismo tratamiento puede estar asociado a varias consultas de seguimiento).

Existen dos tipos de tratamiento: la **medicación**, con su tipo y su dosis en miligramos, que el sistema permite registrar; y la **intervención quirúrgica**, de la que se guarda el nombre del quirófano y la duración en minutos. Las intervenciones se registran en el sistema y se pueden consultar las intervenciones en las que ha participado un auxiliar concreto: en cada intervención participan uno o más auxiliares, y un auxiliar participa en muchas intervenciones.

## Herramienta

Dibuja el diagrama en **DIA** y exporta el resultado como imagen o PDF.

---

## Preguntas de profundización

1. Entre `FichaMedica` y `Tratamiento`, ¿has usado composición o agregación? ¿Qué frase del enunciado lo decide?
2. Hay dos jerarquías de herencia en este sistema. ¿Qué criterio has seguido para decidir qué atributos y operaciones suben a la clase padre en cada una?
3. `programarConsulta` recibe un animal y un veterinario como parámetros. ¿Añade eso alguna relación nueva al diagrama, o ya está cubierta por las asociaciones existentes? Razona con la definición de dependencia en la mano.
4. La relación entre `Consulta` y `Tratamiento` es muchos-a-muchos. ¿Habría hecho falta una clase asociativa? ¿Qué dato tendría que pedir el enunciado para que la respuesta fuera sí?

---

## 📤 Entregable

Rellena la plantilla y entrégala en **PDF**:

1. Captura del diagrama completo hecho en DIA.
2. Respuestas a las cuatro preguntas de profundización.

!!! warning "Corrección oral"
    Con un diagrama de este tamaño, el profesor elegirá dos o tres relaciones al azar y te pedirá que las defiendas. Si no puedes justificarlas, la actividad no se supera.

## ✅ Criterios de corrección

- Aparecen todas las clases del enunciado, con sus atributos tipados y sus operaciones (con parámetros y retorno donde el enunciado lo pide).
- Las dos jerarquías de herencia están bien planteadas, sin atributos repetidos en las hijas.
- La agregación y las asociaciones tienen el rombo o la flecha en el lado correcto.
- Las multiplicidades reflejan todas las restricciones del enunciado.
- Los roles siguen la convención de Java.
