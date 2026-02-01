# 📝 Actividad 4.3: Documentar con Javadoc y generar HTML (IntelliJ)

!!! info "Objetivo"
    Practicar el ciclo completo de documentación en Java:

    - Escribir **Javadoc** en una clase y sus métodos (sin inventar información).
    - Generar la **documentación HTML** desde IntelliJ.
    - Entregar evidencias: **código comentado** + **captura del HTML** generado.

---

## 🔹 Contexto

En un equipo de desarrollo, es habitual documentar clases y métodos para que:

- se entienda rápido **cómo usar** un método,
- queden claras **restricciones** y **valores devueltos**,
- y se pueda generar una **web de documentación** automáticamente.

---

## ✅ Trabajo a realizar

### 1) Añadir Javadoc al código proporcionado
Debes documentar:

- La **clase** (qué representa y qué responsabilidad tiene).
- Los **métodos públicos**:
  
    - `@param` (parámetros),
    - `@return` (si aplica),
    - `@throws` (si aplica),
    - y, si procede, `@since` / `@version` / `@author`.

!!! tip "Regla práctica"
    Documenta lo que el método **promete** y lo que **espera**.  
    Si el método no valida algo, no lo pongas como si lo validara.

---

### 2) Generar el HTML con IntelliJ
1. IntelliJ → **Tools → Generate JavaDoc...**
2. Elige una carpeta de salida (por ejemplo `docs/javadoc`).
3. Selecciona visibilidad **Public**.
4. Genera y abre el `index.html` en el navegador.

---

### 3) Entregar evidencias
Debes entregar:

- El **código final** con Javadoc (archivo `.java` o copiado en un PDF).
- Una **captura** donde se vea el `index.html` generado (o la página principal de Javadoc en el navegador).

---

## 🧩 Código a documentar (no modificar la lógica)

Copia este código en tu proyecto como `UserValidator.java`.

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

!!! warning "Importante"
    En esta actividad **no se refactoriza** ni se cambia la lógica del código.  
    Solo se documenta con Javadoc y se genera la web HTML.

---

## ✅ Entregable

Entrega un **PDF** con:

1. El código final con Javadoc (o adjunta el `.java`).
2. Una captura del `index.html` (o de la clase `UserValidator` dentro de la documentación HTML).

