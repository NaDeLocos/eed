# Repositorio
Un **repositorio de Git** es una carpeta dentro de la cual hemos inicializado un repositorio y, por tanto, tiene una carpeta llamada `.git`. Dentro de esa carpet `.git` el programa Git guarda información de todo lo relacionado con el control de versiones.

# Antes de empezar con Git
Para poder usar Git lo tendrás que instalar en tu equipo (se trata de un programa) y ejecutar, desde la terminal, los siguientes comandos para configurar Git y que puedas hacer *commits*.

Para configurar tu nombre (cambia mi nombre por el tuyo):

```bash
$ git config --global user.name "Román Martínez"
```

Para configurar tu e-mail (cambia el mío por el tuyo):

```bash
$ git config --global user.email "rgmf@riseup.net"
```

Para configurar la rama por defecto (no sabemos qué son las ramas todavía, pero ponle el mismo nombre, es decir, "main"):

```bash
$ git config --global init.defaultBranch main
```

Ahora, por último, necesitas configurar el editor de textos que Git usará cuando lo necesites (lo entenderás más adelante). Yo voy a poner aquí "emacs" que es mi editor de textos favoritos, el que yo uso, pero seguramente tú no lo tendrás instalado. Por tanto, busca qué editor de textos tienes instalado, cómo se llama y cambia ese valor de "emacs" por el tuyo.

```bash
$ git config --global core.editor emacs
```

# Inicializar un repositorio de Git
Para inicializar un repositorio de Git, muévete a la carpeta de trabajo, el proyecto, y ejecuta el siguiente comando: `git init`.

A partir de ahora puedes controlar las versiones de los ficheros que hay en el directorio o carpeta de trabajo. Dicho de otro modo, ya puedes usar los comandos de Git.

# Estado del repositorio
Si quieres ver el estado del repositorio (de los ficheros que hay en la carpeta de trabajo) ejecuta el comando `git status`.

Este comando te informará del estado en que se encuentra el repositorio. Estas son las opciones:

- El repositorio de trabajo está **limpio**: no hay cambios.
- Hay ficheros **sin seguimiento**: estos ficheros están el directorio de trabajo pero Git no sabe nada de ellos, no están dentro de Git.
- Hay cambios **no rastreados**: hay cambios (modificaciones o borrados) en los ficheros que se indiquen, lo que significa que estos ficheros están en Git pero han sufrido cambios en el directorio de trabajo.
- Cambios en el **área de preparación o stage**: Son ficheros que has marcado para que se añadan en el siguiente *commit*.

# Añadir cambios al repositorio
Cuando hablamos de cambios en el repositorio nos referimos a cambios en ficheros. Estos cambios en los ficheros pueden ser:

- Nuevos ficheros que no están en Git.
- Ficheros que hemos modificado.
- Ficheros que hemos borrado del directorio de trabajo y que están en Git.

Sea cual sea el escenario del cambio, si los quieres confirmar en Git tienes que llevar a cabo **2 pasos**: un `git add` y un `git commit`.

En el `git add` tienes que indicar los cambios que deseas introducir en el **stage** o **área de preparación**. Por ejemplo, `git add fic1.txt fic2.txt` añadaría al **stage** los cambios en esos dos ficheros. Si quieres añadir todos los ficheros con cambios puedes usar el atajo `git add .` (fíjate en el último punto).

Tras añadir los cambios en el **stage** ya puedes llevar a cabo el segundo paso: `git commit`. Este comando tiene que ir acomapañdo de una descripción, por ejemplo: `git commit -m "Nuevos ficheros añadidos al repositorio"`.

# Ver el historial de commits
Para ver el historial de los cambios o *commits* que has hecho usa el comando `git log`. Este comando tiene un serie de opciones para ver más o menos información. Algunos ejemplos son:

- `git log --graph` para ver el grafo con el camino de los cambios en el repositorio.
- `git log --oneline` para ver los *commits* junto a la descripción, nada más.
- `git log --stat` para ver qué ficheros fueron cambiados y cuántos cambios se han producido.
- `git log -p` para ver los detalles de los cambios en los ficheros.

Otra opción relacionada es la del comando `git shortlog` que muestra la información formateada para poder ser usada en el momento en que quieras crear una nueva versión del software.
