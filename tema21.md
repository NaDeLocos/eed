## Vi
**Vi** se pronuncia /vi:ai/ en inglés y es un editor de texto creado para el sistema operativo **Unix** en 1976.

El editor, es un editor, que se usa en la terminal. Así pues, para abrir el editor tienes que abrir la terminal y escribir el comando `vi`.

**Vi** es un editor *modal* que tiene dos modos de funcionar u operar:

- Modo inserción (*insert mode*) usado para escribir texto.
- Modo comando (*command mode*) donde los caracteres que tecleamos son considerados como comandos.

En el modo comando, cuando escribes el carácter `:` el cursor se sitúa debajo, en una especie de *prompt*, y queda a la espera de un comando compuesto de una o más letras que tendrás que acabar con la tecla `Enter`.

### Abrir un fichero
Para abrir un fichero con **Vi** tienes que ejecutar el siguiente comando:

```shell
$ vi <ruta al fichero>
```

- Si `<ruta al fichero>` existe, abrirá el fichero.
- Si `<ruta al fichero>` no existe, creará el fichero.

### Flujo de trabajo básico
1. Cuando abrimos **Vi** el editor está en modo comando.
2. En este modo comando te puedes mover por el texto usando las teclas: `h` para moverte un carácter a la izquierda, `l` para moverte un carácter a la derecha, `j` para moverte una línea abajo y `k` para moverte una línea arriba.
3. Para entrar al modo inserción tienes varias opciones básicas:
   - `i` para entrar en el modo inserción justo donde está el cursor.
   - `a` para entrar en el modo inserción un carácter delante de donde está el cursor.
   - `I` para entrar en el modo inserción al principio de la línea actual.
   - `A` para entrar en el modo inserción al final de la línea actual.
   - `o` para entrar en el modo inserción justo debajo de la línea actual.
   - `O` para entrar en el modo inserción justo arriba de la línea actual.
4. Para entrar al modo comando cuando está en el modo inserción pulsa la tecla `ESC`.

Una vez dentro del modo inserción puedes editar texto: escribir, borrar y modificar, como harías con cualquier otro editor.

### Moverte por el fichero
A parte de las teclas `h`, `j`, `k` y `l` para moverte como con las flechas de dirección, en **Vi** puedes moverte por el fichero con estos otros comandos:

- Moverte al principio del fichero: `1G`.
- Moverte al final del fichero: `G`.
- Moverse a la línea 5 del fichero: `5G`.
- Moverse al final de la palabra: `w`.
- Moverse al principio de la palabra: `b`.
- Moverse al final de la línea: `$`.
- Moverse al principio de la línea: `^`.

### Cerrar y/o guardar un fichero
Cuando has terminado de editar un fichero puedes salir de varias maneras:

- Guardar los cambios: para guardar los cambios que hayas hecho en el fichero entra al modo comando pulsando `ESC`, si no lo estás ya, y escribe `:` seguido de `w`. Luego pulsa `Enter` para ejecutar el comando y que guarde.

- Salir sin guardar: entra al modo comando pulsando `ESC`, si no lo estás ya, y escribe `:` seguido de `q` seguido de `!`, es decir: `:q!`. Cuando pulses la tecla `Enter` ejecutará el comando para salir.

- Salir guardando los cambios: puedes guardar y salir entrando al modo comando pulsando la tecla `ESC`, si no lo estás ya, y escribiendo `:wq`. Cuando pulses la tecla `Enter` ejecutará el comando, guardará y saldrá de **Vi**.

### Deshacer
El famoso `Ctrl-Z` de cualquier programa informático, es decir, deshacer la última acción, se puede hacer con **Vi** entrando al modo comando y tecleando `u`.

### Buscar texto
Para buscar texto:

1. Entra al modo comando.
2. Pulsa la tecla `/` y escribe a continuación el texto a buscar.
3. Pulsa `n` para ir a la siguiente ocurrencia.
4. Pulsa `N` para ir a la anterior ocurrencia.

Si, en lugar de pular `/`, pulsas `?` la búsqueda se iniciaría hacia atrás y los comandos `n` y `N` se invierten.

### Buscar y reemplazar
Para buscar y reemplazar en **Vi** se usa el siguiente comando:

`:%s/<texto a sustituir>/<texto nuevo>/g`

donde:
- `<texto a sustituir>` es el texto que quieres buscar.
- `<texto nuevo>` es el texto que por el que quieres reemplazarlo.

### Eliminar texto
En **Vi** "puro y duro" no se pueden usar las teclas de `Retroceso` y `Suprimir` en el modo edición para eliminar texto como lo haríamos en cualquier otro editor. Aunque se puede configurar para hacerlas funcionar como en el resto de editores, aquí te enseño cómo hacerlo del modo tradicional.

Para eliminar texto debes estar en modo comando y usar una de las siguientes opciones:

- Tecla `x` para eliminar el caracter que está sobre el cursor.
- Teclas `dw` para eliminar desde la posición del cursor al final de la palabra.
- teclas `dd` para eliminar la línea en la que se encuentra el cursor.
- Tecla `D` para eliminar desde la posición del cursor al final de la línea.
- Teclas `d0` para eliminar desde la posición del cursor al principio de la línea.

### Copiar, cortar y pegar
Puedes copiar con alguna de estas opciones:

- `yy` para copiar la línea completa en la que está el cursor.
- `yw` para copiar desde donde está el cursor al final de la palabra.
- `y$` para copiar desde donde está el cursor al final de la línea.
- `y^` para copiar desde donde está el cursor al principio de la línea.

Para cortar puedes usar, en realidad, una de los comandos que te indiqué arriba para eliminar texto, ya que cuando eliminas se copia lo eliminado al *portapapeles*.

Puedes pegar lo que hayas copiado y/o cortado con el comando `p`.
