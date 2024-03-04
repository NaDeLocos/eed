# Planificación de pruebas: enfoque de caja negra
En el **enfoque de caja negra** tenemos que leer bien las **especificaciones** del programa, módulo o artilugio a probar y, en base a ellas, planificar los casos de prueba.

Es por ello que aquí se puede hablar de **cobertura de especificación** ya que se trataría de cubrir con todo aquello que viene descrito en las esepcificaciones.

Es habitual encontrase con la posibilidad de que el conjunto de datos a pasar (o entradas) sea muy amplio, y se hace imposible probar con todas las posibilidades. Por eso, existe una técnica algebraica llamada **clases de equivalencia**.

Así pues, nuestro problema aquí va a ser encontrar dichas clases de equivalencia.

Estas clases de equivalencia las tenemos que especificar para las entradas y para la salidas.

Para terminar con esta introducción, y profundizar en todos estos aspectos, se sabe, por experiencia, que **un buen número de errores aparecen en torno a los puntos de cambio de las clases de equivalencia**, valores denominados **frontera o límite**.

# Clases de equivalencia
No hay reglas universales para identificar clases de equivalencia pero sí hay recetas para encontrar estas clases en algunos contextos que te listo aquí debajo:

- Si un parámetro de entrada debe estar comprendido en un cierto rango, aparecen 3 clases de equivalencia: por debajo, dentro y por encima del rango.

> Ejemplo: el rango de los 5 primeros números naturales [0, 1, 2, 3, 4]. Las clases de equivalencia serían estas tres: los números menores que 0, los números mayores que 4 y los números de dicho rango. 

- Si una entrada requiere un valor concreto, aparecen 3 clases de equivalencia: por debajo, dicho valor y por encima del valor.

> Ejemplo: en el caso de requerir un texto de tres caracteres tendríamos estas tres clases de equivalencia: textos con menos de tres caracteres, textos con más de tres caracteres y textos con exactamente tres caracteres.

- Si una entrada requiere un valor de entre los de un conjunto, aparecen 2 clases de equivalencia: en el conjunto o fuera de él.

> Ejemplo: en el caso de los días de la semana son dos las clases de equivalencia: cualquiera de los siete días (dentro) u otro texto cualquieras (fuera).

- Si una entrada es booleana, hay 2 clases: verdadero o falso.

# Valores límite o frontera
Como ya te he dicho al principio, la experiencia muestra que un buen número de errores aparecen en torno a los puntos de cambio de clases de equivalencia: valores denominados límite o frontera.

¿Cómo localizar estos valores límite o frontera?

- Si la clase de equivalencia es un rango [A - B] hay que probar:
  - A - 1
  - A
  - A + 1
  - B - 1
  - B
  - B + 1

- Si hay máximo o mínimo hay que probar:
  - max - 1
  - max
  - max + 1
  - min - 1
  - min
  - min + 1
  
Existen dos enfoques: valores límite de 2 o 3 valores, dependiendo de donde pongas la frontera o el límite.

Te explico:

Imagina el ejemplo en que se require un valor mayor o igual que 8:

[Valores límite: ejemplo 1](./img/valores_limite_1.png)

En este ejemplo puedes ver que se ha optado por usar la técnica de los 2 valores poniendo la frontera entre el número 7 y el 8. Por ese motivo, los valores límite son: el 7 y el 8.

Si pusieras el límite justo en el 8, entonces los valores límites serían: 7, 8 y 9. Así, usarías la técnica de los 3 valores.

Otro ejemplo.

[Valores límite: ejemplo 2](./img/valores_limite_2.png)

Aquí se require un valor entre el 1 y el 5, ambos incluidos. Hay dos fronteras: la frontera entre 0 y 1 y la frontera entre 5 y 6. Por eso, los valores límite son cuatro: 0, 1, 5 y 6.

Si usaramos la técnica de los tres valores entonces los valores límite serían: 0, 1, 2, 4, 5 y 6. ¿Por qué? Porque pondríamos los límites justo en los números 1 y 5.

¡Ojo!, los valores límite no se reducen tan solo a las entradas numéricas, también se aplican a:

- Vectores o arrays de elementos.
- Longitud/tamaño de las cadenas de caracteres.

Por ejemplo, si tienes una entrada que es un nombre de usuario de entre 5 a 10 caracteres, entonces los limites serían (usando la técnica de los 2 valores):

- Cadenas de 4 caracteres.
- Cadenas de 5 caracteres.
- Cadenas de 10 caracteres.
- Cadenas de 11 caracteres.

# Casos de prueba
Vale, todo esto está muy bien pero, ¿cómo elaboramos los casos de prueba en el enfoque de caja negra?

Siguiendo estos pasos:

1. Crea las clases de equivalencia para cada una de las entradas y para la salida: quédate con valores representativos de cada clase de equivalencia.

2. Identifica los valores límite de cada una de las entradas en las que existan dichos límites.

3. Coge los valores representativos de las clases de equivalencia y crea casos de prueba.

4. Coge los valores límites y crea casos de prueba con ellos.
