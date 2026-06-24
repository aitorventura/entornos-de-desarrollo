# 🛠️ Herramientas para la elaboración de diagramas

Diseñar diagramas UML, y en particular diagramas de clases, puede hacerse de diversas maneras. Tienes a tu disposición múltiples y potentes opciones, desde bocetos hechos a mano hasta complejas integraciones dentro del IDE.

## 🔷 DIA (herramienta principal del curso)

**DIA** es la herramienta que usaremos en clase para crear los diagramas UML. Es de código abierto, gratuita y ligera.

- Descarga: [dia-installer.de](http://dia-installer.de/download/index.html)
- Manual: [dia-installer.de/doc/en/dia-manual.pdf](http://dia-installer.de/doc/en/dia-manual.pdf)

Tiene paletas específicas para UML, bases de datos y diagramas de flujo. No es tan completa como herramientas profesionales, pero cubre todo lo que necesitamos en el módulo.

!!! warning "Configuración importante"
    Para poder generar código a partir de un archivo DIA, hay que **desactivar la compresión** antes de guardar. Ve a **Archivo → Preferencias → Diagrama por defecto** y desmarca la casilla **"Comprimir archivos guardados"**. Sin esto, dia2code no puede leer el archivo.

    <figure markdown="span">
      ![Preferencias de DIA con la casilla Comprimir archivos guardados desmarcada](img/dia-preferencias-compresion.png)
      <figcaption>Archivo → Preferencias → Diagrama por defecto: desmarcar "Comprimir archivos guardados"</figcaption>
    </figure>

---

## ✍️ Herramientas Visuales (Drag & Drop)

Estas aplicaciones ofrecen paletas de componentes UML pre-dibujados que se pueden arrastrar al lienzo para que traces las líneas interactivamente, lo cual es estupendo para diseños expresivos en colaboración.

1. **Draw.io (Diagrams.net)**:
    - **Uso**: Directamente en el navegador WEB o con la app de escritorio (es libre).
    - **Ventajas**: Gratuito, se integra bien con plataformas de Drive y GitHub. Interfaz familiar e intuitiva.

2. **Lucidchart**:
    - **Uso**: Aplicación web.
    - **Ventajas**: Excelente entorno colaborativo en tiempo real.
    - **Contras**: La versión gratuita está bastante restringida a un par de documentos simultáneamente.

3. **StarUML**:
    - **Uso**: Software de escritorio enfocado a la ingeniería de software y compatibilidad UML 2.
    - **Ventajas**: Permite la ingeniería inversa y forward preinstaladas (o a través de extensiones), de las pocas opciones completas para UML estricto.

## 💻 Herramientas de "Diagramación como Código"

Esta es la forma preferida de documentar en arquitecturas modernas y Git (precisamente al ser archivo de texto y admitir "diffs"):

1. **Mermaid**:
    - **Uso**: Funciona usando simples sentencias de Markdown (es decir, el diseño se renderiza donde haya intérprete).
    - **Ventajas**: Está nativo en GitHub y lo venimos usando a través de los apuntes para la generación de gráficas visuales.

    ```markdown
    <!-- Ejemplo texto simple para generar una gráfica en Markdown -->
    ```mermaid
    classDiagram
      ClaseA -- ClaseB
    ```

2. **PlantUML**:
    - **Uso**: El pionero e indispensable para arquitecturas de código en formato de texto.
    - **Ventajas**: Mucho más completo que Mermaid (aunque la curva de aprendizaje inicial es un poco más cuesta arriba) con enorme soporte de plugins en los IDE.

## 🔌 Plugins de Entornos de Desarrollo

Puedes integrar diagramas de clases dentro de tus proyectos y que se auto-mantengan al tocar código real agregando diferentes "Extensiones" (NetBeans) o "Plugins" (IntelliJ, Eclipse, VS Code). 

Por ejemplo, con IntelliJ IDEA (versión Ultimate y con algunos plugins de la Community) puedes hacer **"click derecho > Diagrams > Show Diagram"** desde cualquier base de código Java y que te lo trace solo.
