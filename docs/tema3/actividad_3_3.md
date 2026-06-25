# 🎯 Actividad 3.3: Pruebas de caja negra

!!! warning "Descarga la plantilla"
    📄 [Plantilla 3.3 — Pruebas de caja negra](plantillas/Actividad_3_3_Plantilla.docx){target="_blank" rel="noopener"}

!!! info "Objetivo"
    Aplicar **Partición Equivalente (PE)** y **Análisis de Valores Límite (AVL)** para diseñar casos de prueba de caja negra sobre dos sistemas reales.

---

## 🔹 Resumen de las técnicas

### Partición Equivalente (PE)

La idea es simple: si el sistema trata igual a todos los valores de un grupo, basta con probar uno de ese grupo.
Se dividen las entradas en **clases válidas** (lo que el sistema acepta) e **inválidas** (lo que debe rechazar), y se diseña un caso de prueba por clase.

| Tipo de entrada | Clases válidas | Clases inválidas |
|---|---|---|
| Rango `[20..30]` | 1 (ej. 25) | 2: uno por debajo, otro por encima |
| Conjunto `{A, B, C}` | tantas como elementos (una por valor) | 1 (cualquier valor fuera del conjunto) |
| Longitud `[1..10]` | 1 (ej. 5 caracteres) | 2: longitud 0 y longitud 11 |
| Booleano / binario | 2 (verdadero / falso) | — |

### Análisis de Valores Límite (AVL)

Complementa la PE probando los **valores extremos** de cada rango o conjunto, porque ahí es donde suelen esconderse los errores.

| Tipo de entrada | Clases válidas (4) | Clases inválidas (2) |
|---|---|---|
| Rango `[20..30]` | 20, 21, 29, 30 | 19, 31 |
| Longitud `[1..10]` | 1, 2, 9, 10 caracteres | 0, 11 caracteres |

Para conjuntos de valores discretos, se toma el primer elemento, el último y, si hay, el del medio.

---

## 🔹 Estructura de la respuesta (para cada enunciado)

Debes completar cuatro secciones:

1. **Identificación de entradas**: nombre, tipo de dato y restricciones de cada campo.
2. **Tabla PE**: clases válidas e inválidas numeradas (ej. `(1)`, `(2)`...).
3. **Casos de prueba PE**: un caso por clase válida y uno por cada clase inválida.
4. **Tabla AVL + casos de prueba AVL**: límites de los campos que lo permitan.

Los casos de prueba van en tabla con columnas: entrada completa, clases que cubre, salida esperada.

---

## 🧩 Enunciado 1 — Prima de empleados

Un programa lee registros del formato:

```
(Número-empleado, Nombre-empleado, Meses-Trabajo, Directivo)
```

Con las siguientes restricciones:

| Campo | Tipo | Restricciones |
|---|---|---|
| Número-empleado | Entero | 3 dígitos, rango `[001..999]` (excluido `000`) |
| Nombre-empleado | Texto | Entre 1 y 10 caracteres alfanuméricos |
| Meses-Trabajo | Entero | 3 dígitos, rango `[000..999]` |
| Directivo | Carácter | Solo `+` (directivo) o `-` (no directivo) |

El programa asigna una prima según la combinación de los dos últimos campos:

| Directivo | Meses ≥ 12 | Meses < 12 |
|---|---|---|
| `+` (directivo) | **P1** | **P3** |
| `-` (no directivo) | **P2** | **P4** |

### Lo que debes entregar (Enunciado 1)

1. Tabla de clases de equivalencia PE (identifica cuántas clases válidas e inválidas tiene cada campo y nómbralas con un número entre paréntesis).
2. Casos de prueba PE: asegúrate de cubrir las cuatro primas (P1, P2, P3, P4) y todos los casos de error.
3. Tabla AVL con los valores límite de `Número-empleado`, `Meses-Trabajo` y `Nombre-empleado`.
4. Casos de prueba AVL.

!!! tip "Pista: el campo Directivo"
    El campo `Directivo` es un **conjunto de dos valores admitidos**, no un rango.
    Según las reglas de PE, eso genera **2 clases válidas** (una para `+` y otra para `-`) y **1 clase inválida** (cualquier otro carácter).

!!! tip "Pista: las cuatro primas"
    Para cubrir P1, P2, P3 y P4 necesitas probar las cuatro combinaciones de (directivo/no directivo) × (meses ≥ 12 / meses < 12).
    Con una entrada se puede cubrir varias clases válidas a la vez.

---

## 🧳 Enunciado 2 — Tarifa de billetes

Una empresa de transporte opera entre **Santander (SNT)**, **Madrid (MAD)** y **Barcelona (BCN)**. Un programa calcula la tarifa según:

| Campo | Tipo | Restricciones |
|---|---|---|
| CiudadOrigen | Texto | `"SNT"`, `"MAD"` o `"BCN"` |
| CiudadDestino | Texto | `"SNT"`, `"MAD"` o `"BCN"` |
| Fecha | Fecha | Día del viaje (debe ser una fecha futura válida) |
| Edad | Entero | 3 dígitos, rango `[000..999]` |

Descuentos (no acumulables, se aplica el mayor):

| Descuento | Condición |
|---|---|
| 15% | Compra con más de 1 semana de antelación |
| 25% | Compra con más de 1 mes de antelación |
| 30% | Edad < 25 años |
| 40% | Edad > 65 años |

!!! note "Simplificación para el AVL"
    Para el AVL **solo analiza los campos con rango numérico o conjunto discreto** (`Edad`, `CiudadOrigen`, `CiudadDestino`).
    No analices los límites de semana/mes de antelación en el campo Fecha.

### Lo que debes entregar (Enunciado 2)

1. Tabla de clases de equivalencia PE.
2. Casos de prueba PE: cubre los distintos descuentos posibles (0%, 15%, 25%, 30%, 40%) y los casos de error.
3. Tabla AVL + casos de prueba AVL para `Edad` y las ciudades.

!!! tip "Pista: las ciudades"
    `CiudadOrigen` y `CiudadDestino` son **conjuntos de tres valores admitidos**: SNT, MAD, BCN.
    Para PE eso son **3 clases válidas** y **1 clase inválida**.
    Para AVL trata los tres valores como si fueran los límites del conjunto (inferior, medio, superior).

!!! tip "Pista: los descuentos"
    Los descuentos dependen de la fecha (cuánta antelación hay) y de la edad.
    Para cubrir los 5 escenarios (sin descuento y cada uno de los cuatro descuentos) necesitarás combinar
    valores de fecha y edad que disparen cada caso. La fecha de referencia para los ejemplos es el **4 de enero de 2025**.

---

## ✅ Entregable

Un **PDF** exportado desde la plantilla, con para **cada enunciado**:

- Tabla de clases de equivalencia (PE)
- Tabla de casos de prueba PE
- Tabla de valores límite (AVL)
- Tabla de casos de prueba AVL
