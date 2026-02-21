# 🧩 Actividad 4.6: Remotos — Trabajando con GitHub

!!! info "Créditos"
    Actividad basada en el ejercicio original del curso de Joan Puigcerver:  
    [Exercici — Remots (curs-git)](https://joapuiib.github.io/curs-git/apunts/03_remots/exercici/)

!!! warning "Antes de empezar"
    Es recomendable que **leas la actividad entera** de principio a fin, y te asegures de revisar el apartado **📤 Entregable** al final del documento. Así sabrás exactamente qué debes registrar o capturar antes de ponerte a ejecutar comandos.

---

## 🧠 Qué vas a practicar 

En esta actividad pondremos en práctica todo lo aprendido sobre remotos y GitHub. Ya no solo trabajarás en tu ordenador, sino que conectarás tu trabajo con la nube y simularás el trabajo colaborativo clonando tu propio repositorio.

Practicarás:

- Crear repositorios remotos en GitHub y enlazarlos con tu código local.
- Sincronizar repositorios locales y remotos (`push`, `pull`, `fetch`).
- Clonar un repositorio remoto existente en otra carpeta.
- Incorporar cambios mediante fusiones directas y con ramas divergentes.
- Trabajar con ramas tanto en el entorno local como en el remoto.

---

## 🧰 Requisitos previos

- **Cuenta de GitHub**: Necesitas tener creada tu cuenta en [GitHub](https://github.com/) y haber configurado tu acceso (mediante Token PAT o llave SSH, como aprendimos en la teoría).
- **Alias Gráfico**: Sigue utilizando tu alias `git lga` para ver el historial gráficamente.

---

## 🧪 Ejercicio (pasos)

!!! warning "Importante: Tu herramienta principal"
    Comprueba el estado del repositorio con `git status` y `git lga` después de cada orden fundamental para entender por dónde transitan tus archivos y tus ramas.

---

### Parte 1: Creación y Enlace

1. **En GitHub**: Crea un repositorio remoto completamente vacío llamado `bloc3_exercici`. No añadas ningún archivo inicial (ni README, ni LICENSE, ni .gitignore).

2. **En tu ordenador**:

      - Crea un directorio nuevo llamado `bloc3_exercici` en tu carpeta de trabajo.
      - Inicializa un repositorio de Git en ese directorio (`git init`).
      - Crea un archivo `llibres.txt` y añade tres libros que te gusten.
      - Haz un **primer commit**.
      - Asegúrate de que tu rama principal se llama `main` (`git branch -m master main`).

3. **Enlazando mundos**:

      - Configura el repositorio local para añadir el remoto de GitHub llamándolo `origin`.
      - Publica la rama `main` al repositorio remoto.
      - *Comprueba en la web de GitHub que el archivo `llibres.txt` ha subido correctamente.*

---

### Parte 2: Clonación y Preparación

Vamos a simular ser "otra persona" o estar en "otro ordenador" clonando el proyecto en una carpeta paralela.

1. Clona el repositorio remoto que acabas de subir en una nueva carpeta independiente llamada `bloc3_exercici_clone`.
2. Comprueba que dentro de `bloc3_exercici_clone` existe el archivo `llibres.txt`.
3. *Simulación de usuario*: Configura este repositorio clonado para que los commits parezcan hechos por otra persona. Ejecuta dentro de él:
   ```bash
   git config user.name "Brian"
   git config user.email "brian.cohen@edu.gva.es"
   ```

!!! note "A partir de este punto"
    Trabajaremos alternando entre las dos carpetas: el repositorio local original (`bloc3_exercici`) y el clonado (`bloc3_exercici_clone`). Te recomendamos abrir dos terminales a la vez para no hacerte un lío.

---

### Parte 3: Publicación de cambios

Desde el repositorio **clonado** (`bloc3_exercici_clone`):

   - Crea/modifica el archivo `pelicules.txt` añadiendo la película *La vida de Brian*.
   - Realiza un **commit**.
   - Publica (haz `push` de) la rama `main` al repositorio remoto.
   - Comprueba en la web de GitHub que el archivo `pelicules.txt` ha subido correctamente y que el autor es "Brian".

---

### Parte 4: Incorporación con fusión directa

Desde el repositorio **original** (`bloc3_exercici`):

   - Asómate a ver qué hay de nuevo sin alterar tu código usando `git fetch`.
   - Observa el historial de cambios.
   - Incorpora los cambios de la rama `origin/main` a tu rama `main` local (esto es, un `git pull` rápido).

---

### Parte 5: Fusión de ramas divergentes

Vamos a crear historias alternativas.

1. Desde el repositorio **original** (`bloc3_exercici`):

      - Añade una película a `pelicules.txt`.
      - Realiza un **commit**.
      - Publica (`push`) la rama `main` al remoto.

2. Desde el repositorio **clonado** (`bloc3_exercici_clone`):

      - Añade la película *Monty Python and the Holy Grail* a `pelicules.txt`.
      - Realiza un **commit**.
      - **Intenta publicar** (`push`) la rama `main` al remoto. *(Git te dirá que no puedes, piensa y comprende por qué).*
      - Descarga e incorpora los últimos cambios de GitHub (`git pull`).
      - Esto generará un conflicto porque ambas partes modificasteis el mismo archivo a la vez. **Resuélvelo** (quedándote con ambas películas, por ejemplo), consolida el commit de *merge* resultante y ahora sí, publica (`push`) tu rama `main` reparada al remoto.
      - Comprueba que la rama `main` del remoto ha sido actualizada y contiene los cambios actualizados tras el conflicto.

---

### Parte 6: Ramas y Remotos

Cómo gestionar ramas fuera de `main` en GitHub.

Desde el repositorio **original** (`bloc3_exercici`):

   - Pon tu `main` al día bajándolo todo (`git pull`).
   - Crea una nueva rama local llamada `musica` y muévete a ella.
   - Añade una canción a `musica.txt` y realiza un **commit**.
   - Publica esta nueva rama íntegra en el remoto (`git push -u origin musica`).
   - Comprueba en la interfaz de GitHub que ahora existen dos ramas allí (`main` y `musica`).
   - Fija la rama saltando a `main`, fusiona (`merge`) la rama `musica` hacia tu `main`.
   - Publica este `main` definitivo al remoto (`push`).
   - En plan limpieza de fin de proyecto, elimina la rama local `musica` y elimina también la rama remota `musica`.
   - Comprueba que la rama remota `musica` ha sido eliminada entrando en la web de GitHuby consultando las ramas del repositorio remoto.

---

## 📤 Entregable

!!! danger "Atención: Autoría de las capturas"
    En todas las capturas de pantalla debe apreciarse claramente que **eres el autor** (tu cuenta de usuario visible en la web de GitHub, rutas de las carpetas locales, nombre de tu equipo en la terminal, etc.).  
    **En caso de detectar copias, la calificación de la actividad será de un 0 automático.**

Sube un único archivo **PDF** documentando gráficamente lo ocurrido a lo largo del ejercicio:

1. **Capturas de la web de GitHub** que demuestren que la conexión entre tus entornos y la nube ha funcionado:
    - Que el archivo `llibres.txt` se subió a tu repo remoto (Parte 1).
    - Que el archivo `pelicules.txt` se subió correctamente y el autor de ese commit figura explícitamente como "Brian" (Parte 3).
    - Que la rama `main` del remoto contiene una historia integrada con los cambios de ambas partes tras arreglar el conflicto (Parte 5).
    - Que la rama `musica` **existió** en algún momento en GitHub (captura donde se vean las ramas `main` y `musica` disponibles simultáneamente en el desplegable de opciones web) (Mitad de la Parte 6).
    - Que la rama `musica` figura **eliminada** del servidor al final del ejercicio (Final de la Parte 6).
2. **Explica brevemente con tus palabras** cómo solucionaste tú el punto de conflicto de la Parte 5.
3. Asegúrate de incluir **una captura final de consola** donde se vea que has conmutado y trabajado bajo los dos directorios (`bloc3_exercici` y `bloc3_exercici_clone`).
4. Una **breve reflexión personal (5-10 líneas)** sobre la potencia de Git cuando se sincroniza con plataformas como GitHub. ¿Cómo te ayuda esto como programador a la hora de tener un porfolio, de proteger tu código ante desastres locales o colaborar simultáneamente con otros desarrolladores en remoto?
