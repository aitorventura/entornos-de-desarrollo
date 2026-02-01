<a id="documentacion"></a>

# 📝 4. Documentación de código: comentarios y Javadoc

![Documentación de código](diapositivas/documentacion.pdf){ type=application/pdf style="width:100%;min-height:80vh" }

!!!info "Descarga de diapositivas"
    [Descarga las diapositivas](diapositivas/documentacion.pdf){target="_blank" rel="noopener"}

---

## 🎯 Idea clave

La documentación sirve para que otra persona (o tú dentro de 2 meses) pueda entender:

- **qué hace** el código,
- **cómo se usa**,
- y **por qué** se tomaron ciertas decisiones.

En Java, la documentación suele combinar:

- **comentarios** (breves, puntuales)
- y **Javadoc** (documentación estándar de clases y métodos)

---

## 🧠 ¿Por qué documentar?

<div class="grid cards" markdown>
-   :material-account-multiple: **Trabajo en equipo**
    - Facilita que otros entiendan tu código rápido

-   :material-timer-outline: **Ahorra tiempo**
    - Menos dudas y menos “¿esto por qué está así?”

-   :material-bug-check-outline: **Evita errores**
    - Decisiones y reglas quedan claras

-   :material-book-open-variant: **Aprendizaje**
    - Explica reglas de negocio y casos borde
</div>

---

## ✍️ 4.1 Comentarios: cuándo sí y cuándo no

### ✅ Comentarios que aportan valor

- Explican el **por qué** (decisión, regla, restricción).
- Aclaran un caso especial (*edge case*).
- Avisan de una dependencia o requisito.

```java
// Aplicamos IVA reducido por normativa (productos básicos)
double totalConIVA = total * IVA_REDUCIDO;
```

```java
// Si el usuario está bloqueado, no permitimos login aunque la contraseña sea correcta
if (user.isBlocked()) return LoginResult.BLOCKED;
```

---

### ❌ Comentarios que sobran (dicen lo obvio)

```java
// Incrementa i
i++;
```

```java
// Devuelve el total
return total;
```

!!! tip "Regla práctica"
    Si el comentario solo repite lo que el código ya dice, mejor mejora el nombre del método/variable.

---

## 📚 4.2 Javadoc: qué es, para qué sirve y etiquetas más usadas

**Javadoc** es el formato estándar de Java para documentar **clases** y **métodos**.  
Su ventaja es que, si el proyecto lo configura, se puede **generar documentación HTML** automáticamente a partir del código.

Se escribe con `/** ... */` y dentro se combinan:

- una **descripción** (frases cortas),
- y **etiquetas** (tags) con información estructurada.

---

### 🏷️ Etiquetas (tags) más habituales

#### En clases
- `@author` → autor/a o responsable
- `@version` → versión de la clase o del componente
- `@since` → desde qué versión existe (útil cuando el proyecto evoluciona)

#### En métodos
- `@param` → describe cada parámetro
- `@return` → qué devuelve
- `@throws` → cuándo lanza una excepción (si aplica)
- `@deprecated` → si ya no se recomienda usar (y por qué / alternativa)

!!! tip "Buena práctica"
    No es obligatorio usar todas. Usa las que **aporten información real**.  
    Si `@version` no se usa en tu proyecto, no lo inventes “por decorar”.

---

### 🧱 Javadoc en una clase (ejemplo completo)

```java
/**
 * Servicio de cálculo de precios para pedidos.
 * Aplica reglas simples de descuento y validaciones básicas.
 *
 * <p>Uso típico: se llama desde la capa de servicio/controlador para obtener el total.</p>
 *
 * @author Aitor
 * @version 1.0
 * @since 2026-02
 */
public class PriceService {

    private static final double PREMIUM_FACTOR = 0.90;

    public double calculateTotal(double unitPrice, int units, boolean premium) {
        if (unitPrice < 0 || units < 0) {
            throw new IllegalArgumentException("unitPrice y units deben ser >= 0");
        }
        double total = unitPrice * units;
        return premium ? total * PREMIUM_FACTOR : total;
    }
}
```

!!! info "Qué tiene sentido documentar en una clase"
    - Qué responsabilidad tiene (qué hace y qué no).
    - Reglas importantes si las aplica.
    - Cómo se usa en el proyecto (una frase).

---

### 🧩 Javadoc en un método (ejemplo recomendado)

```java
/**
 * Calcula el precio final de un pedido.
 *
 * @param unitPrice precio por unidad (debe ser >= 0)
 * @param units cantidad de unidades (debe ser >= 0)
 * @param premium indica si se aplica descuento premium
 * @return precio final calculado (nunca negativo)
 * @throws IllegalArgumentException si unitPrice o units son negativos
 */
public static double calculateTotal(double unitPrice, int units, boolean premium) {
    if (unitPrice < 0 || units < 0) {
        throw new IllegalArgumentException("unitPrice y units deben ser >= 0");
    }

    double total = unitPrice * units;
    if (premium) {
        total *= 0.90;
    }
    return total;
}
```

---

### ⚠️ Cuándo NO usar Javadoc (o usarlo mínimo)

- Métodos **privados** muy obvios (mejor nombres claros).
- Código que cambia mucho y la doc se quedará desactualizada.
- Comentarios largos que solo repiten el código.

---

### ✅ Mini-checklist específica para Javadoc

- ¿He explicado **qué hace** el método en una frase?
- ¿He indicado restricciones importantes de entrada (`null`, rangos, formato)?
- ¿He explicado `@return` si no es evidente?
- ¿He puesto `@throws` si realmente puede lanzar una excepción?


## 🌐 4.3 Generar documentación HTML desde Javadoc en IntelliJ

Una de las ventajas de Javadoc es que puedes generar una **web HTML** con la documentación del proyecto (o parte del proyecto) directamente desde IntelliJ.

!!! info "Qué obtienes"
    Una carpeta con archivos `.html` (y recursos) que puedes abrir con el navegador.  
    Normalmente encontrarás un `index.html` como página principal.

---

### ✅ Opción A: Generar Javadoc desde el menú de IntelliJ (la más directa)

1. En IntelliJ, abre tu proyecto.

2. Ve a **Tools → Generate JavaDoc...**

3. En la ventana de configuración, revisa estas opciones típicas:

    - **Output directory**: elige una carpeta de salida (por ejemplo, `docs/javadoc` o `out/javadoc`).

    - **Scope**: selecciona qué parte documentar:

        - *Whole project* (todo el proyecto) o
        - *Module* (un módulo) o
        - *Package* (paquete).

    - **Visibility**:

        - *Public* (recomendado para documentación “limpia”),
        - *Protected* o *Package* (si necesitas más detalle),
        - *Private* (no suele hacer falta).

    - **Open generated documentation in browser** (si aparece): actívalo para que te abra el resultado al terminar.

4. Pulsa **OK / Generate**.
5. Abre la carpeta de salida y localiza `index.html` para verlo en el navegador.

!!! tip "Recomendación para clase"
    Genera solo **public** para que el HTML quede más claro y no se llene de detalles internos.

---

### ⚙️ Problemas típicos y soluciones rápidas

- **Caracteres raros (tildes/ñ)**: En algunas configuraciones, la salida puede depender del encoding. Si ves caracteres mal:
  
    - prueba a regenerar y revisar la configuración del proyecto (UTF‑8),
    - o genera con Maven/Gradle (opciones B/C) donde puedes fijar encoding.

- **Faltan clases o paquetes**: Revisa el **Scope** seleccionado (quizá no estás generando “todo el proyecto”).

- **La salida incluye demasiadas cosas**: Reduce visibilidad (por ejemplo, solo *Public*) o genera solo un módulo/paquete.

---

### ✅ Opción B (alternativa): Generar Javadoc con Maven

Si el proyecto usa Maven, suele existir el objetivo `javadoc:javadoc`.

```bash
mvn javadoc:javadoc
```

Normalmente la salida se genera en una carpeta del tipo `target/site/apidocs/` (depende del proyecto).

---

### ✅ Opción C (alternativa): Generar Javadoc con Gradle

En proyectos Gradle suele existir la tarea `javadoc`:

```bash
./gradlew javadoc
```

La salida suele ir a algo parecido a `build/docs/javadoc/`.

!!! info "Cuándo usar Maven/Gradle"
    - Si el proyecto ya está configurado con build tool.
    - Si quieres que la generación sea reproducible por todo el equipo.
    - Si más adelante lo conectas con integración continua (CI).

---


## 🧠 Cómo escribir buena documentación (sin pasarse)

### ✅ Buenas prácticas

- Documenta lo **público** (clases y métodos públicos).
- Describe **qué hace** y **condiciones** (qué espera y qué devuelve).
- Usa frases simples y directas.
- Mantén la documentación **actualizada** (si cambia el método, cambia la doc).

### ⚠️ Errores típicos

- Poner Javadoc enorme para métodos obvios.
- Documentar cosas que el nombre ya deja claras.
- Copiar/pegar docs y dejarlas incoherentes.
- No indicar restricciones de entrada (`null`, rangos, etc.).

---

## 🗂️ ¿Qué documentar primero en un proyecto?

<div class="grid cards" markdown>
-   :material-file-document-outline: **README (nivel proyecto)**
    - Qué es, cómo ejecutar, cómo probar

-   :material-api: **Puntos de entrada**
    - Métodos/servicios clave, controladores, endpoints

-   :material-alert-circle-outline: **Reglas de negocio**
    - Validaciones, permisos, descuentos, casos especiales

-   :material-wrench-outline: **Decisiones raras**
    - “Esto está así por X motivo”
</div>

---

## ✅ Checklist rápida de documentación

??? tip "Abrir checklist"
    - [ ] ¿El nombre del método ya explica lo básico?
    - [ ] ¿Hay algo que pueda confundir a otra persona? (por qué / reglas / casos borde)
    - [ ] ¿He documentado parámetros y restricciones importantes?
    - [ ] ¿He indicado qué devuelve y en qué casos?
    - [ ] ¿He documentado excepciones si aplica?
    - [ ] ¿La documentación coincide con el código actual?

---

## 🧪 Mini-práctica (no entregable)

1) Elige un método de tu proyecto (o de un ejercicio) que tenga una regla clara (validación, descuento, permisos, etc.).

2) Añade:

- 1–2 comentarios útiles (solo donde aporten valor),
- y un bloque de **Javadoc** para el método.

3) Comprueba que la documentación describe:
    
- parámetros,
- valor devuelto,
- y restricciones o excepciones.

---

