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

## Comentarios

Podemos incluir comentarios explicativos en nuestro código para que nos sea más fácil entenderlo cuando pase el tiempo, o bien para que otras personas puedan comprender como funciona. No es conveniente comentar aspectos triviales del código, un buen código prácticamente se comenta a sí mismo. Pero ciertos algorítmos complicados o ciertas funciones reutilizables, por poner algunos ejemplos, requieren de comentarios aclarativos de su intencionalidad o de su funcionamiento.

Los comentarios comienzan con  **/\*** y terminan con **\*/** cuando ocupan más de una línea de código. Un comentario de una sola línea se inicia con **//** y termína al finalizar la línea en la que aparece. Los comentarios son ignorados por el compilador y no influyen en el funcionamiento del programa.

	#!c
	#include <stdio.h>

	/* 
	 *  Ejemplo de comentario
	 *  en varias líneas
	 */

	 void main() // Ejemplo de comentario en una línea
	 {
	 	printf("Hola mundo!"); // Otro comentario
	 }

!!! note "Nota"
	En el ejemplo anterior los asteríscos en las líneas 4 y 5 son únicamente estéticos y totalmente prescindibles. Es unicamente un estilo habitual de decorar comentarios que ocupan varias líneas.

## Escribir datos en la consola

Para escribir datos en la consola utilizaremos la función **printf**.

	#!c
	int a = 2;
	float b = 4.5, suma;
	char c = 'X';
	suma = a + b;
	printf("Mensaje sin datos\n");
	printf("La suma de %i y %f es %f \n", a, b, suma);
	printf("La letra %c es la ultima", c);

Resultado:

	Mensaje sin datos
	La suma de 2 y 4.500000 es 6.500000
	La letra X es la ultima



Con **printf** podemos mostrar un mensaje en la consola indicando el texto entre comillas tal y como vemos en la ==línea 5== del ejemplo anterior. El **\n** final es una secuencia de escape que indica un salto de línea. Las secuencias de escape sirven para representar caractéres especiales como el salto de línea (**\n**) o la tabulación (**\t**). Cuando queremos que se imprima una barra inclinada, para no confundirla con una secuencia de escape, utilizaremos el carácter (**\\\\**).

En la ==línea 6== se incluyen, dentro del texto a escribir, unos comodines formados por el carácter **%** seguido de una letra. Estos comodines se sustituiran por el valor de las variables que colocamos al final separadas por comas, siguiendo su orden. Cada comodín se corresponde con un tipo de dato: **%i** para enteros, **%f** para números con decimales y **%c** para tipo carácter. De esta forma, en el primer comodín se sustituye el valor de la variable **a**, en el segundo el valor de la variable **b** y en el tercero el valor de la variable **suma**. Para poder imprimir el carácter **%** utilizaremos **%%**.

|Tipo de dato|Comodín|
|------------|:-----:|
|entero      |%i     |
|fraccionario|%f     |
|carácter    |%c     |

	#!c
	float a = 10.555;
	printf("El valor %.2f sale con 2 decimales.", a);

Resultado:

	El valor 10.56 sale con 2 decimales.

Dentro de un comodín (código de formato), es posible ==establecer el número de decimales== con el que se mostrará el número. Para indicar 2 decimales utilizaremos el comodín **%.2f**. Colocamos un punto y el número de decimales deseado entre el carácter tanto por ciento y la letra f.

	#!c
	float a = 1.111, b = 2.222, c = 3.333;
	float d = 4.444, e = 5.555, f = 6.666;
	printf("Columna1\tColumna2\n");
	printf("%8.1f\t%-8.1f\n", a, b);
	printf("%8.2f\t%-8.2f\n", c, d);
	printf("%8.3f\t%-8.3f\n", e, f);

Resultado:

	Columna1        Columna2
	     1.1        2.2
	    3.33        4.44
	   5.555        6.666

También es posible ==indicar cuantas posiciones va a ocupar la impresión de un dato==. Esto nos permitirá disponer los datos en forma de columna. En el ejemplo anterior se especifica que los datos ocupen 8 posiciones cada uno. Por ejemplo, el comodín **%8.1f** indica que hay que mostrar el dato ocupando 8 posiciones y con 1 decimal. El número de posiciones puede ser positivo o negativo. Si es positivo el dato se alinea a la derecha en el espacio asignado. Si es negativo se alinea a la izquierda.

	#!c
	float dato = 10.555;
	int decimales = 1;
	printf("El dato es %.*f", decimales, dato);

Resultado:

	El dato es 10.6

Es posible ==especificar el número de decimales con una variable==. Esto nos permite leer ese valor de un fichero de configuración o bien preguntárselo al usuario. Para utilizar esta funcionalidad utilizaremos el comodín **%.\*f**. Al utilizar este comodín, la primera variable que viene a continuación debe de ser un dato entero que indique el número de posiciones decimales a representar (en el ejemplo anterior la variable **decimales**).




