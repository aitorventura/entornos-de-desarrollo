# 📝 Actividad 5.1: Primer diagrama de clases

En esta actividad pondremos en práctica los conceptos básicos aprendidos a lo largo del Tema 5 diseñando un programa orientado a objetos mediante notación UML para la **Gestión de una Clínica Veterinaria**.

## 🎯 Objetivo

El propósito de la tarea es que logres interpretar un texto o pliego de especificaciones en lenguaje natural, e idealizarlo como un diseño de arquitectura estructural de un diagrama de clases lógico.

---

## 📖 Enunciado

Trabajas en una consultora informática y un cliente os ha contratado para crear el sistema de una clínica veterinaria. A continuación, el analista te ha facilitado los detalles que debes modelar:

1. **La Clínica**: La clínica consta de un `Nombre` y un número de `Telefono` general (ambos textos), y por supuesto de una lista con todos sus `Cliente`. A su vez, la clínica contiene los `Box` (habitaciones de atención). Si se llegase a desmantelar la clínica por completo, las habitaciones también desaparecerían **(Composición)**.
2. **Cliente**: Las personas físicas que visitan la clínica se identifican como `Cliente`. De ellos se necesita guardar su `DNI`, `Nombre` e `Email`. Además de esto, un cliente puede ser dueño de **cero a muchas** `Mascota`, mientras que la mascota está atada a **un único** cliente **(Asociación)**.
3. **Mascota**: El sistema guarda unas entidades básicas para todas las mascotas (`Nombre`, `Fecha de nacimiento` en texto y `Peso` en decimal). El programa cuenta con dos clases derivadas de ella (la Mascota es su padre): los **`Perro`**, que almacenan su campo de `Raza`; y los **`Gato`**, de los que interesa un booleano para conocer si actúan de forma `Agresivo` **(Herencia)**. 
4. **Historial y Consultas**: Cada `Mascota` tiene exactamente un archivo físico en el mostrador del `Historial Médico` (compuesto de su `NumeroExpediente`). El cliente llama y agenda las `Consulta`, de las que se necesita obligatoriamente registrar su `Fecha` (texto), `Motivo` y el importe `Precio`. 

---

## 🛠️ Herramientas a utilizar

Usa la herramienta que más te acomode:
- Aplicaciones web dedicadas (Draw.io o Lucidchart).
- Entornos "texto a diagramas" (Mermaid de Markdown o PlantUML).
- Diseñador visual offline integrado o descargable (StarUML), .

*(Si todo falla, en el mundo real también puedes garabatear el borrador en un folio y tirar una foto al finalizar, pero animamos el empleo de las herramientas de la industria).*

---

## ✅ Criterios de corrección

Para evaluar o validar que tu diseño reúne las especificaciones:
- Todas las clases y entidades listadas en el texto aparecen como bloques.
- Se ha respetado un encapsulamiento conveniente (se valorará los símbolos + y - en los atributos según el patrón estándar de datos ocultos frente a acciones públicas).
- Hay herencia generalizada visible entre los grupos de animales correctos.
- Se divisa la flecha que indica agregación, e incluso un rombo relleno para la Clínica y sus estancias (Box).
- Las líneas que conectan a Clientes y Mascotas tienen números detallando la multiplicidad.

---

## 🚀 Entrega

Cuando lo tengas listo, exporta tu lienzo a una **imagen** (formato `.png` o `.jpg`) o un documento `PDF`. En el caso de valerte de Mermaid o texto, haz entrega tanto del texto original `.md` o `.txt` junto con un pantallazo del código renderizado gráficamente.
Sube el archivo final a la propia plataforma del curso virtual en su apartado correcto antes del cierre de calificación.
