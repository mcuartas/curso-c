# Ficheros de texto

Vamos a ver como leer datos y escribir datos en un fichero de texto desde C. Para ello utilizaremos las funciones **fprintf** y **fscanf** de la librería **stdio**. Su funcionamiento es muy similar a la lectura y escritura de datos por consola con **printf** y **scanf**.

## Lectura de datos

### Lectura individual de datos

Supongamos que tenemos un fichero de texto llamado **data.txt** con el siguiente contenido:

	1973
	14.2
	m

Para poder leer los tres datos utilizaremos el siguiente código:

	#!c
	#include <stdio.h>

	void main()
	{
	    int a;
	    float b;
	    char c;
	    
	    FILE *f;
	    f = fopen("data.txt", "r");
	    
	    fscanf(f, "%i", &a);
	    fscanf(f, "%f", &b);
	    fscanf(f, "%c", &c);
	    
	    fclose(f);
	}

En la línea 1 se incluye la librería **stdio**.

Para trabajar con un fichero es necesario declarar primero un puntero al fichero. Esto se hace con la instrucción `#!c FILE *f` donde **f** es el identificador que seleccionamos para el puntero.

!!! bug "No olvides el \*"
	Un puntero es una variable que almacena una dirección de memoria. Un puntero se declara igual que una variable, pero tenemos que escribir un **\*** delante del nombre de la variable en la declaración.

Una vez declarado el puntero, es necesario asignarle un valor con `#!c f = fopen("data.txt", "r")`. Para ello utilizamos **fopen** que se encarga de abrir nuestro fichero y devolver una referencia al mismo que guardaremos en la variable **f**.

A la función **fopen** le pasamos dos argumentos. El primero es el nombre del fichero entre comillas. El segundo es una letra para indicar el modo en que abrimos el fichero:

|Modo|Nombre   |Descripción        |
|----|---------|-------------------|
|r   |Read     |Para leer datos    |
|w   |Write    |Para escribir datos|
|a   |Append   |Para añadir datos  |

El modo **r** sirve esclusivamente para leer datos del fichero. Los modos **w** y **a** sirven ambos para escribir datos en el fichero. La principal diferencia es que **w** siempre sobreescribe el fichero si ya existía, creando uno nuevo. Por el contrario, **a** añade datos a los que ya hay en el fichero en el caso de que el fichero existiera ya.

Una vez que ya hemos abierto el fichero en modo lectura y hemos almacenado en una variable un puntero al mismo, ya podemos leer los datos. La lectura en su forma más simple (la que vamos a ver) es secuencial. Esto significa que debemos de leer todos los datos en orden desde el principio.

Para leer datos utilizaremos la función **fscanf** pasándola tres cosas:

* La primera es un puntero al fichero.
* La segunda es una cadena de formato que indica el o los datos a leer.
* La tercera es una o varias variables donde deseamos almacenar el o los datos leidos.

En nuestro ejemplo leemos solo un dato cada vez. Por ejemplo, para leer el primer dato entero escribimos `#!c fscanf(f, "%i", &a)`. Por ello en la cadena de formato incluimos un único comodín según el tipo de dato. **%i** para leer un valor entero, **%f** para leer el dato con decimales y **%c** para leer el carácter.

Después de la cadena de formato hay que colocar tantas variables como comodines hemos utilizado (en nuestro caso solo uno) separadas por comas. Al nombre de esas variables hay que ponerle delante el carácter **&**.

!!! bug "No olvides el **&**"
	La función **fscanf** va a guardar un valor en las variables que le pasamos. Por ello, debemos enviarle un puntero a la variable. Es decir, la dirección de memoria donde reside la variable. A esto se le llama pasar un parámetro por referencia. Para obtener ese puntero, debemos escribir el carácter **&** delante del nombre de la variable que pasamos como argumento a **fscanf**.

Una vez realizadas las tres lecturas individuales de datos hemos terminado el trabajo con nuestro fichero. Una práctica recomendable es cerrar en ese momento el fichero. De esta forma lo liberamos y permitimos que otras aplicaciones o el propio sistema operativo puedan trabajar con él. Para cerrar el fichero utilizaremos la función **fclose** enviándole el puntero al fichero que queremos cerrar como argumento.

### Lectura del fichero completo

Vamos a ver cómo podemos leer todos los datos de un fichero. Supongamos que tenemos un fichero con un dato numérico entero en cada línea. Dicho fichero tiene un número indeterminado de líneas y deseamos leer todos los datos hasta el final.

Podemos crear un fichero de ejemplo llamado "datos.txt" con el siguiente contenido:

	34
	21
	10
	41

Para poder leer todos los datos y mostrarlos por consola escribimos el siguiente código:

	#!c
	#include <stdio.h>

	void main()
	{
	    int a;
	    FILE *f;
	    f = fopen("data.txt", "r");

	    while( fscanf(f, "%i", &a) == 1)
	    {
	        printf("%i\n", a);
	    }

	    if(feof(f))
	    {
	        printf("Proceso completo");
	    }
	    else
	    {
	        printf("Error leyendo datos");
	    }

	    fclose(f);
	}

La función **fscanf** devuelve un valor entero indicando el número de datos leidos con éxito. En el ejemplo, en cada llamada a **fscanf** leemos un solo dato. Podemos utilizar el valor de retorno de **fscanf** para comprobar si se ha leido un dato y poner esta expresión como condición para la repetición de un ciclo **while**. El ciclo se repetirá mientras que se lean datos correctamente y finalizará cuando se alcance el final de fichero.

Debemos tener presente que el ciclo también podría finalizar al encontrar un dato inválido en el fichero. Podemos probar a sustituir el número 10 por la palabra "diez" en el fichero para comprobarlo. Para distinguir estos dos casos (se alcanza el final de fichero y aparece un dato que no se puede leer) realizaremos una comprobación al final con una estructura **if**. La condición hace uso de la función **feof** que devuelve cierto o falso según si el fichero que pasamos como argumento ha alcanzado su final o no.

### Lectura múltiple de datos

Cuando cada línea de un fichero tiene un formato de datos equivalente, es posible leerlos con una sola llamada a **fscanf**. Supongamos que tenemos el fichero **datos.txt** conteniendo en cada línea un identificador de persona, su edad y su talla.

	1 28 1.78
	2 23 1.82
	3 18 1.56
	4 57 1.65

Podemos leerlo hasta el final y mostrar su información por consola con el siguiente código:

	#!c
	#include <stdio.h>

	void main()
	{
	    int id, edad;
	    float talla;

	    FILE *f;
	    f = fopen("data.txt", "r");

	    while( fscanf(f, "%i %i %f", &id, &edad, &talla) == 3)
	    {
	        printf("id: %i edad: %i talla: %.2f\n", id, edad, talla);
	    }
	    fclose(f);
	}

Para poder leer los datos de una línea con una sola llamada a **fscanf** utilizamos una cadena de formato con tres comodines `#!c "%i %i %f"` y, a continuación, especificamos las tres variables que corresponden, por orden, a cada comodín. En este caso, la condición para procesar los datos y seguir leyendo del **while** es que el número de datos leido sea igual a 3. Ese es el valor que retorna **fscanf**.

### Datos variables por línea

Podría ser que en cada línea se especificara como primer dato entero, el número de datos que aparecen en esa línea. Supongamos que cada línea es una semana y el primer dato es el número de viajes en esa semana y los siguientes los km recorridos en cada viaje. La información de un mes en un fichero "datos.txt" sería:

	3 410 30 105
	5 15 15 15 21 18
	1 900
	2 410 15

Para poder leer todos esos datos, un posible algoritmo sería:

	#!c
	#include <stdio.h>

	void main()
	{
	    int n, i, distancia;
	    FILE *f;
	    f = fopen("data.txt", "r");

	    while( fscanf(f, "%i", &n) == 1)
	    {
	        for(i = 0; i < n; i++)
	        {
	            fscanf(f, "%i", &distancia);
	            printf("%i ", distancia);
	        }
	        printf("\n");
	    }
	    fclose(f);
	}

En la instrucción `#!c while( fscanf(f, "%i", &n) == 1)` leemos el primer dato de cada línea de forma individual. Si no encontramos ese dato asumimos que hemos alcanzado el final del fichero. Ese dato nos indica cuantos datos aparecerán en esa línea. Así que creamos un bucle con un **for** que se repita ese número de veces para leer de forma individual con un `#!c fscanf(f, "%i", &distancia)` cada dato.

## Escritura de datos

Para escribir datos en un archivo de texto podemos emplear el siguiente código:

	#!c
	#include <stdio.h>

	void main()
	{
	    FILE *f;
	    f = fopen("data.txt", "w");

	    fprintf(f, "Hola mundo!!!");

	    fclose(f);
	}

El programa crea un fichero de texto llamado **data.txt** con la frase **Hola mundo!!!**. Al igual que en la lectura de ficheros, hemos de declarar un puntero al fichero con `#!c FILE *f`. En lugar de **f** podriamos utilizar otro identificador para el puntero pero siempre precedido del carácter asterisco en la declaración.

El siguiente paso es abrir el fichero en modo de escritura. Para ello empleamos la función **fopen** pasándole dos argumentos. El primero el nombre del fichero y el segundo el modo en que queremos abrirle que puede ser **w** de *write* o **a** de *append*. Ambos argumentos van entre comillas. 

Si el fichero especificado no existe, al abrirlo en modo escritura se crea un nuevo fichero con ese nombre. La diferencia entre **w** y **a** es que con **w**, si ya existe un fichero, este se sobreescribe (se elimina) y se crea uno nuevo. Mientras que con la opción **a**, si ya existe una archivo, el nuevo contenido se añade al final del mismo.

Si se ejecuta el programa anterior varias veces, como se abre el archivo con **w**, en cada ocasión se sobreescribe el archivo generado la vez anterior. La conclusión es que siempre quedará un archivo con una única frase **Hola mundo!!!**.

Si sustituimos el modo de apertura por **a** y ejecutamos varias veces. En el archivo resultante apareceran varias frases **Hola mundo!!!**, una a continuación de la otra. Una por cada ejecución del programa.

!!! note "Contenido del fichero **data.txt** tras cinco ejecuciones del programa"
	Con el fichero abierto en modo **w**

		Hola mundo!!!

	Con el fichero abierto en modo **a**

		Hola mundo!!!Hola mundo!!!Hola mundo!!!Hola mundo!!!Hola mundo!!!

La escritura de datos se realiza con la función **fprintf**. Esta función recibe los siguientes argumentos:

* El primero es un puntero al fichero.
* El segundo es una cadena de formato entre comillas que puede incluir comodines.
* En el caso de utilizar comodines, los siguientes argumentos son tantos datos como comodines. Esos datos se sustituirán en los comodines con su formato correspondiente.

!!! nota "Saltos de línea en el fichero"
	Cada llamada a **fprintf** no genera al final un salto de línea en el fichero. Varias llamadas a **fprint** se van escribiendo una a continuación de la otra. La forma de especificar un salto de línea es incluyendo la secuencia de escape **\n**.

Veamos un ejemplo de escritura de datos a un fichero que genera varia líneas:

	#!c
	#include <stdio.h>
	#define TABLA 7

	void main()
	{
	    int i, m;

	    FILE *f;
	    f = fopen("data.txt", "w");

	    fprintf(f, "Tabla de multiplicar del %i\n", TABLA);
	    for(i = 1; i <= 10; i++)
	    {
	        m = TABLA * i;
	        fprintf(f, "%i x %i = %i\n", TABLA, i, m);
	    }

	    fclose(f);

	    printf("Tabla creada.");
	}

> Mensaje en la consola:

	Tabla creada.

> Contenido final del fichero:

	Tabla de multiplicar del 7
	7 x 1 = 7
	7 x 2 = 14
	7 x 3 = 21
	7 x 4 = 28
	7 x 5 = 35
	7 x 6 = 42
	7 x 7 = 49
	7 x 8 = 56
	7 x 9 = 63
	7 x 10 = 70

Cuando en el programa terminamos de trabajar con un fichero, es una práctica recomendable cerrar el fichero. De esta forma le liberamos para que el sistema operativo y otras aplicaciones puedan utilizarle. Para ello utilizaremos la función **fclose** pasando como argumento el puntero al fichero que queremos cerrar.