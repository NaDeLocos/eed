# Clasificación de las pruebas
Las pruebas se pueden clasificar en base a muchos factores. En esta imagen te resumo cómo podríamos clasificar los tipos de prueba en función de varios factores:

![Clasificación de las pruebas: resumen](./img/esquema_clasificacion_pruebas.svg)

Estos tipos de prueba no son excluyentes, es decir, puedes hacer pruebas manuales y automáticas; si haces pruebas manuales, puedes optar por en enfoque caja negra o el enfoque caja blanca. No obstante, hay enfoques para las que son mejores las pruebas manuales o las automáticas, por ejemplo.

De hecho, las pruebas de aceptación son manuales, no se hacen automáticas, porque no tiene sentido. Lo entenderás cuando termines de leer todo este apartado.

## En función del grado de automatización
Pueden ser **manuales** o **automáticas**.

Las pruebas **manuales** pueden ser **informales o ad-hoc**, es decir, se prueban sin un plan específico. También pueden ser **pruebas formales** en las que se sigue un plan definido en el que se indica los pasos que tiene que dar la persona que hace las pruebas y, a continuación, va señalando, anotando y respondiendo a cuestiones del plan de pruebas.

> Hasta ahora, en tus prácticas, todos los *tests* que has hecho son de este tipo: manuales y ad-hoc.

En las pruebas **automáticas** se usa un **programa paralelo al que estás desarrollando** y que prueba el programa automáticamente, sin interacción por parte del usuario. Se usan herramientas que facilitan el desarrollo de estas pruebas. Hay muchas herramientas o *frameworks* de tests automáticos. Algunos ejemplos: **JUnit**, **Selenium**, **Serenity** o **Mockito**.

## En función del grado de conocimiento del código
En las pruebas de **caja negra** se realizan y planifican tests sin inspeccionar el código fuente a probar. Lo que vas a probar es una caja negra dentro de la cual no sabes que hay, así que te limitas a proporcionar una entrada, esperando una salida determinada.

![Pruebas de caja negra](./caja_negra.png)

En las pruebas de **caja blanca** haces o planificas las pruebas en base al código fuente. Así pues, cuando usas el enfoque **caja blanca** puedes asegurarte que tus pruebas pasan por todas las partes del código fuente. Por ejemplo, si hay un `if-else` haces dos pruebas: una para pasar por el `if` y otra para pasar por el `else`.

![Pruebas de caja negra](./caja_blanca.png)

## En función del ciclo de vida en que se prueba
El desarrollo del software sigue un ciclo de vida que termina con la entrega del mismo al usuario o cliente final. En cada fase se planifican difentes tipos de pruebas. Desde las fases más tempranas hasta la última fase (entrega del software al usuario/cliente final) estas sería las pruebas que se realizan:

Las **pruebas unitarias** se aplican a un componente software, a una unidad concreta. En la Programación Orientada a Objetos (POO) será una clase; en la Programación Procedimental será una función o procedimiento; en la Programación Estructurada será una estructura de control.

Las **pruebas de integración** consisten en probar varias unidades y comprobar su funcionamiento en conjunto. Por ejemplo, en la POO probar cómo dos clases se integran y funcionan en conjunto.

En las **Pruebas de sistema** se busca, principalmente, validar las especificaciones del software completo, normalmente a través de casos de uso. También se hacen **pruebas de rendimiento** o **estrés** para comprobar que el sistema puede soportar las cargas especificadas, a nivel de CPU, tiempo en realizar tareas, cantidad de memoria secundaria que consume, tiempos de acceso a bases de datos, etc.

Las **pruebas de aceptación** las realizan los usaurios finales para dar su aprobación, y se dividen en dos tipos: pruebas **alfa** que las realizan los usuarios finales delante de los desarrolladores para discutir sobre las especificiones y resultados; y pruebas **beta** que las realizan los usuarios después de que los desarrolladores entreguen el produto al cliente.
