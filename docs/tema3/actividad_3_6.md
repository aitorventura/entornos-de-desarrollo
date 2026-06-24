# 🧪 Actividad 3.6: Tests parametrizados y Mocks

!!! info "Objetivo"
    Aplicar técnicas avanzadas de **pruebas unitarias** con JUnit 5 y Mockito:

    - Crear **tests parametrizados** para probar múltiples datos sin repetir código.
    - Usar **mocks** para aislar componentes y simular dependencias externas.

---

## 🔹 Contexto

Una empresa de alquiler de vehículos necesita un sistema para calcular el **precio del alquiler** y gestionar la **disponibilidad** de su flota. El sistema tiene dos componentes principales:

- `CalculadoraTarifa`: calcula el precio de un alquiler según el tipo de vehículo y los días.
- `GestorAlquiler`: gestiona la lógica de negocio y depende de un repositorio externo (`VehiculoRepository`) para comprobar disponibilidad y obtener datos.

!!! info "Proyecto base"
    Puedes descargar el proyecto inicial para la actividad desde aquí:  
    [📦 Descargar proyecto base](recursos/Actividad_3_6_ED.zip){target="_blank" rel="noopener"}

El proyecto incluye:

- La estructura de paquetes lista.
- Un ejemplo de test parametrizado ya resuelto (`EjemploParametrizadoTest`).
- Un ejemplo de mock ya resuelto (`EjemploMockTest`).
- Las firmas de las clases que debes probar (ver a continuación).

---

## 🔹 Clases del sistema

```java
public class CalculadoraTarifa {

    /**
     * Calcula el precio total del alquiler.
     * @param tipoVehiculo "COCHE", "MOTO", "FURGONETA"
     * @param dias         número de días [1 .. 365]
     * @param seguro       true = incluir seguro (+15% al precio base)
     * @return precio total (double > 0),
     *         o -1.0 si algún parámetro es inválido
     *
     * Tarifas base por día:
     *   COCHE     → 40.00 €
     *   MOTO      → 25.00 €
     *   FURGONETA → 65.00 €
     */
    public double calcularPrecio(String tipoVehiculo, int dias, boolean seguro) { ... }
}
```

```java
public interface VehiculoRepository {
    /** Devuelve true si hay al menos una unidad disponible del tipo indicado. */
    boolean estaDisponible(String tipoVehiculo);

    /** Devuelve el número de kilómetros del vehículo disponible (para aplicar descuento). */
    int getKilometros(String tipoVehiculo);
}
```

```java
public class GestorAlquiler {

    private final CalculadoraTarifa calculadora;
    private final VehiculoRepository repositorio;

    public GestorAlquiler(CalculadoraTarifa calculadora, VehiculoRepository repositorio) { ... }

    /**
     * Procesa una solicitud de alquiler.
     * @param tipoVehiculo tipo de vehículo solicitado
     * @param dias         días de alquiler
     * @param seguro       true si quiere seguro
     * @return precio total si el vehículo está disponible
     * @throws IllegalStateException    si el vehículo no está disponible
     * @throws IllegalArgumentException si los parámetros son inválidos
     *
     * Regla adicional: si el vehículo tiene más de 100.000 km, aplica un 10% de descuento.
     */
    public double procesarAlquiler(String tipoVehiculo, int dias, boolean seguro) { ... }
}
```

---

## 🧩 Actividad 1 — Tests parametrizados para `CalculadoraTarifa`

### ¿Por qué tests parametrizados?

Imagina que tienes que probar `calcularPrecio` con 12 combinaciones distintas. Sin parametrización, escribirías 12 métodos casi idénticos. Con `@ParameterizedTest` y `@CsvSource` defines una tabla de datos y JUnit ejecuta el mismo test con cada fila.

### Qué tienes que hacer

1. Crea la clase `CalculadoraTarifaTest`.
2. Implementa un test parametrizado con `@CsvSource` que cubra **al menos** los siguientes casos:

| `tipoVehiculo` | `dias` | `seguro` | Resultado esperado |
|----------------|--------|----------|--------------------|
| `COCHE`        | 1      | false    | 40.0               |
| `COCHE`        | 1      | true     | 46.0               |
| `COCHE`        | 7      | false    | 280.0              |
| `MOTO`         | 3      | false    | 75.0               |
| `MOTO`         | 3      | true     | 86.25              |
| `FURGONETA`    | 5      | true     | 373.75             |
| `COCHE`        | 0      | false    | -1.0 (inválido)    |
| `COCHE`        | 366    | false    | -1.0 (inválido)    |
| `TAXI`         | 2      | false    | -1.0 (tipo inválido)|
| `null`         | 2      | false    | -1.0 (null)        |

3. Implementa el método `calcularPrecio` en `CalculadoraTarifa` hasta que **todos los tests pasen en verde**.

!!! tip "Estructura de un test parametrizado"
    ```java
    @ParameterizedTest
    @CsvSource({
        "COCHE, 1, false, 40.0",
        "COCHE, 1, true,  46.0"
    })
    void calcularPrecio_devuelveResultadoCorrecto(
            String tipo, int dias, boolean seguro, double esperado) {
        assertEquals(esperado, calculadora.calcularPrecio(tipo, dias, seguro), 0.01);
    }
    ```

---

## 🧩 Actividad 2 — Mocks con Mockito para `GestorAlquiler`

### ¿Por qué mocks?

`GestorAlquiler` depende de `VehiculoRepository`, que en producción accedería a una base de datos. En los tests no queremos base de datos: usamos **Mockito** para crear un doble de `VehiculoRepository` y controlar exactamente qué devuelve en cada escenario.

### Qué tienes que hacer

1. Crea la clase `GestorAlquilerTest`.
2. En el `@BeforeEach`, crea los mocks necesarios con `Mockito.mock(...)`.
3. Implementa los siguientes tests:

| Test | Configuración del mock | Resultado esperado |
|------|------------------------|-------------------|
| Alquiler OK sin descuento | disponible=true, km=50.000 | precio normal |
| Alquiler OK con descuento por km | disponible=true, km=120.000 | precio con -10% |
| Vehículo no disponible | disponible=false | `IllegalStateException` |
| Parámetros inválidos | disponible=true | `IllegalArgumentException` |
| Verifica que se consulta disponibilidad | cualquier caso OK | `verify(repo).estaDisponible(...)` |

!!! tip "Estructura básica con Mockito"
    ```java
    @Test
    void procesarAlquiler_vehiculoNoDisponible_lanzaExcepcion() {
        when(repositorio.estaDisponible("COCHE")).thenReturn(false);

        assertThrows(IllegalStateException.class,
            () -> gestor.procesarAlquiler("COCHE", 2, false));
    }
    ```

4. Implementa el método `procesarAlquiler` en `GestorAlquiler` hasta que **todos los tests pasen**.

---

## 📚 Referencia rápida

| JUnit 5 / Mockito | Para qué sirve |
|-------------------|----------------|
| `@ParameterizedTest` + `@CsvSource` | Ejecutar el mismo test con varios conjuntos de datos |
| `@ValueSource` | Igual, pero con un solo parámetro |
| `Mockito.mock(Clase.class)` | Crear un mock de una clase o interfaz |
| `when(...).thenReturn(...)` | Definir qué devuelve el mock |
| `when(...).thenThrow(...)` | Hacer que el mock lance una excepción |
| `verify(mock).metodo(...)` | Comprobar que se llamó al método del mock |

---

## ✅ Entregable

Sube al Aula Virtual el proyecto en formato **zip** que incluya:

- `CalculadoraTarifa` implementada y `CalculadoraTarifaTest` con tests parametrizados.
- `GestorAlquiler` implementado y `GestorAlquilerTest` con mocks.
- Captura de pantalla donde se vea que **todos los tests pasan en verde**.
