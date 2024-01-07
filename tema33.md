# TDD: Test-Driven Development
Llegados a este punto te voy a explicar TDD, una metodología de desarrollo de software basado en los tests, en la que se pone el foco en los tests y la descripción del sistema a desarrollar.

Esta técnica está dentro de lo que se conoce como **Desarrollo Ágil de Software** o *Agile Software Development*.

La idea detrás de TDD es que si escribes los tests primero, tendrás una mejor comprensión de lo que el código debería hacer.

TDD asegura que el código de tu progrma sea **testable**, **mantenible** y **extensible**.

Se sigue un ciclo de desarrollo que se puede resumir en los siguientes puntos:

1. Se añade un test
2. Se ejecutan todos los tests: el nuevo test va a fallar
3. Se escribe el código más simple para pasar el nuevo test
4. Todo los tests debería pasar
5. Refactorizar el código para mejorar su calidad

Estos pasos se repiten para cada nueva funcionalidad que se tenga que añadir.

Existen otras aproximaciones similares a TDD con los que te encontrarás como son BDD y DDD.

## BDD: Behaviour-Driven Development
BDD es un proceso de desarrollo de software focalizado en el comportamiento del software. Es una extensión de TDD donde los tests son escritos en un lenguaje natural que las partes interesadas puedan comprender.

Esto asegura que el software es desarrollado de acuerdo a las necesidades y comportamientos esperados por el usuario.

Los pasos que se siguen son:

1. Definir el comportamiento del software
2. Escribir tests que describan ese comportamiento
3. Escribir el código que pase los tests
4. Refactorizar el código para mejorar su calidad

## DDD: Domain-Driven Design
DDD se focaliza en el dominio del software. El dominio se refiere al espacio del problema que el software intenta resolver. DDD asegura que el software es construido alrededor de dicho dominio y que resuelve el problema de la mejor manera posible.

Estos son los pasos que se siguen:

1. Comprender el dominio del software
2. Definir el modelo del dominio
3. Implementar el modelo del dominio en código
4. Refinar el dominio del modelo continuamente
