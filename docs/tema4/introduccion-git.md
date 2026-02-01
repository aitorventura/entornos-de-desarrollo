<a id="intro-git"></a>

# 🧩 Introducción a Git (local): control de versiones desde cero

![Introducción a Git](diapositivas/intro-git.pdf){ type=application/pdf style="width:100%;min-height:80vh" }

!!!info "Descarga de diapositivas"
    [Descarga las diapositivas](diapositivas/intro-git.pdf){target="_blank" rel="noopener"}

---

## 🧠 ¿Qué es Git?

**Git** es un **sistema de control de versiones**.

Eso significa que Git sirve para:

- llevar el **historial** de un proyecto (qué cambios se han hecho),
- saber **cuándo** se hicieron y **quién** los hizo,
- y poder **volver atrás** si algo se rompe.

!!! tip "Metáfora: máquina del tiempo"
    Git es como una máquina del tiempo para tu proyecto: puedes guardar “puntos” y viajar a versiones anteriores.

---

## 🧯 ¿Por qué necesitamos control de versiones?

Sin Git, cuando programamos suele pasar esto:

- “Antes funcionaba… ¿qué he tocado?”
- “Voy a guardar una copia por si acaso” → `final.zip`, `final_final.zip`, `ahora_si.zip`
- “He mezclado cambios de varias cosas y ya no sé separar lo que hice”
- “He borrado algo importante sin querer”

Git resuelve todo eso porque crea un historial **ordenado** y **recuperable**.

---

## 🕹️ Qué es un commit (y por qué es tan importante)

Un **commit** es un **punto de guardado** del proyecto.

### Metáfora: “guardar partida”
Como en un videojuego:

- estás jugando (programando),
- llegas a un punto estable,
- guardas la partida → haces un **commit**,
- si luego la lías, vuelves a esa partida.

### ¿Qué lleva un commit?
- una “foto” del estado de los archivos,
- el **autor** (tu nombre/email),
- la **fecha**,
- y un **mensaje**.

!!! tip "Mensajes de commit"
    Un mensaje debe decir **qué** has hecho y **para qué**.  
    Ejemplos buenos:

    - “Añade lista inicial de libros”
    - “Corrige cálculo del total con descuento”
    - “Añade validación de email en registro”

---

## 🧺 La idea que más cuesta: *staging* (la bandeja)

Cuando trabajas con Git, no guardas cambios “a lo bruto”. Git te obliga (para bien) a pasar por un paso intermedio antes del commit: el **staging**.

Piensa que Git no funciona como un “guardar” de Word. Funciona más como:

1) **trabajo y ensayo** (cambio cosas),

2) **selecciono lo que quiero guardar como versión**,

3) **guardo esa versión** con un mensaje.

Ese paso 2 es el *staging*.

---

### 🧠 ¿Qué es exactamente el *staging*?

El **staging area** (también llamado **index**) es una especie de **lista de cambios seleccionados** que van a entrar en el **próximo commit**.

- Todo lo que está en *staging* = “esto sí lo voy a guardar ahora”.
- Todo lo que NO está en *staging* = “esto todavía no”.

> El commit no guarda “lo que tengas en la carpeta”, guarda **lo que hayas puesto en staging**.

---

### 🧾 Metáfora: escritorio, bandeja y álbum

- **Escritorio** (*working directory*): donde editas, pruebas y rompes cosas.
- **Bandeja** (*staging area*): donde colocas lo que ya está listo para quedar “registrado”.
- **Álbum** (*historial*): donde quedan guardadas las versiones (commits).

```mermaid
flowchart LR
  W["Escritorio<br/>(editas archivos)"] -->|git add| S["Bandeja<br/>(staging)"]
  S -->|git commit| H["Álbum<br/>(historial)"]
```

!!! tip "Traducción a comandos"
    - `git add` = “pon esto en la bandeja”
    - `git commit` = “pega lo de la bandeja en el álbum”

---

### 🤔 ¿Por qué existe la bandeja?

Porque en la vida real **los cambios se mezclan**.

Imagina que, mientras arreglas una cosa, también tocas otras:

- arreglas un bug en `Pedido.java`,
- cambias un texto del `README.md`,
- retocas un CSS porque lo ves feo.

Si haces un commit con TODO mezclado, el historial se vuelve difícil de usar:

- no se entiende qué se hizo,
- si un día quieres deshacer “solo el bug”, arrastras lo demás,
- y revisar cambios en equipo se vuelve un lío.

Con staging puedes separar el trabajo en commits con sentido:

> “Ahora guardo el bug. Después guardo el README. Después el CSS.”

---

### ✅ Ejemplo práctico: commits limpios (uno por idea)

Supón que has tocado 3 archivos:

- `Pedido.java` (bug)
- `README.md` (texto)
- `styles.css` (estilo)

#### ❌ Lo típico que NO interesa
```bash
git add .
git commit -m "Cambios"
```

Este commit es un “batiburrillo”: mezcla cosas y luego cuesta entenderlo o deshacerlo.

!!! warning "git add ."
    `git add .` añade al área de staging TODOS los documentos nuevos o modificados desde el último commit.

#### ✅ Lo recomendable con staging

**1) Guardas solo el bug**
```bash
git add Pedido.java
git commit -m "Corrige bug en cálculo de pedido"
```

**2) Guardas el README**
```bash
git add README.md
git commit -m "Actualiza instrucciones del proyecto"
```

**3) Guardas el CSS**
```bash
git add styles.css
git commit -m "Mejora estilos del layout"
```

!!! tip "Qué ganas con esto"
    - Historial claro (se entiende de un vistazo).
    - Más fácil deshacer cambios “por partes”.
    - Revisiones más rápidas y seguras.

---

### 🔍 ¿Cómo sé qué está en la bandeja y qué no?

Usa `git status`.

- **Changes to be committed** → está en staging (bandeja).
- **Changes not staged for commit** → está modificado, pero fuera de staging (escritorio).

```bash
git status
```

!!! warning "Regla de oro"
    Antes de commitear, mira `git status` para comprobar qué vas a guardar.

---

### 🎯 Idea final para que se te quede

**Staging = elegir.**

Git te da un botón mental de:

- “esto sí entra en el próximo commit”
- “esto todavía no”

Y esa es la razón por la que Git ayuda a trabajar **ordenado** incluso cuando tú vas tocando cosas sobre la marcha.


---

## 🧩 Estados de un archivo (lo que te cuenta `git status`)

Los archivos en Git suelen estar en estos estados:

- **Untracked**: Git ve el archivo, pero aún no lo sigue (es nuevo).
- **Modified**: lo has cambiado desde el último commit.
- **Staged**: lo has puesto en la bandeja para el próximo commit.
- **Committed**: ya está guardado en el historial.

```mermaid
flowchart LR
  U[Untracked] -->|git add| S[Staged]
  M[Modified] -->|git add| S
  S -->|git commit| C[Committed]
  C -->|editar| M
```

!!! example "Ejemplo rápido"
    - Creas `hola.txt` → **untracked**
    - `git add hola.txt` → **staged**
    - `git commit ...` → **committed**
    - Editas `hola.txt` → **modified**

---

## 🧰 Instalación de Git (si no lo tienes)

Antes de hacer nada, necesitamos que el comando `git` exista en tu ordenador.

### 1) Comprobar si ya está instalado

Abre una terminal y ejecuta:

```bash
git --version
```

- ✅ Si te devuelve algo tipo `git version 2.4x.x`, **ya lo tienes**.
- ❌ Si sale un error tipo “command not found”, “no se reconoce…”, etc., **hay que instalarlo**.

!!! tip "¿Qué significa la versión?"
    No necesitas la última. Si te funciona `git --version`, para clase te vale.

---

### 🪟 Windows 

La opción más sencilla es **Git for Windows** (incluye **Git Bash**).

Instala **Git for Windows** desde aquí:  
[Git for Windows (instalación oficial)](https://git-scm.com/install/windows)

**Qué instalar y qué te aporta**

- Instalas Git.
- Te aparece **Git Bash**, una terminal “tipo Linux” que va genial para empezar.

**Después de instalar**

1. Abre **Git Bash** (mejor que PowerShell al principio).
2. Comprueba:

```bash
git --version
```

**Si en PowerShell no funciona**

A veces Git está instalado, pero la terminal no lo encuentra por el PATH. La prueba rápida:

- Si en Git Bash funciona y en PowerShell no, para el curso usa Git Bash.
- Si quieres arreglarlo, revisa el instalador y asegúrate de seleccionar que Git se añada al PATH.

!!! warning "Carpetas sincronizadas"
    Evita crear repositorios dentro de OneDrive/Google Drive/iCloud: pueden aparecer cambios “fantasma” al cambiar de versión.

---

### 🍎 macOS

En macOS, a menudo Git viene “a medio instalar”.

Prueba:

```bash
git --version
```

- Si macOS te pide instalar **Command Line Tools**, acepta.  
- Cuando termine, vuelve a ejecutar `git --version`.

---

### 🐧 Linux (Debian/Ubuntu)

```bash
sudo apt update
sudo apt install git
git --version
```

---

## ⚙️ Configuración básica (una vez)

Git guarda en cada commit quién lo hizo. Para eso necesita tu nombre y email.

### 👤 1) Nombre y email (global)

```bash
git config --global user.name "Tu Nombre"
git config --global user.email "tuemail@ejemplo.com"
```

Comprueba la configuración:

```bash
git config --global --list
```

!!! warning "Muy típico"
    Si Git te dice “Please tell me who you are…”, es que falta `user.name` o `user.email`.

---

### 🌿 2) Rama por defecto: `main`

Hoy lo más común es usar `main` como rama principal (en vez de `master`).

```bash
git config --global init.defaultBranch main
```

Esto afecta a repos nuevos que crees a partir de ahora.

---

### 🧾 3) Editor por defecto (opcional, recomendado)

A veces Git necesita que escribas un mensaje (por ejemplo, en operaciones que verás más adelante).  
Para que no se abra un editor raro, puedes fijar uno. Con VS Code:

```bash
git config --global core.editor "code --wait"
```

---

## 🧱 Crear un repositorio: `git init` (con captura)

Para que Git empiece a guardar el historial de un proyecto, primero necesitas un **repositorio**: una carpeta “con Git activado”.

### ✅ Paso 1) Entra en la carpeta del proyecto
```bash
cd ~/Documents/pruebas_git
```

### ✅ Paso 2) Inicializa Git
```bash
git init
```

![](capturas/git-init.png)

**Qué estás viendo en la captura**

- Git confirma que ha creado un repositorio vacío en la carpeta `.git/`.
- A continuación se ejecuta `git status` y aparece:

    - `On branch main` → estás en la rama `main`.
    - `No commits yet` → todavía no has hecho ningún commit.
    - `nothing to commit (create/copy files and use "git add" to track)` → aún no hay archivos preparados para guardar.

!!! info "¿Qué es `.git`?"
    Es la “memoria” del repositorio: ahí Git guarda historial, ramas y metadatos.

!!! warning
    - No borres ni edites `.git` a mano.
    - Si eliminas `.git`, el proyecto pierde el historial (aunque los archivos sigan).

---

## 🧭 Los comandos esenciales 

La idea no es memorizar, sino **entender** qué hace cada comando y qué deberías ver en pantalla.

---

### 1) `git status` — el “¿qué está pasando?”

`git status` te dice **en qué situación está tu repo** y **en qué estado están tus archivos**.

```bash
git status
```

![](capturas/git-status.png)

**Qué estás viendo en la captura**

- Se ejecuta `ls` y aparecen 3 archivos: `adios.txt`, `hasta-luego.txt`, `hola.txt`.
- Luego, `git status` muestra dos bloques importantes:

1) **Changes to be committed** (en staging / bandeja)  

   - `new file: adios.txt` → `adios.txt` está preparado para el próximo commit.

2) **Untracked files** (Git los ve, pero todavía NO los sigue)  

   - `hasta-luego.txt` aparece como untracked: existe en la carpeta, pero **aún no lo has añadido** con `git add`.

!!! tip "Regla de oro"
    Antes de hacer `git add` o `git commit`, mira `git status` para confirmar **qué vas a guardar**.

---

### 2) `git diff` — el “¿qué ha cambiado exactamente?”

`git diff` muestra cambios **línea a línea** respecto al último commit (o respecto al staging, según el caso).

```bash
git diff
```

![](capturas/git-diff.png)

**Qué estás viendo en la captura**

- Git te enseña el archivo que cambió: `hola.txt`.
- La línea que empieza por `+` es lo nuevo que has añadido, por ejemplo:

    - `+esta linea es nueva, no estaba cuando he hecho el commit antes.`

!!! tip "¿Por qué usar diff?"
    - Para revisar cambios antes de guardarlos.
    - Para comprobar que no has tocado algo “sin querer”.

---

### 3) `git add` — “pongo esto en la bandeja (staging)”

`git add` no guarda nada todavía: solo **prepara** archivos para el próximo commit.

Ejemplo (lo típico en tu caso):
```bash
git add adios.txt hola.txt
```

![](capturas/git-add.png)

**Qué estás viendo en la captura (después del add)**

- En **Changes to be committed** aparecen:

    - `new file: adios.txt` → `adios.txt` está en staging.
    - `modified: hola.txt` → los cambios de `hola.txt` también están en staging.

- En **Untracked files** sigue apareciendo:
    - `hasta-luego.txt` → sigue sin estar “bajo control” porque no lo has añadido.

!!! warning "Ojo con `git add .`"
    `git add .` mete en staging **todo** lo nuevo/modificado.  
    Al principio, es mejor añadir **archivo a archivo** para no llevarte cosas sin querer.

---

### 4) `git commit` — “guardo la partida”

`git commit` guarda en el historial **lo que esté en staging**.

```bash
git commit -m "Añado los archivos hola y adios"
```

![](capturas/git-commit.png)

**Qué estás viendo en la captura**

- Git confirma el commit:
  
    - aparece el id (hash corto) del commit, y el mensaje.
    - `2 files changed...` y `create mode ... adios.txt` → creó `adios.txt` en el historial.
    
- Luego se ejecuta `git status` y ocurre algo clave:
  
    - `hasta-luego.txt` sigue en **Untracked files** → no se ha guardado porque **no estaba en staging**.

!!! tip "Idea clave"
    Un commit guarda **solo** lo que tú has puesto en staging con `git add`.

---

### 5) `git log` — “muéstrame el historial”

Para ver los commits que has hecho:

```bash
git log
```

![](capturas/git-log.png)

**Qué estás viendo en la captura**

- Aparecen los commits en orden (más reciente arriba).

- `HEAD -> main` indica:

    - estás en la rama `main`,
    - y `HEAD` apunta al último commit (el “actual”).

!!! tip "Versión corta (recomendada en clase)"
    ```bash
    git log --oneline
    ```

---

## ♻️ “Me he equivocado”: descartar cambios (`git restore`)


### A) Descartar cambios de un archivo (volver al último commit)

Si modificas `hola.txt` y no quieres esos cambios:

```bash
git restore hola.txt
```

![](capturas/git-restore.png)

**Qué estás viendo en la captura**

1) Primero se ejecuta `git diff` y se ven varias líneas nuevas (`+...`) en `hola.txt`.

2) Luego se ejecuta `git restore hola.txt`.

3) Al volver a ejecutar `git diff`, **no sale nada** → significa que el archivo ha vuelto al estado del último commit.

!!! danger
    `git restore` borra cambios **no guardados** en commits.  
    Si esos cambios te importan, guarda antes (commit) o copia el archivo.

---

### B) Quitar un archivo del staging (sin borrar sus cambios): `git restore --staged`

Esto sirve cuando has hecho `git add` por error (lo metiste en staging), pero aún no has hecho commit.

![](capturas/git-restore-staged.png)

**Qué estás viendo en la captura**

1) `git add hasta-luego.txt` → lo mete en staging.  

2) `git status` muestra:

- `new file: hasta-luego.txt` en **Changes to be committed**.

3) `git restore --staged hasta-luego.txt` → lo saca del staging.

4) `git status` vuelve a mostrarlo como **Untracked files**.

!!! tip "Truco mental"
    - `restore --staged` = “saca de la bandeja”
    - `restore` (sin `--staged`) = “deshaz cambios del archivo”

---

## 🚫 `.gitignore`: cosas que NO queremos guardar en el historial

Esto no aparece en tus capturas, pero conviene dejarlo claro aquí porque lo usarás en el ejercicio.

- Ignorar logs:
```gitignore
*.log
```

- Ignorar carpeta `tmp` en la raíz del repo:
```gitignore
/tmp/
```

!!! tip
    `.gitignore` solo afecta “a partir de ahora”.  
    Si un archivo ya está commiteado, seguirá en el historial.

---

## ✅ Ideas clave (muy resumidas)

??? tip "Abrir resumen"
    - `git init` crea un repositorio local (aparece `.git/`).
    - `git status` te dice qué está en staging, qué está modificado y qué es untracked.
    - `git diff` te enseña exactamente qué cambió.
    - `git add` mete archivos en staging (bandeja).
    - `git commit` guarda solo lo que esté en staging.
    - `git log` muestra la historia de commits.
    - `git restore` deshace cambios; `git restore --staged` saca del staging sin borrar cambios.
