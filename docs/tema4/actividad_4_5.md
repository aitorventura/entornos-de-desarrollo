# 🧩 Actividad 4.5: Ramas en Git — Gestión avanzada de versiones

!!! info "Créditos"
    Actividad basada en el ejercicio original del curso de Joan Puigcerver:  
    [Exercici — Branques (curs-git)](https://joapuiib.github.io/curs-git/apunts/02_branques/exercici/)

!!! warning "Antes de empezar"
    Te recomendamos encarecidamente que **leas la actividad entera** de principio a fin, y te asegures de revisar el apartado **📤 Entregable** al final del documento. Así sabrás exactamente qué debes registrar o capturar antes de ponerte a escribir comandos en la terminal.

---

## 🧠 Qué vas a practicar 

En esta actividad profundizarás en el uso de ramas en Git, cubriendo desde lo básico hasta operaciones complejas. El objetivo no es solo ejecutar comandos, sino entender la **topología** del historial de Git.

Practicarás:

- **Creación y fusión** de ramas (Merge).
- Gestión de **ramas divergentes**.
- **Resolución de conflictos** en fusiones.
- **Eliminación** de ramas.

---

## 🧰 Requisitos previos

1.  **Alias Gráfico**: Asegúrate de tener configurado el alias `git lga` para ver el historial gráficamente. Es esencial para entender este ejercicio.
    ```bash
    git config --global alias.lga "log --graph --oneline --all --decorate"
    ```
2.  **Entorno Limpio**: Crea el repositorio en una carpeta limpia para evitar mezclarlo con ejercicios anteriores.

---

## 🧪 Ejercicio (pasos)

!!! warning "Importante: Tu herramienta principal"
    Después de **CADA** paso, es obligatorio que ejecutes:
    
    1. `git status`: Para ver en qué rama estás y si hay cambios pendientes.
    2. `git lga`: Para visualizar el dibujo (grafo) de las ramas. **¡Fíjate bien en dónde apunta cada rama!**

---

### Parte 1: Inicialización

Preparamos el terreno con una rama principal estable.

1. Crea un directorio llamado `bloc2_exercici` en tu carpeta de trabajo y entra en él.
2. Inicializa un repositorio de Git: `git init`.
3. Crea un archivo llamado `llibres.txt`. Añade dentro **tres libros** que te gusten (uno por línea).
4. Haz un **primer commit** con el mensaje "Añadidos libros iniciales".
5. Si tu rama se llama `master`, renómbrala a `main` para seguir el estándar moderno:
   ```bash
   git branch -m master main
   ```

Check: `git lga` debería mostrar un solo punto (commit) donde está `main` y `HEAD`.

---

### Parte 2: Fusión directa (Fast-Forward)

Vamos a crear una rama, avanzar en ella, y luego integrar los cambios. Como `main` no se moverá mientras tanto, la fusión será lineal.

1. Crea una rama llamada `musica` y sitúate en ella:
   ```bash
   git checkout -b musica
   ```
2. Crea un archivo llamado `musica.txt` y añade **tres canciones** que te gusten.
3. Haz un **commit** en esta rama: `git add .` y `git commit -m "Añadida música"`.
4. Vuelve a la rama `main`: `git checkout main`.
5. Incorpora (fusiona) los cambios de `musica` en `main`:
   ```bash
   git merge musica
   ```
6. **Documenta** con una captura el resultado de `git lga`. Verás que `main` simplemente ha avanzado hasta donde estaba `musica`.

---

### Parte 3: Fusión de ramas divergentes

Ahora simularemos que dos personas trabajan a la vez en cosas distintas, creando historias paralelas que luego uniremos.

1. Estando en `main`, crea dos ramas nuevas: `mes-llibres` y `mes-musica`.
2. Sitúate en la rama `mes-llibres` (`git checkout mes-llibres`):
    - Añade un **nuevo libro** al final de `llibres.txt`.
    - Haz un **commit**.
    - Añade **otro libro más** a `llibres.txt`.
    - Haz **otro commit**.
3. Sitúate en la rama `mes-musica` (`git checkout mes-musica`):
    - Añade una **nueva canción** a `musica.txt`.
    - Haz un **commit**.
    - Añade **otra canción más** a `musica.txt`.
    - Haz **otro commit**.
4. Vuelve a `main`.
5. Incorpora los cambios de `mes-llibres`:
    ```bash
    git merge mes-llibres
    ```
    *(Esta será Fast-Forward porque main no había avanzado).*
6. Incorpora los cambios de `mes-musica`:
    ```bash
    git merge mes-musica
    ```
    *(Aquí Git creará automáticamente un **commit de fusión** porque las historias divergieron).*
    - Se abrirá un editor para el mensaje del commit. Guarda y sal.
7. **Documenta** el estado final con `git lga`. Observa cómo se bifurcan y unen las líneas.

---

### Parte 4: Resolución de conflictos en la fusión

Vamos a provocar que dos ramas toquen **las mismas líneas** del archivo `llibres.txt`.

1. Desde `main`, crea las ramas `llibres-ciencia-ficcio` y `llibres-fantasia`.
2. En la rama `llibres-ciencia-ficcio`:
    - Modifica `llibres.txt` añadiendo un libro de **ciencia ficción** en la primera línea (o en una línea específica que vayas a tocar en la otra rama).
    - Haz un **commit**.
    - Añade **otro libro** del género.
    - Haz **otro commit**.
3. En la rama `llibres-fantasia`:
    - Modifica `llibres.txt` añadiendo un libro de **fantasía** **en la misma línea** que usaste antes.
    - Haz un **commit**.
    - Añade **otro libro** del género.
    - Haz **otro commit**.
4. Vuelve a `main`.
5. Fusiona `llibres-ciencia-ficcio`: `git merge llibres-ciencia-ficcio`.
6. Intenta fusionar `llibres-fantasia`: `git merge llibres-fantasia`.
    - **¡CONFLICTO!** Git te dirá: `CONFLICT (content): Merge conflict in llibres.txt`.
7. **Resolución**:
    - Abre `llibres.txt`. Busca las marcas `<<<<<<<`, `=======`, `>>>>>>>`.
    - Decide cómo quieres que quede el archivo (quizás conservando ambos libros).
    - Borra las marcas de Git.
    - Guarda el archivo.
    - Ejecuta `git add llibres.txt`.
    - Ejecuta `git commit` (sin argumentos) para confirmar la fusión.
8. **Documenta** el estado final con `git lga`.

---

### Parte 5: Eliminación de una rama

Limpieza del repositorio.

1. Desde `main`, crea una rama `series` y otra `pelicules`.
2. En la rama `series`:
    - Crea `series.txt`, añade una serie y haz commit.
    - Añade otra serie y haz commit.
3. Desde `main`:
    - Elimina la rama `pelicules`:
      ```bash
      git branch -d pelicules
      ```
      *(Como no tiene cambios propios, se borra sin rechistar).*
    - Intenta eliminar la rama `series`:
      ```bash
      git branch -d series
      ```
      *(Git te dará un error: `error: The branch 'series' is not fully merged`)*.
4. **Fuerza la eliminación**:
   ```bash
   git branch -D series
   ```
5. **Pregunta**: ¿Qué ha pasado con los commits de la rama `series`? (Piensa: ¿Están accesibles? ¿Están en el historial de `main`?).
6. **Documenta** con captura el error que te dio Git y el estado final.


---

## 📤 Entregable

Sube un único **PDF** con:

1. **Capturas de `git lga`** al finalizar las Partes 2, 3, 4 y 5.
2. **Captura y explicación** breve de cómo resolviste los conflictos (Parte 4).
3. **Respuesta** a la pregunta de la Parte 5 sobre los commits perdidos.
