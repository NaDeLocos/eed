# Maven
Maven es una herramienta de software para la gestión y construcción de proyectos Java creada por Jason van Zyl, de Sonatype, en 2002. Tienes toda la información en su [página web](https://maven.apache.org/)

# Instalación de Maven
Instalar Maven es sencillo: descarga los binarios desde [la página web oficial](https://maven.apache.org/download.cgi), descomprímelo en el directorio seleccionado y añade el directorio `bin` que se encuentra en la carpeta descomprimida a la variable de entorno `PATH`, aunque existen otros métodos como instaladores o descargas de repositorio.

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

# Inicio rápido
## Crear un proyecto
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

## El POM
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

## Construir y ejecutar el proyecto
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

## Ejecutando herramientas de Maven
Lo que hicimos en el apartado anterior, cuando ejecutamos `mvn package`, fue ejecutar una **fase de Maven** (*Maven Phase*). Esta es la lista de algunos *Maven Phases* que se pueden usar:

- `validate` para validar si el proyecto es correcto.
- `compile` para compilar el código fuente. 
- `package` toma el código compilado y lo empaqueta en un formato distribuible tal como **JAR**.
- `verify` ejecuta todos los chequeos para verificar que el paquete es válido.
- `install` para instalar el paquete en el repositorio local para usarlo como dependencia en otros proyectos locales.
- `clean` para limpiar las construcciones anteriores.

# El fichero POM con detalle
El fichero `pom.xml` que se encuentra en la ráiz de un proyecto de Maven contiene información necesaria para la construcción:

- Información del proyecto.
- Dependencias.
- Plugins.

Al comienzo del fichero verás:

```xml
<groupId>com.proferoman.app</groupId>
<artifactId>mi_app</artifactId>
<version>1.0-SNAPSHOT</version>
```

Donde se indica el paquete de Java base (`groupId`), el nombre del proyecto (`artifactId`) y la versión (`version`). Así pues, cuando hablamos de **artefacto** nos referimos al proyecto y el **groupId** es el identificador del proyecto. La **versión** está claro lo que es.

En el apartado de `properties` se configura, entre otras cosas, la versión de **Java** a usar:

```xml
<properties>
  <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
  <maven.compiler.source>1.7</maven.compiler.source>
  <maven.compiler.target>1.7</maven.compiler.target>
</properties>
```

Los proyectos grandes suelen necesitar dependencias, es decir, bibliotecas de software. En nuestro ejemplo solo tenemos, como dependencia, **JUnit**, un *framework* de testing:

```xml
<dependencies>
  <dependency>
    <groupId>junit</groupId>
    <artifactId>junit</artifactId>
    <version>4.11</version>
    <scope>test</scope>
  </dependency>
</dependencies>
```

## Dependencias
Nos detenemos en las dependencias para explicar las partes que se tienen que indicar y de donde obtenerlas.

Para empezar, en las dependencias indicamos:

- `groupId`: el identificador de la dependencia (normalmente es un paquete).
- `artifactId`: nombre del proyecto.
- `version`: la versión a instalar y usar.
- `scope`: tenemos varias posibilidades, y básicamente indican cómo se va a usar, y en qué momento, la dependencia:
  - **compile**: opción por defecto: está disponible en todo el paquete y sus dependencias desde la compilación.
  - **provided**: son provistas por el JDK en tiempo de ejecución.
  - **runtime**: necesarias a la hora de ejecutar pero no de compilar el proyecto.
  - **test**: se usan cuando lanzamos los tests.
  - **system**: parecido a *provided* pero hay que añadir directamente el *JAR* que lo contiene.
  
Los artefactos o bibliotecas que usamos como dependencias se instalan de repositorios que tenemos que indicar, aunque por defecto se usa [https://mvnrepository.com](este repositorio).

Desde los repositorios podemos buscar bibliotecas o artefactos y copiar/pegar el fragmente de XML que hay que añadir en el apartado `dependency` del fichero `pom.xml`, como hemos visto en clase.

## Plugins
**Maven** tiene gran cantidad de plugins que podemos ver [en la página web oficial de Maven](https://maven.apache.org/plugins/).

Como ves, en el fichero `pom.xml` es donde se indican los plugins.

Cada plugin tiene una serie de *goals* que podemos ejecutar con el comando `mvn`.

Para ver los *goals* de un plugin puedes ejecutar el comando `mvn <plugin>:help`, por ejemplo, para ver los *goals* del plugin **compiler**:

```shell
$ mvn compiler:help
```

Verás, al final de la salida del comando, sus tres objetivos: **compiler:compile**, **compiler:help** y **compiler:testCompile**:

```shell
This plugin has 3 goals:

compiler:compile
  Compiles application sources

compiler:help
  Display help information on maven-compiler-plugin.
  Call mvn compiler:help -Ddetail=true -Dgoal=<goal-name> to display parameter
  details.

compiler:testCompile
  Compiles application test sources.
```

Si quieres ejecutar uno de esos objetivos lo tienes que hacer con el mismo comando `mvn`, tal que así: `mvn <goal>`. Por ejemplo, para ejecutar el *goal* llamado **compiler:compile**:

```shell
$ mvn compiler:compile
```
