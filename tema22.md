# Construcción de proyectos en Java
Cuando los programas crecen es necesario organizarlos de manera que el mantenimiento de los mismos no se complique. Esto se suele hacer por medio de una jerarquía de directorios determinada y mediante el uso de **paquetes** o *packages* cuando hablamos de **Java**.

Los **paquetes** son contenedores de clases que permiten organizarlas y, además, que no haya conflictos de nombres: podemos tener dos clases llamadas `Car` si están en paquetes diferentes: `es.rgmf.Car` y `com.proferoman.Car`, por ejemplo.

En los siguientes apartados te explico, básicamente:

- Cómo organizar los ficheros de un proyecto de Java, en una jerarquía de carpetas.
- Cómo construir "a mano" un proyecto de Java.
- Cómo usar herramientas de construcción para simplificar ese trabajo "a mano".

## Estructura de un proyecto
Un programa fuente en Java, y en realidad en cualquier lenguaje, consta de una carpeta raíz dentro de la cual tenemos una jerarquía de carpetas con diferentes tipos de ficheros, entre los que tenemos los `*.java`.

Una estructura típica, y la que vamos a usar nosotros, es la que te indico aquí debajo:

```shell
miprograma/
├── src
│   ├── main
│   │   ├── java
│   │   └── resources
│   └── test
└── target
```

Como ves, tenemos una carpeta principal del programa llamada, en este caso, `miprograma`. Dentro tenemos dos carpetas:

- `src` donde encontramos el código.
- `target` donde dejaremos el código objeto y ejecutable del programa (los `*.class`).

Como ves, dentro de `src`, además, se encuentran dos carpetas:

- `main` donde encontraremos el código fuente y recursos como `*.xml`.
- `test` será donde dejaremos los tests automáticos (que veremos y estudiaremos en siguienes temas).

A su vez, dentro de `main` tenemos:

- `java` que será donde tengamos las clases de `*.java` organizadas por carpetas que se corresponden con el nombre del paquete en el que está.
- `resources` donde dejaremos algunos otros ficheros como definiciones de interfaces de usuario, logotipos, iconos y cadenas de traducción.

Te muestro, aquí, un ejemplo completo, en el que verás varios `*.java` y algún recurso:

```shell
miprograma/
├── README.md
├── src
│   ├── main
│   │   ├── com
│   │   │   └── proferoman
│   │   │       └── miprograma
│   │   │           ├── Main.java
│   │   │           └── models
│   │   │               ├── Car.java
│   │   │               ├── Plane.java
│   │   │               └── Train.java
│   │   │           └── views
│   │   │               ├── Desktop.java
│   │   │               └── Mobile.java
│   │   └── resources
│   │   │   └── logo.png
│   └── test
└── target
```

## Construcción "a mano" de un programa Java
Tomando como ejemplo este programa:

```shell
miprograma/
├── README.md
├── src
│   ├── main
│   │   ├── com
│   │   │   └── proferoman
│   │   │       └── miprograma
│   │   │           ├── Main.java
│   │   │           └── models
│   │   │               ├── Car.java
│   │   │               ├── Plane.java
│   │   │               └── Train.java
│   │   │           └── views
│   │   │               ├── Desktop.java
│   │   │               └── Mobile.java
│   │   └── resources
│   │   │   └── logo.png
│   └── test
└── target
```

Podemos deducir los paquetes en que están los ficheros fuente o `*.java`:

- `com.proferoman.miprograma.Main.java`
- `com.proferoman.miprograma.models.Car.java`
- `com.proferoman.miprograma.models.Plane.java`
- `com.proferoman.miprograma.models.Train.java`
- `com.proferoman.miprograma.views.Desktop.java`
- `com.proferoman.miprograma.views.Mobile.java`

Ahora podemos llevar a cabo los dos pasos para compilar y ejecutar este proyecto.

1. Compilar todos los ficheros fuente en `target/`:

```shell
javac -d target src/main/com/proferoman/miprograma/Main.java src/main/com/proferoman/miprograma/models/Car.java src/main/com/proferoman/miprograma/models/Plane.java src/main/com/proferoman/miprograma/models/Train.java src/main/com/proferoman/miprograma/views/Desktop.java src/main/com/proferoman/miprograma/views/Mobile.java
```

2. Ejecutar el programa que hay en `target/`. Fíjate como indicamos el paquete de la clase donde está el método estático `main`:

```shell
java -cp target com.proferoman.miprograma.Main
```

## Herramientas de construcción en Java
Hay dos bastante populares en **Java** que son: [https://maven.apache.org/](Maven) y [https://gradle.org/](Gradle).

Aquí vamos a trabajar con **Maven**.
