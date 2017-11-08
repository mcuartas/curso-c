# Bienvenido al curso de C

!!! danger "Página en construcción"
	Este contenido es solo un prototipo para probar la funcionalidad de mkdocs.

## Primer programa

	#!c
	#include <stdio.h>

	void main()
	{
	    printf("Hola mundo!!!");
	}

Este programa muestra el siguiente mensaje por consola.

	Hola mundo!!!
	Process returned 13 (0xD)   execution time : 0.016 s
	Press any key to continue.

Con la directiva `:::c #include <stdio.h>` incluimos la librería estándar de funciones de entrada y salida (standard input - output) en el programa. Esto lo haremos al comienzo de cada programa para poder usar las funciones de entrada (leer o pedir datos) y de salida (mostrar o escribir datos).

==Los programas tendrán siempre una función llamada `:::c main`, seguida de un bloque entre llaves==. Esta función es la primera que se ejecuta, es decir, es el punto de entrada de nuestro programa. En el caso más simple, no devuelve ningún valor (`:::c void`) y no recibe ningún parámetro (por eso los paréntesis después de `:::c main` van vacios).

Dentro de la función `:::c main` encontramos la instrucción `printf("Hola mundo!!!");`. Esta instrucción muestra el mensaje que va entre comillas en la consola. ==La norma general es que cualquier instrucción finaliza con un punto y coma==. 

!!! warning "Instrucciones que no terminan en punto y coma"
	Algunas instrucciones no siguen la regla general de finalizar en punto y coma: 

	* Las directivas al comienzo del programa (`:::c #include <stdio.h>` es una directiva).

	* 	Instrucciones que llevan, a continuación, un bloque de código entre llaves. Por ejemplo, la definición de la función `:::c void main()` tampoco finaliza en punto y coma.

## Literales

Cuando queremos incluir un dato de forma literal dentro de nuestro código seguiremos las siguientes indicaciones:

*	Si es un número entero lo escribiremos tal cual: **14**.
* 	Si es un dato con decimales utilizaremos siempre el punto decimal: **2.5**.
*   Si es un solo carácter lo roderaremos por unas comillas simples: **'m'**.
*   Si es una cadena de carácteres (varios) lo rodearemos por comillas dobles: **"Hola mundo!!!"**.

## Variables

Las variables son contenedores que podemos utilizar en nuestro programa para guardar datos. Una variable solo puede guardar un dato de un determinado tipo. Utilizaremos tres tipos de datos básicos: números enteros, números con decimales y carácteres.

|Tipo de dato|Nombre    |Ejemplo|
|------------|----------|-------|
|entero      |int       |14     |
|fraccionario|float     |25.32  |
|carácter    |char      |'m'    |

Podemos utilizar cualquier nombre para las variables siguiendo las siguientes normas:

* 	Pueden contener letras, números y guiones bajos.
*	Deben empezar por una letra.
*	No pueden ser iguales a ninguna de las palabras reservadas del lenguaje.
*	No utilizar la letra ñ en los nombres.
* 	Preferiblemente utilizar letras minúsculas para las variables.
*   Preferiblemente utilizar guion bajo para concatenar palabras en nombres de variables largos (formados por varias palabras).

Para utilizar una variable en un programa, previamente hay que declarar la variable. Esto se suele hacer al inicio del programa. ==Declarar una variable consiste en especificar de qué tipo es y cuál es su nombre==.

	:::c
	int edad;
	float altura;
	char inicial;

En el ejemplo anterior se declaran tres variables, una de cada tipo.

Es posible declarar varias variables de un mismo tipo a la vez, separándolas por comas. También es posible asignarlas un valor inicial en el momento de declararlas.

	:::c
	int altura = 10, anchura = 20, longitud = 30;
	float velocidad, aceleracion = 9.8;

## Constantes

Las constantes son identificadores para datos que tienen un valor fijo. En lugar de utilizar el valor literal en diferentes partes del programa, se le asigna al dato un identificador y se vincula el valor al identificador en una directiva al comienzo del programa. De esta forma utilizamos el identificador en el programa sin necesidad de repetir el valor literal. Además resulta más sencillo cambiar su valor, si fuera necesario.

	:::c
	#define PI 3.14159

Para crear una constante escribimos la directiva `:::c #define` seguida del identificador y seguido este del valor. Lo habitual es utilizar letras mayúsculas para distinguirlos de las variables.

## Operadores básicos

Los operadores básicos son la asignación, la suma, la resta, la multiplicación, la division y el módulo.

|Operador |Nombre        |Ejemplo|Resultado  |
|---------|--------------|-------|-----------|
|=        |asignación    |n = 5  | n vale 5  |
|+        |suma          |5 + 2  | 7         |
|-        |resta         |5 - 2  | 3         |
|*        |multiplicación|5 * 2  | 10        |
|/        |división      |5 / 2  | 2         |
|%        |modulo        |5 % 2  | 1         |

El operador de asignación toma el valor que tiene a la derecha y se lo asigna a la variable que hay a la izquierda. La división entre dos tipos de datos enteros da como resultado un tipo de dato entero (sin decimales), por eso el resultado en el ejemplo es 2. Si uno de los dos datos que intervienen hubiera sido *float* el resultado hubierá sido un valor con decimales (2.5). El operador módulo devuelve el resto de realizar la división entera. En el ejemplo, al dividir 5 entre 2 el resto que queda es 1.

## Mi primer programa

	#!c
	#include <stdio.h>
	#define PI 3.14159

	void suma(int a, int b, int *c)
	{
		*c = a + b;
	}

	void main()
	{
		int a, b, c;
		printf("Dame a: ");
		scanf("%i", &a);
		printf("Dame b: ");
		scanf("%i", &b);
		suma(a, b, &c);
		printf("La suma es %i", c);
	}

## Resultados en consola

	Dame a: 6
	Dame b: 6
	La suma es 12


