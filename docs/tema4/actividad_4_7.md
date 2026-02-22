# 🧩 Actividad 4.7: Pull Requests — Contribuyendo a proyectos Open Source

!!! info "Créditos"
    Actividad basada en el ejercicio original del curso de Joan Puigcerver:  
    [Exercici — Col·laboració mitjançant Pull Requests (curs-git)](https://joapuiib.github.io/curs-git/apunts/06_projectes/exercici/)

!!! warning "Antes de empezar"
    Es recomendable que **leas la actividad entera** de principio a fin, y te asegures de revisar el apartado **📤 Entregable** al final del documento. Así sabrás exactamente qué debes evidenciar y capturar de la interfaz web en cada paso.

---

## 🧠 Qué vas a practicar 

En esta actividad abandonarás el trabajo aislado y te convertirás en un auténtico contribuyente Open Source (código abierto) emulando exactamente la forma en la que los desarrolladores profesionales trabajan alrededor del globo cada día.

Practicarás cómo:

- Hacer un **Fork** de un repositorio ajeno donde no tienes permisos.
- Ramificar tu repositorio forkeado y trabajar en local.
- Confeccionar y abrir una **Pull Request (PR)** contra el repositorio originario enviando una contribución oficial de código.
- (Opcional) Comunicarte explorando el panel de Incidencias (*Issues*).

---

## 🧰 Requisitos previos

- **Cuenta de GitHub** plenamente operativa.
- Ninguna carpeta sobrante: al ser un proyecto completamente nuevo clonado desde internet, te recomendamos ponerte en un directorio ordenado donde crear y clonar toda esta nueva práctica.

---

## 🧪 Ejercicio (pasos)

### Parte 1: El Fork

Existe un repositorio compartido y público llamado **Filmoteca**, dedicado a recabar un directorio gigantesco de obras de ocio. Tú no cuentas con permisos directos de escritura/modificación sobre él.

1. Navega a la web principal de dicho repositorio público: [aitorventura/filmoteca](https://github.com/aitorventura/filmoteca).
2. Localiza el botón habilitado para hacer un **Fork** (en la esquina superior derecha) y crea tu propia bifurcación en tu usuario personal intacta.
3. Clona tu Fork, ahora bajo de tu dominio (`https://github.com/TU_USUARIO/filmoteca`), bajándolo mediante terminal a tu ordenador:
   ```bash
   git clone <URL_DE_TU_FORK>
   ```

*(Documenta en las entregas el éxito visual de este primer paso)*.

---

### Parte 2: ¡Hora de contribuir!

Decide qué tipo de obra quieres catalogar entre estas 3 opciones: un **libro**, una **película** o una **série**.  
A continuación, prepara de forma ordenada, siguiendo las buenas costumbres, la adición de tu nueva ficha.

1. Sitúate en terminal en la nueva carpeta del proyecto.
2. Crea de forma disciplinada una **nueva rama aislada** cuyo nombre sugiera qué pretendes introducir allí. Por ejemplo, `pelicula/mad-max`, o `llibre/senyor-anells` para que no contamines el `main`.
3. Adéntrate en la carpeta del género pertinente (el repositorio original ya trae carpetas separadas para libros, películas y series). Crea dentro de esa zona oportuna el fichero con el nombre de tu obra en formato Markdown (`mad-max.md`).
4. **Formato riguroso**: El sistema de PR exige que los archivos subidos mantengan la coherencia con el estilo original elegido del proyecto. Emplea la plantilla adecuada a tu elección y edita los campos entre corchetes rectos `[...]`:

=== "Libro"
    ```markdown
    # [Títol del llibre]
    
    - __Autor__: [Autor del llibre]
    - __Any de publicació__: [Any de publicació]
    
    ## Sinopsi
    [Sinopsi del llibre.]
    
    ## Gèneres
    - [Gènere 1]
    - [Gènere 2]
    - ...
    ```

=== "Película"
    ```markdown
    # [Títol de la pel·lícula]
    
    ## Sinopsi
    [Sinopsi de la pel·lícula.]

    ## Gèneres
    - [Gènere 1]
    - [Gènere 2]
    - ...

    ## Repartiment
    [Directors, actrius i actors principals.]
    ```

=== "Sèrie"
    ```markdown
    # [Títol de la sèrie]
    
    ## Sinopsi
    [Sinopsi de la sèrie.]
    
    ## Gèneres
    - [Gènere 1]
    - [Gènere 2]
    - ...
    
    ## Temporades
    [Nombre de temporades de la sèrie i títol de cada temporada.]
    ```

5\. Consolida esa creación: Haz tu comando `git status` reglamentario, tu correspondiente `add `, y empaquétalo en un `git commit` asertivo.

---

### Parte 3: Elevando la Pull Request

1. Publica hacia internet la rama cargada de cambios que acabas de moldear empleando tu alias hacia el origen de *tu copia*: 
   ```bash
   git push -u origin <tu-rama>
   ```
2. Entra al navegador y recarga la página de tu Fork de la filmoteca. Verás un banner avisándote que tienes ramas recientes y sugiriéndote **"Compare & pull request"**. Púlsalo.
3. El asistente verificará la compatibilidad en verde. **Asegúrate de que tus flechas y repositorios origen/destino dictaminan el viaje adecuado** hacia `aitorventura/filmoteca`.
4. Aporta un **título elegante** y una **descripción clara** expresando tu contribución antes de confirmar el botón verde "Create pull request". 

*(Tras esto, consultaré la PR que me ha llegado, y si todo está correcto, la aceptaré y mergearé).*

---

### (Opcional) Ampliación de Caza-errores

Si quieres subir de nivel, explora la sección de [Issues](https://github.com/aitorventura/filmoteca/issues) del repositorio original. 

Detecta fallos, repórtalos o atrévete a solucionarlos: crea una rama específica para el parche, haz el commit y abre una Pull Request incluyendo el comando `Closes #N` en la descripción. Al fusionarse, la incidencia se cerrará automáticamente, consolidando tu perfil como colaborador experto.


---

## 📤 Entregable

!!! danger "Atención: Autoría de las capturas"
    En todas las capturas de pantalla de navegadores a continuación debe apreciarse siempre la URL, tu avatar, o **tu cuenta de usuario explícitamente logueada** en la interfaz para evidenciar la autoría frente al peligro del Ctrl+C / Ctrl+V de un compañero.  

Sube un único archivo **PDF** documentando gráficamente lo ocurrido a lo largo del encargo:

1. **El Fork verificado:** Captura de la página web de tu clonado personal, donde en la esquina superior izquierda se aprecia a la perfección que el dueño actual del Fork es tu nombre de usuario *(ej. `@EstudianteX/filmoteca forked from aitorventura/filmoteca`)*. (Parte 1).
2. **El Commit subido con sentido aislacionista:** Brevísima captura de la terminal ejecutando orgullosamente el `git push -u ...`, tras el pertinente `git checkout -b` de separación. (Parte 2).
3. **La Oferta Creada (La Pull Request):** Captura del propio panel web final de la Pull Request ya creada (con tu título y descripción adjuntos), denotándose en la ruta y etiquetas gráficas cuáles eran las ramas comparativas. (Parte 3).
4. Una **breve reflexión personal (5-10 líneas)** al final de tu documento que evalúe y opine sobre este sistema. ¿Crees que este método de "Forks" y solicitudes de validación ordenadas frente a abrir el repositorio madre a "que toque código quien quiera libremente" supone salvar la vida de proyectos inmensos, o por el contrario frena los tiempos de agilidad local? Extiéndete.
