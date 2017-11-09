# Bienvenido a la programación con C

Esta documentación pretende ofrecer de la forma más simple y clara posible una introducción a la programación con el lenguaje C. Se presentan los temas con un lenguaje coloquial y sencillo. Se intenta presentar toda la información imprescindible para una persona que se inicia evitando ser una referencia exhaustiva del lenguaje. Esta documentación se apoya mucho en ejemplos que ilustran cada uno de los conceptos que se presentan.

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

Con la directiva `:::c #include <stdio.h>` incluimos la [librería estándar de funciones de entrada y salida](https://es.wikipedia.org/wiki/Stdio.h) en el programa. Esto lo haremos al comienzo de cada programa para poder usar las funciones de entrada (leer o pedir datos) y de salida (mostrar o escribir datos).

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

Existen otros operadores que sirven para simplificar ciertas operaciones muy habituales a la hora de programar. Expresan de forma más compacta expresiones que se pueden escribir con los operadores básicos. Estos operadores son **++**, **--**, **+=**, **-=**, **\*=**, **/=** y se explican en la siguiente tabla.

> Suponiendo a = 10

|Ejemplo |Equivalencia |Resultado  |
|--------|-------------|-----------|
|a++     |a = a + 1    | a vale 11 |
|a--     |a = a - 1    | a vale 9  |
|a += 2  |a = a + 2    | a vale 12 |
|a -= 2  |a = a - 2    | a vale 8  |
|a *= 2  |a = a \* 2   | a vale 20 |
|a /= 2  |a = a / 2    | a vale 10 |

## Prioridad de operadores

En una expresión formada por varios operandos y operadores no todo se ejecuta a la vez. Existen unas reglas que determinan que operadores se procesan antes que otros.

	#!c
	float a = 10, b = 2, c;
	c = a + 10 / b;

En el ejemplo, el operador división tiene mayor prioridad que la suma y la asignación. Por ello primero se ejecuta `#!c 10 / b` y posteriormente `#!c a + 5`. Por último se ejecuta `#!c c = 15`.

Como norma general, la multiplicacion y la división tienen mayor prioridad que la suma y la resta. Los operadores que tienen la misma prioridad entre ellos se ejecutan, en general, de izquierda a derecha (por ejemplo la multiplicacion y la división). A esto último se le llama 

En caso de duda, lo más recomendable es hacer uso intensivo de paréntesis para dejar claro el orden de las operaciones. Incluso cuando no sean extrictamente necesarios.

	#!c
	float a = 10, b = 2, c;
	c = (a + 10) / b;

Con esta modificación en el ejemplo **c** acaba valiendo **10** en lugar de **15**.

## Conversión de tipos

Es posible convertir un tipo de dato en otro poniendo delante de él el tipo destino entre paréntesis.

	#!c
	int a = 5;
	float b;
	b = (float)a;

Cuando realizamos operaciones entre tipos de datos enteros, el resultado es un número entero (con independencia de que hagamos con él luego).

> Ejemplo:

	#!c
	int a = 5, b = 2;
	float division;
	division = a / b;
	printf("%.2f", division);

> Resultado:

	2.00

En el ejemplo anterior se podría pensar que, dado que **division** admite decimales, el resultado se va a mostrar con decimales. Cuando se evalua la expresión `#!c division = a / b` el operador división tiene prioridad sobre el operador asignación. En primer lugar se ejecuta `#!c a / b` y después el resultado se almacena en `#!c division`. Dado que **a** y **b** son datos enteros, la división da como resultado un dato entero, que posteriormente se almacena en **division**. Para que la operación de lugar a un dato con decimales es necesario convertir, o bien el numerador, o el denominador, o ambos a un tipo **float**.

> Ejemplo:

	#!c
	int a = 5, b = 2;
	float division;
	division = (float)a / b;
	printf("%.2f", division);

> Resultado:

	2.50

Otra posible solución hubiera sido declarar las variables como **float** desde el principio.

Este caso también ocurre cuando intervienen literales en los cálculos. Si la operación hubiera sido `#!c division = a / 2` se podría haber resuelto sustituyendo el literal entero **2** por el literal con decimales **2.0**.

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

>Ejemplo:

	#!c
	int a = 2;
	float b = 4.5, suma;
	char c = 'X';
	suma = a + b;
	printf("Mensaje sin datos\n");
	printf("La suma de %i y %f es %f \n", a, b, suma);
	printf("La letra %c es la ultima", c);

>Resultado:

	Mensaje sin datos
	La suma de 2 y 4.500000 es 6.500000
	La letra X es la ultima



Con **printf** podemos mostrar un mensaje en la consola indicando el texto entre comillas tal y como vemos en la ==línea 5== del ejemplo anterior. El **\n** final es una secuencia de escape que indica un salto de línea. Las secuencias de escape sirven para representar caractéres especiales como el salto de línea (**\n**) o la tabulación (**\t**). Cuando queremos que se imprima una barra inclinada, para no confundirla con una secuencia de escape, utilizaremos el carácter (**\\\\**) y para las dobles comillas el carácter (**\\"**).

En la ==línea 6== se incluyen, dentro del texto a escribir, unos comodines formados por el carácter **%** seguido de una letra. Estos comodines se sustituiran por el valor de las variables que colocamos al final separadas por comas, siguiendo su orden. Cada comodín se corresponde con un tipo de dato: **%i** para enteros, **%f** para números con decimales y **%c** para tipo carácter. De esta forma, en el primer comodín se sustituye el valor de la variable **a**, en el segundo el valor de la variable **b** y en el tercero el valor de la variable **suma**. Para poder imprimir el carácter **%** utilizaremos **%%**.

|Tipo de dato|Comodín|
|------------|:-----:|
|entero      |%i     |
|fraccionario|%f     |
|carácter    |%c     |

> Ejemplo:

	#!c
	float a = 10.555;
	printf("El valor %.2f sale con 2 decimales.", a);

> Resultado:

	El valor 10.56 sale con 2 decimales.

Dentro de un comodín (código de formato), es posible ==establecer el número de decimales== con el que se mostrará el número. Para indicar 2 decimales utilizaremos el comodín **%.2f**. Colocamos un punto y el número de decimales deseado entre el carácter tanto por ciento y la letra f.

> Ejemplo:

	#!c
	float a = 1.111, b = 2.222, c = 3.333;
	float d = 4.444, e = 5.555, f = 6.666;
	printf("Columna1\tColumna2\n");
	printf("%8.1f\t%-8.1f\n", a, b);
	printf("%8.2f\t%-8.2f\n", c, d);
	printf("%8.3f\t%-8.3f\n", e, f);

> Resultado:

	Columna1        Columna2
	     1.1        2.2
	    3.33        4.44
	   5.555        6.666

También es posible ==indicar cuantas posiciones va a ocupar la impresión de un dato==. Esto nos permitirá disponer los datos en forma de columna. En el ejemplo anterior se especifica que los datos ocupen 8 posiciones cada uno. Por ejemplo, el comodín **%8.1f** indica que hay que mostrar el dato ocupando 8 posiciones y con 1 decimal. El número de posiciones puede ser positivo o negativo. Si es positivo el dato se alinea a la derecha en el espacio asignado. Si es negativo se alinea a la izquierda.

> Ejemplo:

	#!c
	float dato = 10.555;
	int decimales = 1;
	printf("El dato es %.*f", decimales, dato);

> Resultado:

	El dato es 10.6

Es posible ==especificar el número de decimales con una variable==. Esto nos permite leer ese valor de un fichero de configuración o bien preguntárselo al usuario. Para utilizar esta funcionalidad utilizaremos el comodín **%.\*f**. Al utilizar este comodín, la primera variable que viene a continuación debe de ser un dato entero que indique el número de posiciones decimales a representar (en el ejemplo anterior la variable **decimales**).

Es posible ampliar esta información en [wikipedia](https://es.wikipedia.org/wiki/Printf).

## Leer datos de la consola

Para leer datos de la consola, escritos por el usuario de nuestro programa, utilizaremos **scanf**.

> Ejemplo:

	#!c
	int velocidad;
	printf("Dame velocidad: ");
	scanf("%i", &velocidad);
	printf("La velocidad introducida es %i", velocidad);

> Resultado:

	Dame velocidad: 280
	La velocidad introducida es 280

En este ejemplo, el programa le pide al usuario una velocidad. El usuario teclea **280** y pulsa **INTRO**. A continuacion, el programa guarda el valor 280 en la variable **velocidad**. Por último, el programa imprime un mensaje en el que incorpora el valor de la variable **velocidad**.

Cuando la el programa encuentra la función **scanf** detiene su ejecución y espera a que el usuario teclee en la consola la información que considere y pulse la tecla INTRO. En ese momento se evalua esa información para guardarla en la variable que indicamos en la llamada a **scanf**.

Los parámetros que enviamos a **scanf** son semejantes a los que enviamos a **printf** (ver apartado anterior). En primer lugar una cadena de formato donde indicaremos el comodín correspondiente al tipo de dato que queremos obtener. **%i** para números enteros, **%f** para números con decimales y **%c** para un carácter. En segundo lugar, la variable donde queremos que se almacene el dato que el usuario va a introducir ==precedida por el carácter &==.

!!! danger "Poner & delante de las variables que pasamos a scanf"
	Cuando llamamos a **scanf** es necesario pasar un puntero a la variable donde queremos que se almacene el dato. (Un puntero es la dirección de memoria donde se ubica la variable). Esto permite a **scanf** modificar el valor de dicha variable. A esto se le llama pasar a una función una variable por referencia. Para ello es necesario poner delante del nombre de la variable un **&**. Uno de los fallos más frecuentes, al principio, es omitir ese carácter **&**. Así que es importante tenerlo presente.

Es posible leer varios datos de una sola vez, siempre que indiquemos en la cadena de formato los comodines correspondientes a esos datos, y le pasemos a **scanf** las variables correspondientes para guardarlos.

> Ejemplo:

	#!c
	int edad;
    float altura;
    printf("Teclee los datos separados por un espacio.\n");
	printf("Edad y altura en metros: ");
	scanf("%i %f", &edad, &altura);
	printf("Edad: %i, Altura: %.2f", edad, altura);

> Resultado:

	Teclee los datos separados por un espacio.
	Edad y altura en metros: 28 1.78
	Edad: 28, Altura: 1.78

En este ejemplo se le piden al usuario dos datos. El usuario introduce los dos datos separados por un espacio y pulsa **INTRO**. La función **scanf** es capaz de leer los dos datos simultaneamente y guardarlos en las variables **edad** y **altura**.

Cuando vamos a leer varios datos, en la cadena de formato de **scanf** es necesario introducir los comodines correspondientes con el formato adecuado para que coincidan con la entrada que el usuario realize. Luego, separadas por comas, incluiremos tantas variables como datos a leer. Es importante incluir el **&** delante de las variables para pasarlas por referencia.

Puede ser complicado que el usuario respete el formato esperado a la hora de introducir múltiples datos simultaneamente. En la mayor parte de los casos es recomendable pedir cada dato de forma individual.

## Configuración regional

==Cuando escribimos código==, no podemos utilizar la letra **ñ** ni **letras acentuadas** en el nombre de una variable. Para separar los decimales en literales numéricos utilizaremos el **punto** decimal y nunca la **coma**. Estas reglas se aplican ==SIEMPRE== a los identificadores y los literales en el código c que escribimos.

En cambio, ==el usuario de nuestro programa== puede ser que esté acostumbrado a ver palabras acentuadas, al uso de la **ñ** o bien, a introducir las cifras decimales con **coma** como separador decimal. Los sistemas operativos normalmente permiten al usuario configurar este tipo de aspectos. Un programa correcto, debería hacer uso de esta configuración del sistema operativo.

> Ejemplo:

	#!c
    int edad;
    float altura;
    printf("Cuántos años tienes ? ");
    scanf("%i", &edad);
    printf("Cuánto mides (metros) ? ");
    scanf("%f", &altura);
    printf("Tienes %i años y mides %.2f metros",
           edad, altura);

> Resultado:

	Cußntos a±os tienes ? 28
	Cußnto mides (metros) ? 1.78
	Tienes 28 a±os y mides 1.78 metros

En este código de ejemplo vemos que los mensajes que mostramos al usuario por consola llevan letras acentuadas y el carácter ñ. Estos carácteres no aparecen correctamente a la hora de ejecutar el programa. Además, el dato de altura que introduce el usuario con decimales, por defecto, debe ir obligatoriamente con un punto decimal. Vemos que, si no especificamos nada, las reglas para los mensajes al usuario y para que este introduzca datos, son las mismas que cuando creamos identificadores o literales en código c.

Es posible indicar al programa que tenga en cuenta la configuración regional del sistema operativo con una función llamada **setlocale** que está disponible en la librería **locale.h**. Vamos a modificar el ejemplo anterior aplicando está función:

> Ejemplo:

	#!c hl_lines="2 6"
	#include <stdio.h>
	#include <locale.h>

	void main()
	{
	    setlocale(LC_ALL, "");
	    int edad;
	    float altura;
	    printf("Cuántos años tienes ? ");
	    scanf("%i", &edad);
	    printf("Cuánto mides (metros) ? ");
	    scanf("%f", &altura);
	    printf("Tienes %i años y mides %.2f metros",
	           edad, altura);
	}

> Resultado:

	Cuántos años tienes ? 28
	Cuánto mides (metros) ? 1,78
	Tienes 28 años y mides 1,78 metros

Gracias a esta función, ahora se interpretan correctamente los acentos y las letras ñ que aparecen dentro de los ==literales de tipo cadena de carácter== (textos entre comillas) que aparecen en nuestro código. Además, el usuario utiliza las reglas indicadas en su configuración regional del sistema operativo para introducir valores numéricos.

Es importante recalcar que las reglas para construir identificadores de variables dentro del código y para incluir valores numéricos literales en el mismo no se ven alteradas por **setlocale**.

**setlocale** también afecta a otros aspectos como, por ejemplo, la comparación de textos o el formato de cantidades monetarias, fechas y horas.

## Funciones matemáticas

Podemos encontrar las funciones matemáticas más frecuentes en la librería **math**.
Para utilizarlas es necesario poner al principio del programa `:::c #include <math.h>`.

|Función |Nombre              |Ejemplo     |Resultado|   
|--------|--------------------|------------|--------:|
|sqrt    |Raiz cuadrada	      | sqrt(10)   |3.16     |
|pow     |x elevado a y       | pow(2, 3)  |8.00     |
|exp     |e elevado a x       | exp(2)     |7.39     |
|log     |Logaritmo neperiano | log(7.39)  |2.00     |
|log10   |Logaritmo en base 10| log10(7.39)|0.87     |
|sin     |Seno                | sin(1.57)  |1.00     |
|cos     |Coseno	          | cos(1.57)  |0.00     |
|tan     |Tangente            | tan(1)     |1.56     |
|asin    |Arco seno           | asin(1.00) |1.57     |
|acos    |Arco coseno         | acos(0.00) |1.57     |
|atan    |Arco tangente       | atan(1.56) |1.00     |
|sinh    |Seno hiperbólico    | sinh(1.00) |1.18     |
|cosh    |Coseno hiperbólico  | cosh(1.00) |1.54     |
|tanh    |Tangente hiperbólica| tanh(1.00) |0.76     |
|ceil    |Entero superior     | ceil(2.50) |3.00     |
|floor   |Entero inferior     | floor(2.50)|2.00     |
|fabs    |Valor absoluto      | fabs(-2.50)|2.50     |

> Ejemplo:

	#!c  hl_lines="2 8"
	#include <stdio.h>
	#include <math.h>

	void main()
	{
	    float n = 10;
	    printf("raiz: %.2f\ncubo: %.0f\n",
	           sqrt(n), pow(n, 3));
	}

> Resultado:

	raiz: 3.16
	cubo: 1000
