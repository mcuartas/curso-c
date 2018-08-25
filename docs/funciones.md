# Funciones

## Introducción

Un programa en C esta compuesto por una o varias funciones. Un programa siempre contiene una función llamada **main** que es el punto de entrada del programa. Una función incluye en su interior un cierto código que tiene un determinado proposito. De esta forma, al llamar a la función se ejecutará el código que contiene realizando una determinada tarea. Al usar funciones evitamos repetir en nuestro programa el mismo código o código similar una y otra vez. Ese conjunto de instrucciones que utilizamos frecuentemente, lo incluimos en una función. Las funciones también aportan claridad y legibilidad al código. Además, permiten verificar el código con más facilidad. Al dividir un programa grande en funciones es más fácil establecer pruebas que verifiquen que cada función realiza su labor correctamente.

El código contenido en una función puede llamar a otras funciones. Pero hay que tener presente que cada función tiene internamente sus propias variables y una función no tiene acceso a las variables declaradas en otra. Por ello, a la hora de llamar a una función se le pueden enviar datos que llamaremos argumentos. La función llamada recibe estos datos como parámetros y puede operar con ellos.

## Argumentos y parámetros

Veamos un ejemplo de función:

	#!c
	#include <stdio.h>

	void imprimir_suma(int a, int b)
	{
	    int suma;
	    suma = a + b;
	    printf("%i", suma);
	}

	void main()
	{
	    int n1 = 5, n2 = 4;
	    imprimir_suma(n1, n2);
	    printf("Fin del programa.");
	}

Definiremos una función antes de cualquier código que haga uso de ella. En el ejemplo vemos un programa formado por dos funciones: **imprimir_suma** y **main**. Cuando se ejecuta el programa, el sistema operativo comienza con una llamada a **main** que es el punto de entrada.

En **main** se declaran dos variables llamadas **n1** y **n2**. Estas variables no son visibles dentro del código de **imprimir_suma**. Así mismo, **main** no tiene acceso a la variable **suma** declarada en **imprimir_suma**.

Si nos fijamos en la definición de **imprimir_suma** vemos que aparece la palabra `#!c void` seguida del nombre de la función `#!c imprimir_suma`y, a continuación, una lista entre paréntesis de parámetros `#!c (int a, int b)`. Esos parámetros indican los datos que necesita la función para realizar su labor. En este caso, a la función se le envían dos números y su misión es mostrar su suma por consola. Por último viene el cuerpo de la función que es un bloque delimitado por llaves que contiene el código de la función.

Cada parámetro entre paréntesis `#!c (int a, int b)`consta de un tipo y un identificador. Es equivalente a declarar una variable. Esos parámetros van separados por comas. Cuando se realize una llamada a la función es necesario enviar un argumento por cada uno de los parámetros. En el ejemplo vemos la llamada `#!c imprimir_suma(n1, n2)` que consiste en poner el nombre de la función seguida de una serie de argumentos entre paréntesis. Cada uno de los argumentos `#!c (n1, n2)`==se corresponde por orden== con cada uno de los parámetros que hemos indicado en la definición de la función `#!c (int a, int b)`. Lo que se envía a la función (argumentos) y lo que la función espera recibir (parámetros) deben de coincidir en tipo.

Cuando se llama a la función, se realiza una copia de cada uno de los argumentos y se asigna su valor al parámetro correspondiente. La función entonces ejecuta su código y, cuando termina, devuelve la ejecución al punto inicial desde donde se la ha llamado para que continue. De esta forma, la secuencia de ejecución de instrucciones en el ejemplo es: 12, 13, 5, 6, 7, 14.

!!! note "Funciones sin parámetros"
	Es posible que una función no tenga parámetros ya que no necesita ningún dato para realizar su tarea. En ese caso los paréntesis en su definición iran vacios. También iran vacios los paréntesis en su llamada ya que no la pasaremos ningún argumento.

## Valor de retorno

Es posible que una función realize una tarea y necesite comunicar un resultado al código que la ha invocado. Imaginemos que en el ejemplo anterior la tarea de la función auxiliar no es calcular la suma e imprimirla por consola, sino solamente realizar la suma. El código entonces sería el siguiente:

	#!c
	#include <stdio.h>

	int calcular_suma(int a, int b)
	{
	    int resultado;
	    resultado = a + b;
	    return resultado;
	}

	void main()
	{
	    int n1 = 5, n2 = 4, suma;
	    suma = calcular_suma(n1, n2);
	    printf("La suma es %i", suma);
	}

En primer lugar vemos que en la definición de la función (a la que ahora hemos llamado **calcular_suma**) se establece un tipo de retorno **int** justo antes del nombre: `#!c int calcular_suma(int a, int b)`. Con esto estamos indicando que la función va a realizar una tarea y, cuando finalize, va a devolver una número entero al código que la ha llamado. Podemos apreciar como el resultado de la llamada a la función se guarda en la variable **suma** declarada en **main**: `#!c suma = calcular_suma(n1, n2)`.

!!! note "Variable vs Función con valor de retorno"
	En ese sentido podemos pensar que una función, cuando tiene un valor de retorno, es equivalente a una variable. En el punto del código donde se la invoca, se coloca su valor de retorno tras procesarla.

Una función que no devuelve ningún valor al código que la invoca tendra como tipo de retorno **void**. Podemos pensar en el significado de **void** como 'nada' o 'ninguno'. Si devuelve un valor, se especificará el tipo del valor de retorno que podrá ser cualquiera de los tipos que utilizamos en la declaración de variables (int, float, char...).

Cuando una función devuelve un valor es obligatorio que dentro de la función exista una instrucción **return** seguida del valor a devolver (una variable, un literal o una expresión en general). Dentro del cuerpo de una función pueden existir múltiples ocurrencias de **return + valor**. La primera de ellas que se ejecute finalizará la ejecución de la función.

## Parámetros de salida

En ocasiones puede ser necesario que una función devuelva más de un valor al finalizar su ejecución. Esto se consigue permitiendo a la función escribir valores en sus parámetros (que pueden ser muchos), para que los reciba el código que la ha llamado en sus argumentos. Esto requiere una forma especial de tratar dichos argumentos y parámetros. Vamos a escribir de nuevo la función **calcular_suma** utilizando esta técnica.

	#!c
	#include <stdio.h>

	void calcular_suma(int a, int b, int *suma)
	{
	    *suma = a + b;
	}

	void main()
	{
	    int n1 = 5, n2 = 4, suma;
	    calcular_suma(n1, n2, &suma);
	    printf("La suma es %i", suma);
	}

Vemos que ahora la función **calcular_suma** ya no devuelve directamente ningún valor. Su tipo de retorno es **void**. En cambio, ahora tiene tres parámetros en su definición y tiene tres argumentos en su llamada. Los dos primeros son los datos de entrada, los números a sumar. El tercero es el dato de salida, el resultado de la suma. Existen unas diferencias en como se tratan los datos de entrada y los datos de salida:

* Los datos de entrada son datos que enviamos a la función para que realize su cometido. La función no va a modificarles. Mientras que los datos de salida, son datos que enviamos para que la función modifique su valor y nos comunique, a través de ellos, resultados.

* Los datos de entrada se pasan **por valor**, es decir, se copia el valor del argumento (el contenido de la variable) en el parámetro correspondiente de la función. Los datos de salida se pasan **por referencia**, es decir, lo que se copia en el parámetro no es el contenido del argumento (su valor) sino la dirección de memoria donde reside dicho dato (un puntero o referencia). Esto va a permitir a la función que invocamos modificar su valor.

En la práctica esto supone que para pasar a una función un argumento de salida, en la invocación a la función debemos poner delante del nombre de la variable un carácter **&**. Esto indica que se le envíe a la función un puntero a esa variable `#!c calcular_suma(n1, n2, &suma)`.

En la definición de la función, el parámetro correspondiente de salida se declarará como un puntero. Para ello en la declaración se coloca un carácter **\*** delante del nombre de la variable: `#!c void calcular_suma(int a, int b, int *suma)`.

Para utilizar el parámetro dentro de la función a la que invocamos, debemos colocar delante de él el carácter **\*** cada vez. Podemos verlo en: `#!c *suma = a + b`.

|Declaración|Interpretación         |Valor almacenado|Dirección de memoria|
|-----------|-----------------------|:--------------:|:------------------:|
|int a      |Declaramos una variable|a               |&a                  |
|int *a     |Declaramos un puntero  |\*a             |a                   |

Veamos un ejemplo con dos parámetros de salida. La función **swap** intercambia el valor de dos variables con decimales.

	#!c
	#include <stdio.h>

	void swap(float *a, float *b)
	{
	    float temp;
	    temp = *a;
	    *a = *b;
	    *b = temp;
	}

	void main()
	{
	    float n1 = 0.5, n2 = 2.0;
	    swap(&n1, &n2);
	    printf("n1: %.1f n2: %.1f", n1, n2);
	}

> Resultado:

	n1: 2.0 n2: 0.5

## Casos especiales

Imaginemos que queremos crear una función **leer_dato** cuya misión sea pedir por consola un dato entero al usuario. Pasaremos a esa función un parámetro por referencia para que devuelva en él el dato leido. El ejemplo sería algo así:

	#!c
	#include <stdio.h>

	void leer_dato(int *a)
	{
	    printf("Dame un dato entero: ");
	    scanf("%i", a);
	}

	void main()
	{
	    int dato;
	    leer_dato(&dato);
	    printf("Dato leido: %i", dato);
	}

En la función se define el parámetro por referencia de la siguiente forma: `#!c void leer_dato(int *a)`. En la invocación a la función se envía el argumento (un puntero a la variable) de la siguiente forma: `#!c leer_dato(&dato)`. La cuestión a la que debemos prestar atención es a la llamada a la función **scanf**. El primer argumento que la enviamos es la cadena de formato **"%i"** el segundo argumento que espera **scanf** es ==un puntero a una variable== donde almacenar el dato. Es decir, espera que le pasemos una variable por referencia, un parámetro de salida. Dado que el parámetro **a** está declarado como un puntero le pasaremos directamente el puntero **a**: `#!c scanf("%i", a)`

!!! bug "Errores frecuentes en este caso"
	En este caso es frecuente cometer alguno de estos errores:

	* Poner `#!c scanf("%i", &a)` pensando que **a** está declarado como una variable.
	* Poner `#!c scanf("%i", *a)` pensando que debemos pasar el parámetro por valor.

Imaginemos ahora que necesitamos pasar un puntero a fichero a una función para que realize su tarea. La forma de hacerlo sería la siguiente:

	#!c
	#include <stdio.h>

	void procesar_fichero(FILE *f)
	{
	    int n;
	    fscanf(f, "%i", &n);
	    printf("Dato leido: %i", n);
	    // Resto del proceso del fichero
	}

	void main()
	{
	    FILE *f;
	    f = fopen("datos.txt", "r");
	    procesar_fichero(f);
	    fclose(f);
	}

En este caso el parámetro **f** se trata como un parámetro de salida aunque no vamos a escribir nada en él. La funcion no va a retornar ningún dato en él. La necesidad de pasarlo como puntero es porque en el código que invoca la función, **f** esta declarado como puntero `#!c FILE *f` y así se le pasamos a la función **procesar_fichero** cuya definición es `#!c void procesar_fichero(FILE *f)`.

!!! bug "Errores frecuentes en este caso"
	En este caso es frecuente cometer alguno de estos errores:

	* Poner `#!c procesar_fichero(&f)` pensando que **f** no esta declarado como puntero en **main**.
	* Poner `#!c void procesar_fichero(FILE f)` pensando que f es un parámetro de entrada.

## Recursividad

La recursividad consiste en una función que se llama a si misma para resolver un cierto problema. Imaginemos una función capaz de calcular el factorial de un número. Por ejemplo, factorial de 4 = 4 * 3 * 2 = 24.

	#!c
	#include <stdio.h>

	int factorial(int n)
	{
	    int r = 1, i;
	    for(i = n; i > 1; i = i - 1)
	    {
	        r = r * i;
	    }
	    return r;
	}

	void main()
	{
	    int n, f;
	    printf("Dame n: ");
	    scanf("%i", &n);
	    f = factorial(n);
	    printf("El factorial es %i", f);
	}

> Resultado:

	Dame n: 5
	El factorial es 120

Podemos resolver el cálculo del factorial con un algoritmo recursivo de la siguiente forma:

	#!c
	#include <stdio.h>

	int factorial(int n)
	{
	    if(n == 1)
	    {
	        return 1;
	    }
	    else
	    {
	        return n * factorial(n - 1);
	    }
	}

	void main()
	{
	    int n, f;
	    printf("Dame n: ");
	    scanf("%i", &n);
	    f = factorial(n);
	    printf("El factorial es %i", f);
	}

La solución recursiva consiste en ir generando una cola de llamadas de la función a si misma hasta llegar al factorial de 1 que devuelve un 1 y se van resolviendo todas las funciones en orden inverso hasta devolver el resultado. 

Operación |Llamada 1      |Llamada 2      |Llamada 3      |Llamada 4      |
----------|---------------|---------------|---------------|---------------|
Invocacion|factorial(4) ->|factorial(3) ->|factorial(2) ->|factorial(1)   |
Retorno   |[24] <- 4 * [6]|[6] <- 3 * [2] |[2] <- 2 * [1] |[1] <- 1       |

Los algoritmos recursivos suelen ser más expresivos y, sin duda, son fundamentales para resolver ciertos problemas complejos. Aún así ,en algunos casos, las soluciones recursivas pueden resultar ineficientes en tiempo de computación frente a otras alternativas.

Imaginemos el típico juego en el cual hay un tablero formado por una matriz grande de diamantes de diferentes colores. Si pulsamos en un diamante rojo, ese diamante y todos los adyacentes a él de color rojo deben desaparecer, y también los adyacentes a los adyacentes, etc. Es un problema en el cuál una solución recursiva puede ayudar mucho. Podemos crear la función **elimina_diamante** que llama a la función **elimina_diamante** en cada diamante de su contorno igual a él y, por último, se elimina a si mismo. Habria que crear un mecanismo de marcado para no repetir las posiciones ya recorridas pero la solución quedaría bastante simple en comparación con otros posibles algoritmos de resolución.