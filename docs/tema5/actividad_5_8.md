# Actividad 5.8: Del diagrama al código y vuelta

!!! warning "Descarga la plantilla"
    📄 [Plantilla 5.8 — Del diagrama al código y vuelta](plantillas/Actividad_5_8_Plantilla.docx){target="_blank" rel="noopener"}

## Qué vas a practicar

Las dos direcciones del puente entre diagrama y código: generar código Java desde un diagrama de DIA con **dia2code** (*forward engineering*) y obtener el diagrama de un código existente con **IntelliJ IDEA** (*reverse engineering*). Al final comprobarás en qué se parecen y en qué no el diagrama que dibujaste y el que la máquina reconstruye.

## Requisitos previos

- El diagrama `.dia` de la actividad 5.4 (series de televisión) terminado y corregido.
- dia2code instalado y añadido al `PATH` (ver [la teoría](generacion-y-ingenieria-inversa.md)).
- IntelliJ IDEA con soporte de *Diagrams* (Ultimate; tienes licencia educativa gratuita).

---

## Parte A — Generar código con dia2code

**Paso 1.** Abre tu diagrama de la actividad 5.4 en DIA. Ve a **Archivo → Preferencias → Diagrama por defecto** y desmarca **"Comprimir archivos guardados"**. Vuelve a guardar el archivo.

!!! warning "Predicción antes de generar"
    Antes de ejecutar nada, responde por escrito: ¿cuántos ficheros `.java` se van a crear? ¿Qué habrá dentro del cuerpo de los métodos? ¿Cómo crees que se traducirá la multiplicidad `1..*` de las temporadas?

**Paso 2.** Genera el código:

```
dia2code -t java -d src series.dia
```

**Paso 3.** Abre los ficheros generados y compáralos con tu predicción.

**Pregunta A.1.** ¿Ha coincidido tu predicción? Copia el fragmento de código donde se ve cómo ha quedado la relación `Serie`–`Temporada` y explica qué ha hecho la herramienta con la composición y la multiplicidad.

**Pregunta A.2.** Enumera dos cosas que has tenido que decidir tú al dibujar el diagrama y que dia2code **no** ha podido generar. ¿Por qué la herramienta no puede hacer ese trabajo?

---

## Parte B — Ingeniería inversa con IntelliJ

**Paso 4.** Crea un proyecto Java en IntelliJ con un paquete `taller` y pega estas cuatro clases, cada una en su fichero:

```java
package taller;

public abstract class Vehiculo {
    protected String matricula;
    protected int kilometros;

    public abstract double calcularPrecioRevision();
}
```

```java
package taller;

public class Furgoneta extends Vehiculo {
    private double cargaMaxima;

    public double calcularPrecioRevision() {
        return 90 + cargaMaxima * 0.5;
    }
}
```

```java
package taller;

import java.util.ArrayList;
import java.util.List;

public class Taller {
    private String nombre;
    private List<Vehiculo> vehiculos = new ArrayList<>();

    public void admitir(Vehiculo v) {
        vehiculos.add(v);
    }

    public Factura facturar(Vehiculo v) {
        return new Factura(v.calcularPrecioRevision());
    }
}
```

```java
package taller;

public class Factura {
    private double importe;

    public Factura(double importe) {
        this.importe = importe;
    }
}
```

!!! warning "Predicción antes de generar"
    Dibuja a mano (o describe) el diagrama que esperas que genere IntelliJ: qué relación habrá entre `Taller` y `Vehiculo`, entre `Furgoneta` y `Vehiculo`, y entre `Taller` y `Factura`. ¿Aparecerá `Vehiculo` en cursiva?

**Paso 5.** Clic derecho sobre el paquete `taller` → **Diagrams → Show Diagram** (`Ctrl+Alt+Mayús+U`). Activa la vista de atributos y métodos, y exporta el diagrama como imagen.

**Pregunta B.1.** Compara el diagrama generado con tu predicción. ¿Qué relación ha dibujado IntelliJ entre `Taller` y `Factura`? ¿Coincide con lo que la teoría llama dependencia? ¿Por qué?

**Pregunta B.2.** ¿Cómo ha representado IntelliJ que `Vehiculo` es abstracta y que `calcularPrecioRevision` no tiene cuerpo en el padre?

---

## Parte C — Tu propio código

**Paso 6.** Coge una práctica **tuya** del módulo de Programación que tenga al menos 3 clases relacionadas (si no tienes ninguna, pide al profesor un proyecto alternativo). Genera su diagrama por ingeniería inversa con IntelliJ y exporta la imagen.

**Pregunta C.1.** Mirando tu código "desde arriba" por primera vez: ¿hay algo del diseño que ahora te parezca mejorable (una clase que hace demasiado, una relación que no esperabas, atributos duplicados)? Coméntalo en 4-6 líneas. Si crees que está bien, justifica también por qué.

---

## 📤 Entregable

Rellena la plantilla y entrégala en **PDF**:

1. Captura del terminal con la ejecución de dia2code y captura del código generado.
2. Predicciones escritas **antes** de cada generación.
3. Respuestas A.1, A.2, B.1, B.2 y C.1.
4. Diagrama exportado de IntelliJ (Parte B) y el de tu práctica (Parte C).

!!! warning "Corrección oral"
    El profesor puede pedirte que expliques cualquier diferencia entre tu predicción y el resultado real, o cualquier decisión de diseño de tu propio código. Si no puedes explicarlo, la actividad no se supera.

## ✅ Criterios de corrección

- Las predicciones están escritas antes de actuar y las respuestas las comparan honestamente con el resultado.
- Las respuestas explican el *porqué* de lo que hace cada herramienta, no solo el *qué*.
- La Parte C usa código propio y la reflexión es concreta (señala clases y relaciones por su nombre).
