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

### Instalación de Maven
Instalar Maven es sencillo: descarga los binarios desde [https://maven.apache.org/download.cgi](la página web oficial), descomprímelo en el directorio seleccionado y añade el directorio `bin` que se encuentra en la carpeta descomprimida a la variable de entorno `PATH`, aunque existen otros métodos como instaladores o descargas de repositorio.

> Si usas una distribución de GNU/Linux usa el gestor de paquetes para instalar Maven.

A partir de ese momento es posible ejecutar desde la línea de comandos el comando `mvn`.

```shell
$ mvn --version
```

Esto debería imprimir algo así:

```shell
Apache Maven 3.8.7 (b89d5959fcde851dcb1c8946a785a163f14e1e29)
Maven home: /opt/maven
Java version: 21, vendor: N/A, runtime: /usr/lib/jvm/java-21-openjdk
Default locale: es_ES, platform encoding: UTF-8
OS name: "linux", version: "6.6.1-arch1-1", arch: "amd64", family: "unix"
```

### Crear un proyecto
Si vas a usar **Maven** para iniciar un nuevo proyecto hazlo con el comando `mvn`. Crea una carpeta, sitúate en ella y ejecuta el siguiente comando:

```shell
mvn archetype:generate -DgroupId=com.proferoman.app -DartifactId=mi_app -DarchetypeArtifactId=maven-archetype-quickstart -DarchetypeVersion=1.4 -DinteractiveMode=false
```

Puede tardar un poco, espera. Al final, verás que se ha creado una carpeta llamada `mi_app` con la estructura del proyecto estándar:

```shell
mi_app/
├── pom.xml
└── src
    ├── main
    │   └── java
    │       └── com
    │           └── proferoman
    │               └── app
    │                   └── App.java
    └── test
        └── java
            └── com
                └── proferoman
                    └── app
                        └── AppTest.java
```

Te resultará familiar. El directorio `src/main/java` contiene el código fuente del proyecto y el directorio `src/test/java` el código fuente de los tests. El fichero `pom.xml` es el **Project Object Model** o **POM**. ¿Qué es ese fichero **POM**?

### El POM
El fichero `pom.xml` es el fichero de configuración del proyecto de **Maven** y contiene la información necesaria para construir el proyecto. Este fichero es enorme y entenderlo puede ser complejo, peor no necesitas entender todo lo que hay en él para usarlo de forma efectiva.

Vamos a echarle un vistazo:

```xml
<?xml version="1.0" encoding="UTF-8"?>

<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
  <modelVersion>4.0.0</modelVersion>

  <groupId>com.proferoman.app</groupId>
  <artifactId>mi_app</artifactId>
  <version>1.0-SNAPSHOT</version>

  <name>mi_app</name>
  <!-- FIXME change it to the project's website -->
  <url>http://www.example.com</url>

  <properties>
    <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
    <maven.compiler.source>1.7</maven.compiler.source>
    <maven.compiler.target>1.7</maven.compiler.target>
  </properties>

  <dependencies>
    <dependency>
      <groupId>junit</groupId>
      <artifactId>junit</artifactId>
      <version>4.11</version>
      <scope>test</scope>
    </dependency>
  </dependencies>

  <build>
    <pluginManagement><!-- lock down plugins versions to avoid using Maven defaults (may be moved to parent pom) -->
      <plugins>
        <!-- clean lifecycle, see https://maven.apache.org/ref/current/maven-core/lifecycles.html#clean_Lifecycle -->
        <plugin>
          <artifactId>maven-clean-plugin</artifactId>
          <version>3.1.0</version>
        </plugin>
        <!-- default lifecycle, jar packaging: see https://maven.apache.org/ref/current/maven-core/default-bindings.html#Plugin_bindings_for_jar_packaging -->
        <plugin>
          <artifactId>maven-resources-plugin</artifactId>
          <version>3.0.2</version>
        </plugin>
        <plugin>
          <artifactId>maven-compiler-plugin</artifactId>
          <version>3.8.0</version>
        </plugin>
        <plugin>
          <artifactId>maven-surefire-plugin</artifactId>
          <version>2.22.1</version>
        </plugin>
        <plugin>
          <artifactId>maven-jar-plugin</artifactId>
          <version>3.0.2</version>
        </plugin>
        <plugin>
          <artifactId>maven-install-plugin</artifactId>
          <version>2.5.2</version>
        </plugin>
        <plugin>
          <artifactId>maven-deploy-plugin</artifactId>
          <version>2.8.2</version>
        </plugin>
        <!-- site lifecycle, see https://maven.apache.org/ref/current/maven-core/lifecycles.html#site_Lifecycle -->
        <plugin>
          <artifactId>maven-site-plugin</artifactId>
          <version>3.7.1</version>
        </plugin>
        <plugin>
          <artifactId>maven-project-info-reports-plugin</artifactId>
          <version>3.0.0</version>
        </plugin>
      </plugins>
    </pluginManagement>
  </build>
</project>
```

### Construir y ejecutar el proyecto
Desde el directorio del proyecto, ejecuta este comando:

```shell
mvn package
```

En la salida verás muchas líneas y, al final, tienes que ver este mensaje, lo que significa que se ha construido correctamente:

```shell
[INFO] Building jar: /home/roman/tmp/mi_app/target/mi_app-1.0-SNAPSHOT.jar
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  8.992 s
[INFO] Finished at: 2023-11-16T20:06:47+01:00
[INFO] ------------------------------------------------------------------------
```

Una vez construido puedes ejecutar el programa:

```shell
$ java -cp target/mi_app-1.0-SNAPSHOT.jar com.proferoman.app.App
```

Que imprimirá:

```shell
Hello World!
```

### Ejecutando herramientas de Maven
Lo que hicimos en el apartado anterior, cuando ejecutamos `mvn package`, fue ejecutar una **fase de Maven** (*Maven Phase*). Esta es la lista de algunos *Maven Phases* que se pueden usar:

- `validate` para validar si el proyecto es correcto.
- `compile` para compilar el código fuente. 
- `package` toma el código compilado y lo empaqueta en un formato distribuible tal como **JAR**.
- `verify` ejecuta todos los chequeos para verificar que el paquete es válido.
- `install` para instalar el paquete en el repositorio local para usarlo como dependencia en otros proyectos locales.
- `clean` para limpiar las construcciones anteriores.
