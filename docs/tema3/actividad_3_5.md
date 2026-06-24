# 🧪 Actividad 3.5: Pruebas unitarias con JUnit

!!! info "Objetivo"
    Diseñar e implementar **pruebas unitarias con JUnit 5** sobre un sistema de gestión de calificaciones, aplicando el ciclo TDD:

    - Escribir tests **antes** de implementar la lógica.
    - Cubrir casos **válidos** e **inválidos**.
    - Verificar la implementación ejecutando la batería de tests.

---

## 🔹 Contexto

El instituto necesita una aplicación para calcular la **calificación final** de los alumnos y determinar si pueden presentarse a la recuperación. Se te proporciona la firma de las clases; tú debes implementarlas guiándote por los tests.

!!! info "Proyecto base"
    Puedes descargar el proyecto inicial para la actividad desde aquí:  
    [📦 Descargar proyecto base](recursos/Actividad_3_5_ED.zip){target="_blank" rel="noopener"}

El proyecto incluye:

- La estructura de paquetes lista para trabajar.
- Un ejemplo resuelto (`EjemploTest`) que muestra cómo usar JUnit 5.
- Las firmas de las clases que debes implementar (ver a continuación).

---

## 🔹 Sistema a implementar: `GestorCalificaciones`

La clase `GestorCalificaciones` tiene tres métodos:

```java
public class GestorCalificaciones {

    /**
     * Calcula la nota final ponderada.
     * @param notaExamen  nota del examen final  [0.0 .. 10.0]
     * @param notaPractica nota de prácticas     [0.0 .. 10.0]
     * @param porcentajeExamen porcentaje del examen sobre 100 [0 .. 100]
     * @return nota final redondeada a 1 decimal,
     *         o -1.0 si algún parámetro está fuera de rango
     */
    public double calcularNotaFinal(double notaExamen,
                                    double notaPractica,
                                    int porcentajeExamen) { ... }

    /**
     * Convierte una nota numérica en calificación textual.
     * @param nota valor numérico [0.0 .. 10.0]
     * @return "Suspenso"      si nota < 5.0
     *         "Aprobado"      si 5.0 <= nota < 6.0
     *         "Bien"          si 6.0 <= nota < 7.0
     *         "Notable"       si 7.0 <= nota < 9.0
     *         "Sobresaliente" si nota >= 9.0
     *         "Error"         si nota < 0.0 o nota > 10.0
     */
    public String obtenerCalificacion(double nota) { ... }

    /**
     * Indica si el alumno necesita ir a recuperación.
     * @param nota       nota final del alumno [0.0 .. 10.0]
     * @param faltas     número de faltas de asistencia [0 .. Integer.MAX_VALUE]
     * @param maxFaltas  número máximo de faltas permitido [1 .. Integer.MAX_VALUE]
     * @return true  si nota < 5.0 O faltas > maxFaltas
     *         false si nota >= 5.0 Y faltas <= maxFaltas
     *         lanza IllegalArgumentException si algún parámetro es inválido
     */
    public boolean necesitaRecuperacion(double nota, int faltas, int maxFaltas) { ... }
}
```

---

## 🔹 Tarea 1 – Revisar el ejemplo resuelto

1. Abre el proyecto en **IntelliJ IDEA**.
2. Localiza la clase `EjemploTest` y léela con atención.
3. Identifica:
    - Cómo se declara una clase de test con JUnit 5.
    - Cómo se usan `@Test`, `@BeforeEach` y los métodos `assertEquals`, `assertThrows`.
    - Cómo se nombran los métodos de test de forma descriptiva.

---

## 🔹 Tarea 2 – Tests para `calcularNotaFinal`

Crea la clase `GestorCalificacionesTest` e implementa tests que cubran al menos:

| Caso | `notaExamen` | `notaPractica` | `porcentajeExamen` | Resultado esperado |
|------|-------------|---------------|-------------------|-------------------|
| Cálculo normal (60/40) | 8.0 | 6.0 | 60 | 7.2 |
| Todo examen (100%) | 5.0 | 0.0 | 100 | 5.0 |
| Nota examen fuera de rango | 11.0 | 5.0 | 50 | -1.0 |
| Nota práctica fuera de rango | 5.0 | -1.0 | 50 | -1.0 |
| Porcentaje fuera de rango | 5.0 | 5.0 | 110 | -1.0 |
| Porcentaje = 0 | 8.0 | 4.0 | 0 | 4.0 |

!!! tip "Pista"
    Recuerda que la nota final es: `notaExamen * (porcentajeExamen/100.0) + notaPractica * ((100 - porcentajeExamen)/100.0)`

---

## 🔹 Tarea 3 – Tests para `obtenerCalificacion`

Añade métodos de test que cubran al menos:

| Caso | Entrada | Resultado esperado |
|------|---------|-------------------|
| Límite inferior suspenso | 0.0 | "Suspenso" |
| Centro suspenso | 3.5 | "Suspenso" |
| Límite superior suspenso | 4.9 | "Suspenso" |
| Límite inferior aprobado | 5.0 | "Aprobado" |
| Centro aprobado | 5.5 | "Aprobado" |
| Límite superior aprobado | 5.9 | "Aprobado" |
| Bien | 6.5 | "Bien" |
| Notable | 8.0 | "Notable" |
| Límite inferior sobresaliente | 9.0 | "Sobresaliente" |
| Máximo | 10.0 | "Sobresaliente" |
| Negativo (inválido) | -1.0 | "Error" |
| Mayor que 10 (inválido) | 10.1 | "Error" |

---

## 🔹 Tarea 4 – Tests para `necesitaRecuperacion`

Añade tests que cubran al menos:

| Caso | `nota` | `faltas` | `maxFaltas` | Resultado esperado |
|------|--------|----------|-------------|-------------------|
| Aprobado, sin exceso de faltas | 6.0 | 10 | 20 | false |
| Suspenso, sin exceso de faltas | 4.0 | 5 | 20 | true |
| Aprobado, exceso de faltas | 7.0 | 25 | 20 | true |
| Suspenso y exceso de faltas | 3.0 | 30 | 20 | true |
| Nota exactamente 5.0, faltas OK | 5.0 | 20 | 20 | false |
| Nota exactamente 5.0, faltas en límite+1 | 5.0 | 21 | 20 | true |
| Nota negativa (inválida) | -1.0 | 0 | 10 | `IllegalArgumentException` |
| maxFaltas = 0 (inválido) | 5.0 | 0 | 0 | `IllegalArgumentException` |

---

## 🔹 Tarea 5 – Implementar la lógica

Una vez escritos los tests (aunque fallen), implementa los tres métodos de `GestorCalificaciones` hasta que **todos los tests pasen en verde**.

!!! warning "Orden de trabajo recomendado"
    Sigue el ciclo TDD: **Red → Green → Refactor**.  
    Escribe un test, comprueba que falla, implementa lo mínimo para que pase, y repite.

---

## ✅ Entregable

Sube al Aula Virtual el proyecto en formato **zip** que incluya:

- La clase `GestorCalificaciones` implementada.
- La clase `GestorCalificacionesTest` con todos los tests.
- Captura de pantalla donde se vea que **todos los tests pasan en verde**.
