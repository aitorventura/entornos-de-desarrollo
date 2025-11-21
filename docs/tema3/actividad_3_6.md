# 🧪 Actividad 3.6: Tests parametrizados y Mocks

!!! info "Objetivo"
    Aplicar técnicas avanzadas de **pruebas unitarias** con JUnit y Mockito:
    
    - Crear **tests parametrizados** para reducir duplicación y mejorar claridad.  
    - Utilizar **mocks** para aislar componentes y probar servicios dependientes.

---

## Introducción

En el desarrollo de software, las pruebas unitarias son fundamentales para asegurar que las aplicaciones funcionan correctamente.  

A medida que los sistemas crecen en complejidad, también lo hace la necesidad de pruebas más potentes y flexibles.

En esta actividad trabajaremos con dos técnicas clave:

### Tests parametrizados
- Permiten ejecutar **el mismo método de prueba** varias veces con diferentes datos.  
- Reducen repetición y hacen que los tests sean más claros.
- En JUnit 5 se implementan con:
    - `@ParameterizedTest`
    - Fuentes de datos como `@CsvSource`, `@ValueSource`, etc.

### Mocks
- Los **mocks simulan dependencias externas** dentro de una clase.
- Permiten aislar la unidad de código bajo prueba.
- Mockito es la librería utilizada:
    - Crear mocks.  
    - Definir comportamientos esperados.  
    - Verificar interacciones.

---

## Código base

!!! info "Proyecto base"
    Puedes descargar el proyecto inicial para la actividad desde aquí:  
    [📦 Descargar proyecto base](recursos/Actividad_3_6_ED.zip){target="_blank" rel="noopener"}


Incluye:

  - Clases para pruebas unitarias.
  - Tests de ejemplo.
  - Implementaciones parciales de servicios y clases auxiliares.

---

## 🧩 Actividad 1 — Convertir a tests parametrizados

Modifica los tests de:

  - **Ejemplo2**  
  - **Ejemplo3**  
  - **Enunciado1**

### Debes:

1. Convertir las pruebas unitarias existentes en **tests parametrizados**.
2. Utilizar `@CsvSource` o `@ValueSource` para definir los conjuntos de datos.
3. Cubrir:
    - Clases de equivalencia  
    - Valores límite  
    - Casos inválidos que deben lanzar excepciones  
4. Seguir como referencia el ejemplo ya implementado en **Ejemplo1**.

---

## 🧩 Actividad 2 — Uso de Mocks con Mockito

En el proyecto encontrarás las clases:

- `Calculadora`  
- `CalculadoraService` (con métodos ampliados)

### Debes:

1. Utilizar **Mockito** para simular el comportamiento de la clase `Calculadora`.
2. Probar los nuevos métodos de `CalculadoraService`.
3. Tomar como ejemplo el **primer método ya probado**, que sirve como base.
4. Ampliar la **cobertura de pruebas** creando mocks que:
    - simulen cálculos,  
    - devuelvan valores esperados,  
    - verifiquen interacciones.

---

## 📚 Recuerda

- Revisa los tests ya hechos para entender el estilo y estructura esperada.

---

## ✅ Entregable

Sube al Aula Virtual el proyecto en formato zip que incluya:

- Las clases de **tests parametrizados** para Ejemplo2, Ejemplo3 y Enunciado1.  
- La clase de pruebas con **mocks** para `CalculadoraService`.  
- Asegúrate de que **todas las pruebas pasan en verde**.

