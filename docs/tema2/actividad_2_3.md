# 🧪 Actividad 2.3: VSCodium — Extensiones y personalización

## Objetivo

Configurar **VSCodium** como entorno de desarrollo funcional para Java y un segundo lenguaje (Python o JavaScript), instalando y gestionando extensiones, personalizando el editor y creando snippets propios.

!!! info "VSCodium vs. VS Code"
    VS Code y VSCodium comparten el mismo código fuente. La diferencia es que la versión oficial de Microsoft incluye un sistema de rastreo de uso —llamado telemetría— que envía datos a Microsoft sobre cómo usas el editor. VSCodium elimina ese rastreo y usa un catálogo de extensiones alternativo llamado [Open VSX](https://open-vsx.org), aunque la mayoría de extensiones populares están disponibles. Para el día a día, la experiencia es prácticamente idéntica.

---

## Lo que tienes que entregar

Completa la **plantilla** con las capturas y respuestas de cada apartado, expórtala a PDF y súbela al Aula Virtual con el nombre:

```
A2-3_NombreApellido.pdf
```

!!!warning "Descarga la plantilla"
    📄 [Plantilla 2.3 — VSCodium: extensiones y personalización](plantillas/Actividad_2_3_Plantilla.docx){target="_blank" rel="noopener"}

---

## Resumen de tareas

**A — Extensiones para Java**
Instala el **Extension Pack for Java** (o las extensiones individuales que lo componen: Language Support for Java, Debugger for Java, Test Runner for Java, Maven for Java). Crea un proyecto Java sencillo y compílalo.

**B — Más extensiones y gestión**
Instala al menos una extensión adicional de tu elección (*GitLens*, *Prettier*, *ESLint*, un tema de color…). Desinstala una extensión y vuélvela a instalar. Documenta el proceso.

**C — Personalización con `settings.json`**
Abre la configuración en formato JSON (`Ctrl + Shift + P` → *Open User Settings JSON*) y configura:
- Fuente monoespaciada (JetBrains Mono o similar)
- Tamaño de fuente
- Tema de color
- Formato automático al guardar (`editor.formatOnSave: true`)

**D — Snippets de usuario**
Crea un snippet para Java que expanda `sout` en `System.out.println();`. Demuestra su uso en un archivo `.java` con una captura.

**E — Segundo lenguaje**
Instala soporte para **Python** o **JavaScript/Node.js** desde el marketplace. Ejecuta un "Hola mundo" en ese segundo lenguaje directamente desde VSCodium (terminal integrado). Captura la ejecución.

---

## Indicaciones importantes

- Muestra en cada captura que estás en VSCodium (no VS Code): la barra de título o el icono lo diferencia.
- Si alguna extensión no está disponible en Open VSX, puedes instalarla manualmente desde el `.vsix` o cambiar el marketplace. Documenta cómo lo has resuelto.
- **No uses IA para redactar las respuestas.**

---

## Entrega

Sube el archivo al **Aula Virtual**, apartado **Actividad 2.3**.
