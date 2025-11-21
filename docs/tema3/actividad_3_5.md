# 🧪 Actividad 3.5: Pruebas unitarias con JUnit

!!! info "Objetivo"
    Diseñar y ejecutar **pruebas unitarias con JUnit** a partir de los **casos de prueba de caja negra** definidos previamente, para:

    - Verificar que cada **método** funciona correctamente de forma **aislada**.  
    - Tradificar casos de prueba en **tests automatizados**.  
    - Implementar la lógica de los métodos guiándote por las **pruebas** (enfoque TDD).  
    - Asegurar que la implementación cumple las **especificaciones**.

---

## 🔹 Contexto

Las **pruebas unitarias** permiten comprobar que cada unidad funcional del código (normalmente un método) se comporta como se espera.  
En esta actividad trabajarás con **JUnit** sobre un proyecto Java proporcionado a continuación:

!!! info "Proyecto base"
    Puedes descargar el proyecto inicial para la actividad desde aquí:  
    [📦 Descargar proyecto base](recursos/Actividad_3_5_ED.zip){target="_blank" rel="noopener"}



El proyecto base incluye:

- La lógica y tests de los ejercicios **Ejemplo1** y **Ejemplo2** ya resueltos.  
- Esto te servirá como **modelo** para crear nuevos tests y métodos.

A partir de los **casos de prueba de caja negra** definidos en actividades anteriores (Ejemplo3 y Enunciado1), deberás crear **tests unitarios** y la **implementación** de los métodos correspondientes.

---

## 🔹 Tarea 1: Revisar el proyecto base

1. Descarga y abre en IntelliJ el proyecto.  
2. Revisa:
    - La estructura del proyecto (paquetes, clases, carpeta `test`).  
    - Las clases y tests ya resueltos de **Ejemplo1** y **Ejemplo2**.  
3. Identifica:
    - Cómo se nombran las clases de prueba.  
    - Cómo se usan las **anotaciones de JUnit** y los **asserts**.  

---

## 🔹 Tarea 2: Pruebas unitarias para `Ejemplo3`

### Clase y método a implementar

```java
public class Ejemplo3 {
    public int calcula(int numero, int numero2, char operador) {
        // TODO: implementar
    }
}
```

### Qué tienes que hacer

1. **Identificar los casos de prueba**  
   Usa los casos de prueba ya definidos en la actividad de **caja negra** para `Ejemplo3` (la solución de la actividad está en Aules).

2. **Crear la clase de test y los métodos de prueba**  
    - Crea la clase de prueba correspondiente (por ejemplo, `Ejemplo3Test`).  
    - Añade métodos de test en JUnit que cubran:
        - Todos los casos **válidos**.  
        - Todos los casos **inválidos** (deben producir “error”).

3. **Implementar la lógica del método `calcula`**  
    - Validar parámetros.  
    - Realizar la operación adecuada (`+`, `-`, `/`, `*`).  
    - Gestionar casos inválidos según los tests.

4. **Ejecutar y depurar los tests**  
    - Ejecuta la batería completa de tests.  
    - Ajusta la lógica o los tests si alguno falla.

---

## 🔹 Tarea 3: Pruebas unitarias para `Enunciado1`

### Clase y método a implementar

```java
public class Enunciado1 {
    public String asignaPrima(int numEmpleado, String nombreEmpleado, int mesesTrabajo, char directivo) {
        // TODO: implementar
    }
}
```

### Qué tienes que hacer

1. **Identificar los casos de prueba**  
   Usa los casos de prueba de **Enunciado1** previamente definidos (Solución en Aules).

2. **Crear la clase de test**  
    - Crea `Enunciado1Test`.  
    - Implementa pruebas para:
        - Casos válidos: P1, P2, P3, P4.  
        - Casos inválidos: deben devolver “error”.

3. **Implementar la lógica del método**  
    - Validar todos los parámetros.  
    - Devolver la prima correspondiente.  
    - Gestionar errores.

4. **Ejecutar y depurar los tests**  
    - Comprueba que todas las pruebas pasen en verde.  
    - Ajusta la lógica si es necesario.

---

## 📚 Recursos de apoyo

!!! info "Casos de prueba de caja negra"
    Los casos de prueba detallados para `Ejemplo3` y `Enunciado1` están disponibles en los documentos de **Ejemplos de caja negra** en la sección de teoría y en la solución de la actividad **Actividad 3.3 – Caja negra** respectivamente.

---

## ✅ Entregable

Tu entrega deberá incluir:

- Implementación de las clases **`Ejemplo3`** y **`Enunciado1`**.  
- Clases de test JUnit con todos los casos de prueba implementados.  
- Todas las pruebas ejecutándose correctamente.  
- Entrega según formato indicado en Aula Virtual.
