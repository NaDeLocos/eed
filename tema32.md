# Técnicas o métodos para la realización de pruebas
Si echas un vistazo a la bibliografía relacionada con las pruebas de software verás que hay una gran cantidad de métodos y técnicas para la realización de pruebas.

En este apartado te explico algunas de las técnicas usadas para la realización de tests, aproximaciones al testing populares y que encontrarás en dichas bibliografías.

## Regresión (*regression testing*)
El software evoluciona a lo largo del tiempo y hay veces en que nuevas características en unos módulos pueden estropear funcionalidades en otros.

Por este motivo, cada vez que se evoluciona hay que ejecutar las pruebas anteriores para asegurar la consistencia del sistema y que no hay nada "roto".

Estas pruebas de regresión no suponen un gran esfuerzo extra cuando se han automatizado con herramientas específicas las pruebas, ya que basta con lanzarlas cada vez que se hagan cambios.

## Recorridos (*walkthroughs*)
En estos "recorridos" se sientan junto a los desarrolladores una serie de "críticos" que revisan el código, línea a línea, con el objetivo de pedir explicaciones sobre todas las partes del programa.

Cuando algo no queda meridianamente claro posiblemente sea porque se puede mejorar (a veces simplemente falta un comentario, sin más, otras hay que reescribir partes del código).

Esta técnica es muy eficaz localizando errores locales, muy localizados, pero no es útil para localizar errores que derivan de la integración de otras partes.

Hay que entender que el programa no se ejecuta, solo se revisa mirando e interpretando el código.

## Estrés (*stress testing*)
En estas pruebas el objetivo es comprobar cómo aguanta el sistema frente a cargas altas: de CPU, de almacenamiento, de recursos en general.

## Prestaciones (*performance testing*)
Cuando el tiempo de respuesta es importante hay que introducir este tipo de pruebas.

Por ejemplo, si tu aplicación hace un uso intensivo de bases de datos, donde se accede para recoger información, te interesa construir sentencias SQL eficientes y las que menos tiempo necesiten para extraer la información.

Aquí se usan *frameworks* o bibliotecas que midan los tiempos de ejecución de partes del software: *profiler*.

> En Java, por ejemplo, tienes **JProfiler** con el que poder perfilar y estipular el rendimiento, el uso de la memoria, etc, de tus programas en Java.
