# 🧩 Actividad 4.4: Git local — tu primer historial de cambios

!!! info "Créditos"
    Actividad basada en el ejercicio original del curso de Joan Puigcerver:  
    [Exercici — Introducció (curs-git)](https://joapuiib.github.io/curs-git/apunts/01_introduccio/exercici/)

---

## 🧠 Qué vas a practicar 

En esta actividad vas a practicar Git **en local** para aprender a:

- crear e inicializar un repositorio,
- añadir archivos y hacer commits,
- realizar cambios y entender qué ocurre,
- consultar el estado del repositorio,
- consultar el historial de cambios,
- configurar lo básico (por ejemplo, ignorar archivos/carpetas).

---

## 🧰 Requisitos previos

1) Tener Git instalado:

```bash
git --version
```

2) Tener configurado tu nombre y email (solo una vez en tu ordenador):

```bash
git config --global user.name "Tu Nombre"
git config --global user.email "tuemail@ejemplo.com"
```

---

## 📌 Norma de la actividad

!!! warning "Obligatorio durante TODO el ejercicio"
    Comprueba el estado del repositorio con:

    - `git status`
    - `git diff`

    **después de cada paso**.  
    El objetivo es que aprendas a interpretar los estados en los que puede estar el repositorio y los archivos.

---

## 🗂️ Recomendación importante

Crea el repositorio en una carpeta **independiente** para evitar problemas con otros ejercicios o repos.

!!! warning "Evita carpetas sincronizadas"
    Si usas OneDrive/Google Drive/iCloud u otros sistemas similares, es recomendable **no** crear el repo dentro de esas carpetas.

---

## 🧪 Ejercicio (pasos)

> En cada paso, recuerda ejecutar **`git status`** y **`git diff`**.

1. Crea un directorio llamado **`bloc1_exercici`** dentro de tu carpeta de trabajo.
2. Inicializa un repositorio de Git en ese directorio.
3. Crea un archivo llamado **`llibres.txt`** y añade **tres libros** que te gusten.
4. Haz un **primer commit**. Elige un **mensaje significativo**.
5. Añade **otro libro** a `llibres.txt`.
6. Haz un **segundo commit**.
7. Crea un archivo llamado **`musica.txt`** y añade **tres canciones** que te gusten.
8. Crea un archivo llamado **`pelicules.txt`** y añade **tres películas** que te gusten.
9. Haz un **tercer commit** que **solo** incluya el archivo `musica.txt`.
10. Crea un archivo llamado **`series.txt`** y añade **tres series** que te gusten.
11. Haz un **cuarto commit** que incluya los archivos `pelicules.txt` y `series.txt`.
12. Modifica `llibres.txt` para **eliminar** uno de los libros.
13. Haz un **quinto commit**.
14. Modifica `pelicules.txt` para **añadir** una película.
15. **Sin modificar el archivo manualmente**, descarta el cambio de `pelicules.txt` mediante una **orden de Git**.
16. Añade un archivo llamado **`{fecha}.log`** con cualquier contenido.  
    - `{fecha}` es la **fecha actual** en formato `YYYYMMDD`.
17. Configura el repositorio para **ignorar** los archivos con extensión **`.log`**.
18. Haz un commit con esa configuración.
19. Crea la carpeta **`tmp`** y copia todos los archivos de texto (`.txt`) dentro de esa carpeta.
20. Configura el repositorio para **ignorar** la carpeta `tmp`.
21. Haz un commit con esa configuración.
22. Comprueba la **historia de cambios** del repositorio.

---

## 📤 Entregable

Entrega un **PDF** que incluya:

- **Capturas de pantalla** de los comandos ejecutados (especialmente `git status` y `git diff` después de cada paso).
- Una **explicación breve** de **qué ha pasado** tras cada paso:  
  
    - qué archivos aparecen como *untracked*, *modified* o *staged*,  
    - qué cambios muestra `git diff`,  
    - y qué se ha guardado (o no) en cada commit.

!!! tip "Consejo"
    Si quieres que quede ordenado, usa un apartado por paso: **Paso X → Captura(s) → Explicación**.
