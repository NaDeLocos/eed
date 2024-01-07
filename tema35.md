# Planificar pruebas: casos de prueba
Un **caso de prueba** (en inglés **test case**) es la **descripción de una prueba** concreta, en la que se indican las entradas de la prueba, unas condiciones de ejecución y los resultados esperados.

Puedes realizar varios casos de prueba para comprobar que un requisito es completamente satisfactorio.

En algunas metodologías como RUP (Proceso Racional Unificado, del inglés Rational Unified Process) se recomiendan, por lo menos, dos casos de prueba por cada requisito: uno de ellos debe realizar la prueba positiva y otro debe realizar la prueba negativa.

## Plan de pruebas
En el desarrollo de software se tienen que construir documentos donde se indica toda la información necesaria para probar el software.

En este plan de pruebas se describen todas las pruebas que se tienen que hacer para probar todas las partes del software y, también, se indicarán los resultados obtenidos, quién ha hecho dichas pruebas, etc.

Dependiendo de la institución, empresa, organización o equipo de desarrollo este documento tiene una forma u otra.

Lo que simpre habrá en un plan de pruebas son:

- Qué tipo de propiedades se quieren probar: corrección, robustez, fiabilidad, amigabilidad, etc
- Cómo se mide el resultado
- En qué consiste la prueba con todo detalle sobre su ejecución
- Resultado que se espera

Todo esto debe estar documentado. El objetivo del documento es señalar el enfoque, los recursos y el esquema de actividades de prueba, así como los elementos a probar, las características, las actividades de prueba, el personal responsable y los riesgos asociados.

Un posible esquema del documento del plan de pruebas podría ser el siguiente:

- Identificador únicó del documento
- Introducción y resumen de elementos y características a probar
- Elementos software a probar
- Características a probar
- Características que no se probarán
- Enfoque general de la prueba
- Criterios de paso/fallo para cada elemento
- Criterios de suspensión y requisitos de reanudación
- Documentos a entregar
- Actividades de preparación y ejecución de pruebas
- Necesidades de entorno
- Responsabilidades en la organización y realización de las pruebas
- Necesidades de personal y formación
- Esquema de tiempos
- Riesgos asumidos por el plan y planes de contingencias
- Aprobaciones y firmas con nombre y puesto desempeñado

Junto a este documento, se pueden encontrar estos otros documentos:

- Documento de especificación del diseño de pruebas: especifica los refinamientos necesarios sobre el enfoque general reflejado en el plan e identifica las características que se deben probar con este diseño de pruebas
- Documento de especificación de caso de prueba: define uno de los casos de prueba identificado por una especificación del diseño de las pruebas.
- Documento de especificación de procedimientos de prueba: especifica los pasos para la ejecución de un conjunto de casos de prueba o, más generalmente, los pasos utilizados para analizar un elemento software con el propósito de evaluar un conjunto de características del mismo

No obstante, nosotros, en este módulo, cuando vayamos a planificar pruebas lo vamos a hacer de manera más informal, indicando los puntos absolutamente necesarios de cada caso de prueba, que te indicaré más adelante cuando vayamos a hacer ejercicios.

## Definir un caso de prueba
Nosotros, para nuestras prácticas, vamos a planificar las pruebas de una manera sencilla, recogiendo y anotando lo mínimo necesario.

Por cada caso de prueba vamos a anotar:

- **Descripción** de la prueba: indicando qué se quiere probar y detallando en qué va a consistir la prueba
- **Condiciones** en que se produce la ejecución
- **Entradas**: los datos que vamos a pasar o utilizar para la prueba
- La **salida** que se espera

Vayamos a un ejemplo para entender qué esperamos en los plantes de prueba que vamos a planificar: imagina que tenemos una clase en Java para la gestión del *login* o acceso típico de un programa. En este programa buscamos que el usuario introduzca un nombre de usuario y una contraseña. Aquí tienes dos casos de prueba para probar esta clase.

<table>
	<tr>
		<th colspan="2">Descripción</th>
	</tr>
	<tr>
		<td colspan="2">
			Se quiere probar que la clase Login dejará entrar al usuario si dicho usuario y contraseña está en la base de datos registrado
		</td>
	</tr>
	<tr>
		<th colspan="2">Condiciones de ejecución</th>
	</tr>
	<tr>
		<td colspan="2">
			En la base de datos se tiene un usuario "roman" con contraseña "123456"
		</td>
	</tr>
	<tr>
		<th>Entrada</th>
		<th>Salida</th>
	</tr>
	<tr>
		<td>
			Usuario: "roman"<br>
			Contraseña: "123456"
		</td>
		<td>
			 Dejar entrar y mostrar mensaje "Has iniciado sesión correctamente"
		</td>
	</tr>
</table>

<table>
	<tr>
		<th colspan="2">Descripción</th>
	</tr>
	<tr>
		<td colspan="2">
			Se quiere probar que la clase Login impedirá entrar a un usuario/contraseña no válidos (no existente)
		</td>
	</tr>
	<tr>
		<th colspan="2">Condiciones de ejecución</th>
	</tr>
	<tr>
		<td colspan="2">
			En la base de datos no se tiene un usaurio "gines" con contraseña "123456"
		</td>
	</tr>
	<tr>
		<th>Entrada</th>
		<th>Salida</th>
	</tr>
	<tr>
		<td>
			Usuario: "gines"<br>
			Contraseña: "123456"
		</td>
		<td>
			No deja entrar y devuelve un mensaje "Usuario y/o contraseña no válidos"
		</td>
	</tr>
</table>
