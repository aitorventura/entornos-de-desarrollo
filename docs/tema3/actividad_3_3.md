# 🎯 Actividad 3.3: Pruebas de caja negra (Partición Equivalente y Valores Límite)

!!! info "Objetivo"
    Aplicar técnicas de **pruebas de caja negra** para diseñar casos de prueba efectivos utilizando:
    
    - **Partición Equivalente (PE)**: Agrupar entradas en clases que se comportan de forma similar.  
    - **Análisis de Valores Límite (AVL)**: Probar valores en los bordes de las particiones.

---

## 🔹 Contexto de la actividad

En esta actividad vamos a aplicar las técnicas de **pruebas de caja negra**, centrándonos en:

- **Partición Equivalente**  
  Identificaremos y agruparemos las entradas del sistema en **clases o particiones** que se comportan de manera similar.  
  Reducimos así el número de pruebas seleccionando **un representante por clase**.

- **Análisis de los Valores Límite**  
  Nos fijaremos en los **valores extremos** o cercanos a los límites de las particiones para detectar errores que aparecen en **condiciones críticas**.

El objetivo principal es **diseñar y documentar casos de prueba** que validen el correcto funcionamiento del sistema, cubriendo tanto **escenarios comunes** como **casos extremos**.

---

## 🔹 Recordatorio de directrices

### Partición Equivalente

| Tipo de entrada                          | Nº clases válidas                              | Nº clases inválidas                                           |
|-----------------------------------------|------------------------------------------------|---------------------------------------------------------------|
| Rango de valores (ej. `[20..30]`)       | 1: valor en rango (25)                         | 2: por debajo y por encima del rango (15, 40)                |
| Conjunto finito (ej. `{2,4,6,8}`)       | 1: valor en el conjunto (4)                    | 2: fuera del conjunto, por debajo y por encima (1, 10)       |
| Condición booleana (T/F)                | 1: valor evaluado a cierto (“j”)               | 1: valor evaluado a falso (“?”)                              |
| Conjunto de valores admitidos           | tantas como valores admitidos                  | 1: valor no admitido (p.e. opción4)                          |

---

### Análisis de Valores Límite (AVL)

| Tipo de entrada                          | Nº clases válidas                                                      | Nº clases inválidas                                                    |
|-----------------------------------------|-------------------------------------------------------------------------|-------------------------------------------------------------------------|
| Rango de valores (ej. `[20..30]`)       | 4: límites y adyacentes dentro del rango (20, 21, 29, 30)              | 2: justo por debajo y por encima (19, 31)                             |
| Conjunto finito (ej. `{2,4,6,8}`)       | 4: mínimo, máximo y adyacentes dentro del conjunto (2, 4, 6, 8)        | 2: justo por debajo y por encima del conjunto (1, 9)                  |

---

## 🔹 Tarea general

Para **cada enunciado** deberás realizar **caja negra** siguiendo la estructura trabajada en clase:

1. **Identificar entradas**  
    - Listar todas las entradas del sistema, su **tipo de dato** y restricciones (rango, longitud, conjunto de valores, etc.).

2. **Partición Equivalente (PE)**  
    - Determinar el nº de **clases válidas** e **inválidas** para cada entrada.  
    - Construir una **tabla de clases de equivalencia**.  
    - Diseñar **casos de prueba** que cubran todas las clases (al menos uno por clase válida y uno por cada clase inválida).

3. **Análisis de Valores Límite (AVL)**  
    - Identificar los **límites** de cada entrada que lo permita (rangos, conjuntos).  
    - Construir una tabla con los **valores límite** válidos e inválidos.  
    - Diseñar **casos de prueba adicionales** para cubrir esos valores.

4. **Casos de prueba finales**  
    - Presentar las pruebas en **tablas** con:  
        - Entradas  
        - Clase de equivalencia / tipo de límite  
        - Descripción  
        - Salida esperada

Puedes usar el los ejemplos resueltos como plantilla para realizar los ejercicios.

---

## 🧩 Enunciado 1 – Prima de empleados

Un programa toma como entrada un fichero cuyo formato de registro es:

`(Número-empleado, Nombre-empleado, Meses-Trabajo, Directivo)`

Donde:

- **Número-empleado**: entero positivo de 3 dígitos (excluido `000`).  
- **Nombre-empleado**: alfanumérico (mínimo 1, máximo 10 caracteres).  
- **Meses-Trabajo**: entero positivo de 3 dígitos (incluye `000`).  
- **Directivo**: carácter que puede ser `+` (directivo) o `-` (no directivo).

El programa asigna una **prima** según:

- **P1**: directivos con al menos **12 meses** de antigüedad.  
- **P2**: no directivos con al menos **12 meses** de antigüedad.  
- **P3**: directivos con menos de 12 meses.  
- **P4**: no directivos con menos de 12 meses.

### Trabajo a realizar (Enunciado 1)

Para este enunciado debes:

1. Identificar las **entradas** y sus **tipos**.  
2. Calcular el nº de **clases válidas e inválidas** para cada entrada (PE).  
3. Construir la **tabla de clases de equivalencia** (incluyendo identificadores de clase).  
4. Diseñar **casos de prueba** usando **Partición Equivalente**:  
    - Asegúrate de cubrir todas las categorías de prima (P1, P2, P3, P4).  
5. Diseñar **casos de prueba adicionales** con **Valores Límite** cuando tenga sentido (ej. meses de trabajo, número-empleado, longitud del nombre).  
6. Presentar todo en tablas claras:  
    - Tabla de clases de equivalencia.  
    - Tabla(s) de casos de prueba (PE y AVL).

---

## 🧳 Enunciado 2 – Tarifa de billetes

Un programa calcula la **tarifa de cada billete** según el trayecto, la antelación y la edad del pasajero. La empresa sólo opera viajes entre **Santander, Madrid y Barcelona**.

Datos de entrada:

- **CiudadOrigen**: `"SNT"`, `"MAD"`, `"BCN"`.  
- **CiudadDestino**: `"SNT"`, `"MAD"`, `"BCN"`.  
- **Fecha**: tipo fecha (día del viaje).  
- **Edad**: número entero positivo de 3 cifras (incluyendo `000`).

Descuentos (no acumulables, se aplica el MAYOR):

- **Antelación**:  
    - 15% si se compra con **> 1 semana** de antelación.  
    - 25% si se compra con **> 1 mes** de antelación.

- **Edad**:  
    - 30% si **edad < 25** años.  
    - 40% si **edad > 65** años.

> **NOTA simplificada para esta actividad**  
> Para hacer el ejercicio más asequible, **solo tomarás como límites** los que aparecen en los **datos de entrada** (por ejemplo, límites del campo Edad, códigos de ciudad, etc.), no los de fechas, semanas y meses.

### Trabajo a realizar (Enunciado 2)

Para este enunciado debes:

1. Identificar las **entradas** y sus **restricciones** (valores posibles, formato, etc.).  
2. Determinar **clases de equivalencia válidas e inválidas** para cada entrada:  
    - Ejemplo: ciudades válidas / ciudad no válida.  
3. Elaborar la **tabla de clases de equivalencia**.  
4. Diseñar **casos de prueba** que cubran:  
    - Trayectos válidos e inválidos.  
    - Edades en diferentes rangos relevantes (niños/jóvenes, adultos, mayores…).  
    - Situaciones sin descuento / con cada tipo de descuento.  
5. Diseñar **casos de prueba usando AVL** solo sobre los límites de los datos de entrada que tenga sentido aplicar.  
6. Presentar las pruebas en **tablas**, indicando también el **descuento esperado** (0%, 15%, 25%, 30%, 40%).

---

## ✅ Entregable

Un **PDF** que contenga, para **cada enunciado (1 y 2)**:

- Identificación de entradas y tipos.  
- Tabla(s) de **clases de equivalencia** (PE).  
- Tabla(s) de **valores límite** (AVL), cuando proceda.  
- Tabla(s) de **casos de prueba** con: entradas, clase, tipo de técnica (PE/AVL) y salida esperada.  

