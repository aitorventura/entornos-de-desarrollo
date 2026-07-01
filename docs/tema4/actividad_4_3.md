# 📝 Actividad 4.3: Documentar con Javadoc y generar HTML

!!! warning "Descarga la plantilla"
    📄 [Plantilla 4.3 — Documentar con Javadoc](Actividad_4_3_Plantilla.docx){target="_blank" rel="noopener"}

!!! info "Objetivo"
    Practicar el ciclo completo de documentación en Java:

    - Leer código ajeno y entender qué promete, qué espera y qué **no** valida.
    - Escribir **Javadoc** que refleje fielmente lo que el código hace (sin inventar comportamiento).
    - Generar la **documentación HTML** desde IntelliJ y verificar que tiene sentido.

---

## Contexto

Imagina que llegas a un proyecto heredado y te encuentras esta clase: `UserValidator`. No tiene documentación. Tienes que llamar a `validateUser` desde otro módulo, pero no sabes si puedes pasarle `null`, qué pasa si el email no tiene dominio, o qué significa "contraseña válida" para este sistema.

Ese es exactamente el problema que resuelve Javadoc: que quien usa un método no tenga que leer la implementación para saber cómo usarlo.

---

## Código a documentar

Copia este código en tu proyecto como `UserValidator.java`. **No modifiques la lógica** — solo añades documentación.

```java
public class UserValidator {

    public boolean isValidEmail(String email) {
        if (email == null) return false;
        String e = email.trim();
        return e.contains("@") && !e.startsWith("@") && !e.endsWith("@");
    }

    public boolean isValidPassword(String password) {
        if (password == null) return false;
        return password.length() >= 8;
    }

    public void validateUser(String email, String password) {
        if (!isValidEmail(email)) {
            throw new IllegalArgumentException("Email no válido");
        }
        if (!isValidPassword(password)) {
            throw new IllegalArgumentException("Password no válida");
        }
    }
}
```

---

## Instrucciones

### Paso 1 — Analiza antes de escribir nada

Lee cada método y responde por escrito **antes de abrir IntelliJ**:

- ¿Qué hace exactamente `isValidEmail`? ¿Qué considera válido y qué no?
- ¿Qué hace `isValidPassword`? ¿Qué **no** comprueba aunque podría?
- ¿Qué lanza `validateUser`? ¿Cuándo? ¿Puede recibir `null`?

Esto va en tu entregable como "análisis previo". No se puede hacer bien el Javadoc sin haber respondido esto primero.

### Paso 2 — Detecta el error en este Javadoc

Alguien ha intentado documentar `isValidPassword` y ha cometido un error. Encuéntralo y explica por qué es un problema:

```java
/**
 * Valida que la contraseña sea segura.
 * Comprueba que tenga al menos 8 caracteres, una mayúscula y un número.
 *
 * @param password la contraseña a validar
 * @return true si la contraseña es segura, false si no lo es
 */
public boolean isValidPassword(String password) {
    if (password == null) return false;
    return password.length() >= 8;
}
```

!!! warning "Pista"
    Compara lo que dice el Javadoc con lo que hace el código línea por línea.

### Paso 3 — Escribe el Javadoc correcto

Documenta la clase y sus tres métodos. Para cada uno:

- Usa las etiquetas que **aporten información real** (`@param`, `@return`, `@throws`).
- Indica qué pasa si se pasa `null`.
- Indica qué **no** valida el método aunque parezca que debería.

!!! tip "Regla clave"
    Si el método no valida algo, no lo pongas en el Javadoc como si lo validara — eso es peor que no documentar.

### Paso 4 — Justifica tus etiquetas

Para cada método, rellena esta tabla en tu entregable:

| Método | Etiquetas usadas | Por qué esas y no otras |
|--------|------------------|-------------------------|
| `isValidEmail` | | |
| `isValidPassword` | | |
| `validateUser` | | |

### Paso 5 — Genera el HTML desde IntelliJ

1. Ve a **Tools → Generate JavaDoc...**
2. **Output directory**: crea una carpeta `docs/javadoc` dentro de tu proyecto.
3. **Scope**: *Whole project*.
4. **Visibility**: *Public* (para que el HTML quede limpio).
5. Pulsa **OK** y abre el `index.html` en el navegador.
6. Haz una captura donde se vea la documentación de `UserValidator` (la página de la clase, no solo el índice).

---

## Preguntas de reflexión

Responde por escrito (6–10 líneas en total):

1. `isValidEmail` rechaza tanto `"@algo.com"` como `"a@"`, pero acepta `"a@b"` (sin punto de dominio ni extensión). ¿Has reflejado este comportamiento en tu Javadoc? ¿Cómo lo has descrito?
2. ¿Por qué es importante documentar lo que un método **no** hace, no solo lo que hace? Pon un ejemplo concreto con `isValidPassword`.
3. ¿Qué consecuencia real puede tener que otro desarrollador confíe en el Javadoc incorrecto del Paso 2?

---

## Entregable

Entrega un **PDF** con:

| Qué | Cómo se evalúa |
|-----|---------------|
| Análisis previo (Paso 1) | ¿Has entendido lo que hace y lo que no hace cada método? |
| Error detectado (Paso 2) | ¿Has identificado exactamente qué está mal y por qué es un problema? |
| Código con Javadoc (Paso 3) | ¿El Javadoc refleja fielmente el código sin inventar comportamiento? |
| Tabla de etiquetas (Paso 4) | ¿Puedes justificar por qué has usado cada etiqueta? |
| Captura del HTML (Paso 5) | ¿Se ve la página de `UserValidator` en el navegador? |
| Respuestas a las preguntas | ¿Razonas sobre qué documentar y por qué importa? |

!!! warning "Lo que no vale"
    Un Javadoc que documente cosas que el código no hace. Si escribes `@throws` cuando el método no lanza nada, o describres validaciones que no existen, la actividad no se supera aunque el HTML se genere correctamente.
