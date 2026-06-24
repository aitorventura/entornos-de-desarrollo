# ⚙️ Generación automática de código

Una de las grandes ventajas de UML es su proximidad con el código fuente en lenguajes orientados a objetos. Esta conexión bidireccional entre el diagrama visual y el texto del código permite que ambos se retroalimenten.

La **Generación de Código** (también conocida como *Forward Engineering* o Ingeniería directa) es el proceso mediante el cual se crea automáticamente el código fuente a partir de un diagrama de clases estructurado en una herramienta UML.

## 🚀 Ventajas de la Generación de Código

1. **Ahorro de Tiempo**: Generar la estructura de decenas de clases con sus atributos y cabeceras de métodos vacíos puede ahorrar horas de copia y pega, reduciendo así la posibilidad de cometer "Typos".
2. **Sincronización de Diseño**: Asegura que el código inicial coincida exactamente con las directrices pautadas durante la etapa de diseño de arquitectura y análisis del sistema (los cimientos son idénticos al plano).
3. **Plantillas a Medida**: Numerosas herramientas avanzadas admiten scripts donde si deseas que todos los atributos generen un *Getter* y *Setter*, lo harán masivamente.

## 👨‍💻 ¿Qué genera exactamente?

La mayoría de las herramientas (como StarUML o plugins de NetBeans/IntelliJ) generarán **el esqueleto** u armazón del programa, incluyendo:

- Las definiciones y declaraciones de las `Clases` (incluyendo su paquete).
- Las herencias e implementaciones de `Interfaces`.
- La declaración de los `Atributos` (variables globales) respetando su tipo de datos y modificadores de visibilidad (`private`, `public`, etc).
- La cabecera o firma de los `Métodos`, pero por regla general **vacíos** en su interior. La lógica "algorítmica" del bloque *body* te corresponderá a ti programarla.

```java
// Ejemplo de Java generado automáticamente a partir de una clase UML "Coche"
public class Coche extends Vehiculo {

    private String marca;
    private String modelo;

    public void acelerar() {
        // Todo: Implement logic here
    }
}
```

---

## 🔷 Generación de código desde DIA con dia2code

Para generar código Java directamente desde un archivo `.dia`, se usa la herramienta **dia2code**.

1. Descarga desde [dia2code.sourceforge.net](https://dia2code.sourceforge.net/)
2. Añade el directorio `bin` de instalación a la variable de entorno `PATH`
3. Ejecuta el comando:

```
dia2code -t java -d directorio_salida archivo.dia
```

| Parámetro | Significado |
|---|---|
| `-t java` | Lenguaje de destino |
| `-d directorio_salida` | Dónde se crearán los ficheros `.java` |
| `archivo.dia` | El diagrama fuente |

!!! warning "Importante: desactivar la compresión en DIA"
    dia2code necesita que el archivo `.dia` **no esté comprimido**. 
    
    Ve a **Archivo → Preferencias → Diagrama por defecto** y **desmarca** la casilla **"Comprimir archivos guardados"**. Si no lo haces, dia2code no podrá leer el archivo.

    <figure markdown="span">
      ![Preferencias de DIA con la casilla Comprimir archivos guardados desmarcada](img/dia-preferencias-compresion.png)
      <figcaption>Archivo → Preferencias → Diagrama por defecto: desmarcar "Comprimir archivos guardados" para que dia2code pueda leer el .dia</figcaption>
    </figure>
