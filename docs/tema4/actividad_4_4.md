# Actividad 4.4: Análisis estático con IntelliJ y SonarLint

!!! info "Objetivo"
    Usar las herramientas de análisis estático del IDE para revisar el código de forma sistemática:

    - Ejecutar las **inspecciones de IntelliJ** sobre el código refactorizado de la Actividad 4.2.
    - Interpretar los avisos: entender qué detectan y decidir qué hacer con cada uno.
    - Comparar los resultados con **SonarLint** (si lo tienes instalado).

---

## Contexto

Cuando refactorizas código, es fácil centrarse en lo que ves a simple vista. Los analizadores estáticos hacen algo diferente: aplican cientos de reglas automáticamente sobre el código completo y señalan patrones que, aunque no rompen el programa ahora mismo, suelen convertirse en problemas más adelante.

Esta actividad te pide que uses las herramientas que ya tiene IntelliJ para obtener ese informe y que decidas, aviso por aviso, qué hacer.

---

## Trabajo a realizar

### 1) Preparación

Abre en IntelliJ el proyecto con el código refactorizado de la **Actividad 4.2** (los dos códigos: `TriangleCalculator` y `WeatherAnalyzer`, ya refactorizados).

---

### 2) Ejecutar inspecciones con IntelliJ

En IntelliJ, ve a:

**Analyze → Inspect Code**

- Elige el ámbito: selecciona el módulo o el proyecto completo.
- Deja la configuración de perfiles por defecto (Default).
- Haz clic en **OK** y espera a que termine el análisis.

Se abrirá un panel con los problemas encontrados, agrupados por categorías (por ejemplo: *Probable bugs*, *Code style*, *Performance*, etc.).

!!! tip "Cómo navegar el informe"
    Despliega cada categoría para ver los avisos. Haz clic en un aviso para que IntelliJ te lleve directamente a la línea de código correspondiente.

---

### 3) Documentar los avisos encontrados

En tu entregable, recoge **al menos 3 avisos** del informe. Para cada uno indica:

| Campo | Qué poner |
|---|---|
| **Categoría** | La sección del informe donde aparece (ej: *Probable bugs*, *Code style*) |
| **Descripción** | Qué dice el aviso (puedes copiar el texto del panel) |
| **Archivo y línea** | Dónde se encuentra en el código |
| **Decisión** | ¿Lo has corregido? ¿Por qué sí o por qué no? |

!!! warning "Importante"
    No se espera que corrijas todos los avisos. Lo importante es que entiendas qué detecta cada uno y que justifiques tu decisión.

---

### 4) Ejercicio con SonarLint (si lo tienes instalado)

Si tienes el plugin **SonarLint** activo en IntelliJ, abre el mismo archivo que tiene más avisos en las inspecciones y mira el panel de SonarLint (parte inferior del IDE).

Compara los resultados con los de IntelliJ Inspect Code:

- ¿Coinciden los avisos? ¿SonarLint detecta algo que IntelliJ no señaló, o al revés?
- ¿Las explicaciones de SonarLint son más o menos detalladas?

Describe brevemente la comparación (4–6 líneas).

!!! info "Si no tienes SonarLint"
    Puedes saltarte este apartado. Si quieres instalarlo, búscalo en **File → Settings → Plugins → Marketplace → SonarLint**.

---

## Pregunta de reflexión

Responde por escrito (6–10 líneas):

¿Qué tipo de problemas ha detectado el analizador que tú no habrías visto leyendo el código a simple vista? ¿Hay algún aviso que te haya sorprendido? ¿Crees que un analizador estático puede sustituir a una revisión manual del código, o son complementarios?

---

## Entregable

Entrega un **PDF** con:

1. **Captura del panel de resultados** de IntelliJ Inspect Code (la pantalla con el informe completo).
2. **Tabla con al menos 3 avisos** (categoría, descripción, archivo/línea, decisión tomada).
3. **Comparación con SonarLint** (si lo tienes instalado): 4–6 líneas.
4. **Respuesta a la pregunta de reflexión**: 6–10 líneas.
