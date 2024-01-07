# Introducción
Una de las fases importantes en el ciclo de vida de un programa antes de entregarlo es la **fase de pruebas**.

Esta fase es crucial, muy importante, y te sorprenderá como el tiempo que le dedicas a esta fase puede ser mayor que el tiempo que le dedicas a la programación. Así pues, el coste, en tiempo y en dinero, de esta fase es importante, y dependerá del programa que estés desarrollando: si hablamos de programas que involucran vidas humanas el coste de la fase de pruebas puede fácilmente superar con mucho los costes del programa en sí.

![Edsger Dijkstra](./img/edsger_dijkstra.jpg)

Edsger Dijkstra (11 de mayo de 1930 - 6 de agosto de 2002) fue un destacado físico y científico de la computación de origen holandés.

Sus algoritmos son conocidos por ofrecer soluciones a los problemas de una forma sólida y eficiente. Entre sus principales aportaciones destacan el conocido como algoritmo de Dijkstra, el algoritmo del banquero, el algoritmo de shuting yard o el problema de los filósofos.

Es también conocido por sus citas y frases memorables, entre las que te destaco, con motivo de este tema, la siguiente: **Las pruebas solo pueden demostrar la presencia de errores, no su ausencia.**

# ¿Por qué probar el software?
Los fallos de software ocasionan pérdidas de todo tipo, de confianza, económicas, de imagen, etc. Así, como ya te he comentado anteriormente, la fase de pruebas es fundamental por los siguiente motivos:

- Evitar plazos y presupuestos incumplidos
- Insatisfacción del usuario
- Pérdida de clientes
- Escasa productividad
- Mala calidad en el software producido

La fase de pruebas añade valor al producto: todos los programas tienen errores y en esta fase se trata de descubrirlos, ahí está el valor que se añade, ya que el objetivo específico de esta fase es la de encontrar cuantos más errores, mejor.

# Objetivo de las pruebas
Te lo resumo en un fase: **ejecutar el programa con el fin de encontrar errores**.

# Alcance de las pruebas
Llegamos al punto en el que tengo que presentarte uno de los términos que más vas a escuchar a partir de ahora: la **cobertura**.

**La cobertura de las pruebas** es una medición, más o menos aproximada, dado en tanto por ciento, con la que se trata de establecer **cuánto código cubren las pruebas planificadas**.

![Fórmula para obtener la cobertura de pruebas](./img/formula_cobertura.png)

Cuando se planifican las pruebas se busca que estas sean completas, la llamada **completitud**, que nos dará una idea del grado de fiabilidad de las pruebas. Debes tener claro que no se puede llegar al 100% del a completitud porque no es posible crear todas las posibles pruebas.

La prueba ideal sería aquella que expone al programa a todas las situaciones posibles. Como imaginas sería imposible. Llevado al ejemplo más simple: si escribes un programa que sume dos números, al probarlo no podrías diseñar una prueba que comprobara que todas las sumas posibles dan el resultado esperado, porque las pruebas serían infinitas.

Así, esta prueba ideal es imposible desde todos los puntos de vista: humano, económico y matemático.

A estas alturas ya imaginas que, aunque un programa tiene un conjunto finito de instrucciones, no podrías probar todas estas instrucciones ya que entran en juego variables, bucles y condiciones que hacen que las combinaciones sean gigantescas.

De todo esto surge la necesidad de diseñar un conjunto de pruebas lo más eficiente y efectivas posibles, cubriendo la mayor parte de los casos posible y más representativos. Lo veremos más adelante.
