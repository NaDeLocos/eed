# Depuradores
Podríamos decir que los programadores se encuentran en un ciclo de trabajo que consiste en: programar, probar y depurar.

Depurar consiste en detectar e identificar errores que hay en el software (*bugs*).

Hay varias formas de depurar un programa entre las que se encuentra la técnica de *printear* o imprimir mensajes por pantalla para ver el estado de las variables en un *scope* o ámbito concreto. No obstante, llegados al caso siempre es útil usar un **programa depurador** o *debugger*.

Los depuradores permiten detener el programa:

- En una línea de un fichero determinado por medio de un punto de ruptura o **breakpoint**.
- En una línea de un fichero determinado bajo unas condiciones: **breakpoint condicional**.

Cuando detienes un programa o estás en un lugar determinado puedes, entre otras cosas:

- Examinar y modificar el valor de las variables en ese ámbito o *scope*.
- Examinar el contenido de los registros del procesador.
- Examinar la pila de llamadas que se han desembocado en ese punto.
- Ejecutar instrucción a instrucción.

# JDB
El depurador de **Java** se llama **JDB** (*Java Debugger*) y es una herramienta en modo comando que viene incluida con el **JDK**.

Para poder usar el depurador de Java tendrás que compilar tus programas con la opción `-g`. Esta opción genera símbolos e información en el ejecutable que usará el depurador de Java. Sin estos símbolos e información no se puede depurar un programa.

Por ejemplo, imagina que tienes un programa llamado `Calculadora.java` y quieres depurar dicho programa. Tendrás que compilar este programa con la opción `-g`, como ves a continuación:

```shell
$ javac -g Calculadora.java
```

Ahora, ya puedes ejecutar el programa con el depurador. Como ves debajo, se ejecuta el programa con el comando `jdb` en vez de con `java`:

```shell
$ jdb Calculadora
```

Con esto entrarás al depurador (en línea de comandos):

```shell
Initializing jdb ...
> 
```

Es aquí donde tienes que usar los comandos del depurador (estás en "otra terminal", en la terminal del depurador, para que nos entendamos). Estos son los comandos del depurador:

- `run` para ejecutar. Si no hay puntos de parada se ejecutará el programa hasta el final, como si ejecutáramos el programa con `java`.
- `next` para ejecutar instrucción a instrucción el programa.
- `step` como `next` pero saltando (entrando) a los métodos.
- `stop at Calculator:10` para configurar un punto de parada en la línea 10 del fichero `Calculator.java`.
- `cont` para continuar la ejecucion desde donde estás hasta el siguiente *breakpoint* o el final del programa.
- `print` seguido del nombre de una variable para ver su valor actual.
- `list` para ver el código fuente alrededor del punto en el que estás.
- `locals` para ver la lista de las variables locales.
- `classes` para ver las clases que hay cargadas.
- `methods` seguido del nombre de un clase, muestra todos los métodos de esa clase.
- `help` para obtener una ayuda.
- `exit` para salir del depurador.

## ¿Qué pasa si el programa pide entrada de datos?
Tienes que ejecutar el depurador en una terminal tal que así:

```shell
java -Xdebug -Xrunjdwp:transport=dt_socket,address=8000,server=y,suspend=n MyClass
```

Y en otra terminal lanzar `jdb` para unirse a la ejecución anterior:

```shell
jdb -attach 8000
```

De todos modos, no te preocupes por esto porque acabaremos usando el depurador visual del editor de programación que usemos.

## Depurando en VSCode
Si has instalado la extensión de Java que hemos estado usando, ya tienes lo necesario para depurar programas de Java desde VSCode.

En otros editores sería similar.

En estos editores podemos configurar puntos de padara o *breakpoints* haciendo clic en el margen izquierdo en la línea donde queramos pararlo. Aparecerá un punto de color rojo. Si pinchas en ese punto rojo se quitará el *breakpoint*. Así de fácil. En la imagen siguiente puedes ver cómo hay un *breakpoint* en la línea 17:

[Breakpoint en la línea 17 de VSCode](img/vscode_breakpoint.png)

Ahora, si lanzas el depurador:

[Lanza el depurador en VSCode](img/vscode_launch_debugger.png)

Verás que aparecen los controles y toda la información que necesitas, todo visual e intuitivo:

[Depurador en VSCode ejecutándose](img/vscode_run_debugger.png)
