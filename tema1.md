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

# Ver las diferencias entre commits: diff
En Git tenemos el comando `git diff` para ver las diferencias, los cambios, que hay entre *commits* o versiones.

Existen varias posibilidades y opciones. Te resumo algunas:

- `git diff` para ver los cambios antes de realizar el *commit* (cambios actuales).
- `git diff <hash commit a> <hash commit b>` para ver los cambios entre los *commits* indicados (para especificar estos commits se tienen que usar los códigos hash que verás en el `git log`).
- `git diff --name-only <hash commit a> <hash commit b>` para ver solo los nombres de los ficheros que han sufrido cambios entre los dos commits indicados.

# Ignorar ficheros: .gitignore
Podemos indicar a Git qué ficheros queremos que ignore y, por tanto, que no haga un seguimiento de ellos.

Se utiliza un fichero llamado `.gitignore` que se crea en la raíz del proyecto para indicar en él, a través de reglas, qué ficheros queremos ignorar. ¿Por qué? Entre otras cosas:

- Porque contienen información sensible
- Porque son ficheros temporales
- Porque no son relevantes para el proyecto

En este fichero indicamos, por cada línea, qué fichero o ficheros ignorar. Algunos ejemplos:

- `message.log` ignorará el fichero llamado `message.log` que está en la raíz del proyecto.
- `logs/message.log` ignorará el fichero llamado `message.log` que está dentro de la carpeta `logs`.
- `**/message.log` ignorará los ficheros que se llamen `message.log`, estén donde estén.
- `logs/` ignorará todos los ficheros que haya en la carpeta `logs`.
- `*.log` ignorará todos los ficheros que acaben con la extensión `.log`.

# Ramas (branches)
Recuerda configurar tu rama principal con el nombre **main** que es el nombre que se usa como convención hoy en día para la rama principal de trabajo:

```bash
$ git config --global init.defaultBranch main
```

Recordada esta configuración, ya podemos hablar de ramas: las ramas son diferentes líneas de desarrollo en Git. Nos permite trabajar de forma independiente y sin colisionar en proyectos colaborativos.

También es útil usar ramas aunque trabajemos en un proyecto solos/as porque esto nos permitirá trabajar en características nuevas y hacer pruebas sin estropear la línea principal de trabajo.

Aquí te doy la lista de las opciones, lo que puedes hacer con las ramas y el comando `git branch`:

- `git branch` para ver las ramas actuales.
- `git branch <nombre de la rama>` para crear una nueva rama con el nombre indicado.
- `git branch -d <nombre de la rama>` para borrar de forma **segura** un rama ya que no se hará si hay cambios por mezclar.
- `git branch -D <nombre de la rama>` para borrar la rama, se encuentre como se encuentre (¡¡¡CUIDADO!!!).
- `git branch -m <nuevo nombre de la rama>` para cambiar el nombre de la rama actual por el nuevo nombre indicado.
- `git branch -a` para ver las ramas remotas (todavía no hemos entrado al trabajo remoto con Git pero podemos adelantar este comando, para que lo tengas presente).

# HEAD y referencias relativas a commits
El commit sobre el que estamos trabajando tiene un puntero llamado `HEAD`.

Podemos usar el puntero o referencia `HEAD` de Git para identificar *commits*. En vez de usar el hash del *commit* podemos usar el `HEAD`:

- `HEAD` apunta al último commit.
- `HEAD^` apunta al penúltimo commit.
- `HEAD^^` apunta a hace dos commits.
- `HEAD^^^` apunta a hace tres commits... vas entendiendo, ¿verdad?

Si quieres apuntar a muchos commits atrás o, si lo prefires, puedes usar esta otra alternativa:

- `HEAD~1` apunta la penúltimo commit.
- `HEAD~2` apunta a hace dos commits.
- `HEAD~10` apunta a hace diez commits.

Sabiendo esto, podemos comprar los últimos dos commits así:

```bash
$ git diff HEAD^ HEAD
```

O, podemos ver los cambios que se han producido en los últimos tres commits así:

```bash
$ git diff HEAD~3 HEAD
```

# Checkout: moverse a otra rama o commit
La opción `checkout` de Git la podemos usar para movernos de rama o de commit.

## Moverse a otro commit
¿Para qué podemos querer hacer esto? Para ver el estado de los ficheros y del proyecto en un commit atrás en el tiempo. Para moverte:

```bash
$ git checkout <hash del commit al que te quieres mover>
```

En este punto, el puntero `HEAD` quedará *detacheado* (*detached HEAD state*) lo que significa que no estás en ninguna rama. Así que, cualquier cambio que hagas en esta situación quedará huérfano.

Para volver al último commit, imaginanado que estás en la rama *main*, basta con hacer:

```bash
$ git checkout main
```

## Moverse a otra rama
Te puedes mover de una rama a otra con el comando `git checkout` indicando el nombre de la nueva rama. Imagina que estás en la rama *main* y quieres moverte a la rama *ejemplo*:

```bash
$ git checkout ejemplo
```

Los cambios que no hayan sido *commiteados* se arrastran.

Un opción muy útil es la de crear la rama y moverse a ella. Lo que haríamos en dos comandos:

```bash
$ git branch ejemplo
$ git checkout ejemplo
```

Lo puedes hacer en uno, con la opción *-b* de *checkout*:

```bash
$ git checkout -b ejemplo
```
