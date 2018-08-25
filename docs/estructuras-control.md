# Estructuras de control

## Introducción

La ejecución de una programa es secuencial desde la primera sentencia del método **main** hacia abajo. Las estructuras de control de flujo permiten alterar este orden general de dos formas:

* Estructuras condicionales. Permiten ejecutar o no un bloque de código en base a si se cumple o no una condición.
* Estructuras de repetición. Permite repetir la ejecución de un bloque de código mientras se cumpla una condición.

Comenzemos por ver como podemos crear expresiones condicionales.

## Condiciones

Una condición es una expresión que se evalua a **cierto** o **falso**. En una expresión pueden participar como operandos valores literales, variables o funciones. Para construir expresiones condicionales podemos utilizar operadores relacionales. Los operadores condicionales comparan lo que tienen a su izquierda con lo que tienen a su derecha de la siguiente forma:

|Operador|Descripción      |Ejemplo|Resultado|
|--------|-----------------|-------|---------|
|>	     |Mayor que        |4 > 2  |cierto   |
|>=      |Mayor o igual que|4 >= 5 |falso    |
|<       |Menor que        |4 < 2  |falso    |
|<=      |Menor o igual que|1 <= 2 |cierto   |
|==      |Igual que        |1 == 1 |cierto   |
|!=      |Distinto que     |1 != 1 |falso    |

Es posible construir condiciones más complejas concatenando varias condiciones simples con los operadores lógicos **y**, **o** y **no**. A continuación se presentan estos operadores:

|Operador|Descripción|Ejemplo          |Resultado|
|--------|-----------|-----------------|---------|
|&&	     |y lógico   |4 > 2 && 3 < 1   |falso    |
|\|\|    |ó lógico   |4 > 2 \|\| 3 < 1 |cierto   | 
|!       |no         |!(4 < 2)         |cierto   |

Si dos o más condiciones se unen por el **y lógico** para que sea cierta la resultante, tienen que ser ciertas todas ellas. En otro caso la resultante es falsa.

Si dos o más condiciones se unen por el **ó lógico** para que sea cierta la resultante, vale con que cualquiera de ellas sea cierta. Solamente si todas son falsas el resultado es falso.

La exclamación (**no lógico**) convierte algo falso en cierto o bien, algo cierto en falso.

## Estructuras condicionales

### La estructura **if else**

La estructura **if** sigue el siguiente formato:

	:::c
	if(condicion)
	{
		// Bloque de código
	}

La estructura **if** consiste en la palabra clave **if** seguida de una expresión condicional entre paréntesis. A continuación viene un bloque de código entre llaves. Si la condición se cumple (es cierta) el bloque de código se ejecuta. Si la condición no se cumple (es falsa) el programa salta el bloque de código y continua.

	:::c
	if(condicion)
	{
		// Bloque si la condición se cumple
	}
	else
	{
		// Bloque si la condición no se cumple
	}

Opcionalmente se puede incluir la palabra clave **else** y otro bloque de código entre llaves. En el caso de que la condición no se cumpla, se ejecutará el bloque de código del **else**.

> Ejemplo:

	#!c
    int nota;
    printf("Dame nota: ");
    scanf("%i", &nota);
    if(nota >= 5)
    {
        printf("Aprobado");
    }
    else
    {
        printf("Suspenso");
    }

> Resultado 1:

	Dame nota: 9
	Aprobado

> Resultado 2:

	Dame nota: 3
	Suspenso

Es posible incluir estructuras **if** dentro de los bloques de código de otras estructuras **if**. Cuando un bloque de código de una estructura **if** solamente incluye una sentencia, se pueden omitir las llaves. No se aconseja esta práctica como norma general por los errores que puede generar. Pero existe un caso habitual que hace uso de esta funcionalidad para concatenar **if-else-if** de la siguiente forma:

> Ejemplo:

	#!c
	int nota;
    printf("Dame nota: ");
    scanf("%i", &nota);
    if(nota >= 0 && nota < 5)
    {
        printf("Suspenso");
    }
    else if(nota >= 5 && nota <= 10)
    {
        printf("Aprobado");
    }
    else
    {
        printf("Nota incorrecta.");
    }

En este ejemplo podemos ver la utilización de condicionales compuestas con el **y lógico**. Para que la condición se cumpla, se deben cumplir ambas condiciones simples. En la **línea 8** se ve como el **else** no lleva un bloque entre llaves sino que incluye directamente otro **if** que a su vez tiene un **else**.

### La estructura **switch case**

La estructura **switch** sigue el siguiente formato:

	:::c
	switch(variable)	// variable int o char
	{
		case valor1:
			// Código para valor 1
			break;
		case valor2:
			// Código para valor 2
			break;
		...
		default:	// Opcional
			// Valor no contemplado
			break;
	}

Cualquier algoritmo resoluble con un **switch case** lo podríamos resolver con **if**. Pero en algunos casos **switch** puede aportar más claridad al código. Su utilización o no es una decisión personal. La mejor forma de entender un **switch** es con un ejemplo:

> Ejemplo:
	
	#!c
    char luz;
    printf("Luz del semaforo (r, a, v) ? ");
    scanf("%c", &luz);
    switch(luz)
    {
        case 'r':
            printf("Parar");
            break;
        case 'a':
            printf("Parar si es posible");
            break;
        case 'v':
            printf("Continuar");
            break;
        default:
            printf("Continuar con precaucion");
            break;
    }

Se escribe la palabra **switch** seguida de una variable entre paréntesis. Lo habitual es que esta variable sea de tipo entero o de tipo carácter como en el ejemplo. Luego viene un bloque entre llaves. Dentro del bloque se crea un **case** para tratar cada posible valor de la variable. Para ello se pone la palabra clave **case** seguida del literal correspondiente al valor (en este caso un carácter, si la variable fuera un entero sería un número) y después el carácter **dos puntos**. En las líneas siguientes se escriben las sentencias que deseamos ejecutar cuando la variable tenga este valor (una o varias). Cuando queremos terminar el caso se pone la palabra clave **break**.

Opcionalmente se puede incluir una etiqueta **default:** para tratar cualquier posible valor no contemplado en los casos anteriores.

## Estructuras de repetición

### Estructura **while**

La estructura **while** sigue el siguiente formato:

	:::c
	while(condicion)
	{
		// Bloque de código
	}

El bloque de código que va entre llaves se repetirá mientras se cumpla la expresión condicional que va entre paréntesis (sea cierta). Veamos un ejemplo:

> Ejemplo:

	#!c
    int n = 1;
    while(n <= 5)
    {
        printf("%i\n", n);
        n = n + 1;
    }

> Resultado:

	1
	2
	3
	4
	5

!!! bug "Evita ciclos que no paren nunca"
	Cuando utilizamos una variable de control dentro de la condición, como la **n** en el ejemplo, dentro del bloque de código debe de existir alguna expresión que modifique el valor de esa variable. En el ejemplo se le suma 1 en cada repetición. Si no se modificase su valor, el ciclo se repetiría de forma indefinida.

!!! bug "Cuidado con las condiciones erroneas"
	Si cuando se ejecuta el **while** por primera vez no se cumple la condición, el bloque de código del **while** no se ejecutará ninguna vez.

### Estructura **do while**

La estructura **do while** sigue el siguiente formato:

	:::c
	do
	{
		// Bloque de código

	}while(condicion);

El **do while** es muy similar al **while**. La principal diferencia es que el bloque de código se ejecuta siempre una primera vez y es al final de cada ejecución cuando se decide si debe repetirse en base a si se cumple o no la condición. Esta estructura puede encajar bien en escenarios como los siguientes:

* Se le pide un dato al usuario y, si es incorrecto, se le debe volver a pedir.
* Se ejecuta un programa y, al final, se pregunta al usuario si desea repetirlo.

!!! bug "No olvides el punto y coma"
	Es importante tener presente que el **do while** finaliza en **punto y coma** a diferencia de otras estructuras como el **while**. Cuando una estructura termina con un bloque de código entre llaves no lleva punto y coma. En el resto de casos si lo llevan.

> Ejemplo:

	#!c
    int n = 1;
    do
    {
        printf("%i\n", n);
        n = n + 1;
    }while(n <= 5);

> Resultado:

	1
	2
	3
	4
	5

### Estructura **for**

La estructura **for** sigue el siguiente formato:

	:::c
	for(expresion1 ; expresion2 ; expresion3)
	{
		// Bloque de código
	}

La estructura **for** es muy utilizada. Habitualmente representa una forma compacta de escribir un ciclo regulado por una variable de control. Veamos un ejemplo para ilustrar cada una de las tres expresiones que aparecen entre paréntesis separadas por **punto y coma**.

> Ejemplo:

	#!c
    int n;
    for(n = 1; n <= 5; n++)
    {
        printf("%i\n", n);
    }

> Resultado:

	1
	2
	3
	4
	5

La ==primera expresión== se ejecuta una única vez cuando comienza la ejecución del **for**. Se utiliza para inicializar las variables que van a controlar el ciclo. En el ejemplo la **n** a la que se le da un valor inicial de **1**.

La ==segunda expresión== se evalua antes de cada repetición del bloque de código entre llaves. Su función es equivalente a la condición de un **while**. Si la expresión condicional se cumple (es cierta), se ejecuta el bloque entre llaves. En el ejemplo se comprueba si la variable **n** es menor o igual que **5**.

La ==tercera expresión== se evalúa después de cada repetición del bloque de código. Se utiliza para actualizar las variables que controlan la repetición del ciclo. En este caso suma **1** al valor de **n**. El operador **n++** es equivalente a escribir **n = n + 1**.

!!! bug "El separador de las expresiones es punto y coma"
	Recuerda que el separador de las tres expresiones del **for** es un **punto y coma**.

## break y continue

Es posible alterar la ejecución normal de un ciclo de repetición con las instrucciones *break* y *continue*.  

### La instrucción **break**

La instrucción *break* detiene la ejecución del ciclo.

> Ejemplo:

	#!c
    int n;
    for(n = 1; n <= 5; n++)
    {
        if (n == 3)
        {
            break;
        }
        printf("%i\n", n);
    }

> Resultado:

	1
	2

### La instrucción **continue**

La instrucción *continue* termina la repetición del bloque de código actual y continua evaluando la siguiente repetición.

> Ejemplo:

	#!c
    int n;
    for(n = 1; n <= 5; n++)
    {
        if (n == 3)
        {
            continue;
        }
        printf("%i\n", n);
    }

> Resultado:

	1
	2
	4
	5

### Ciclos infinitos

Aunque no es una práctica muy recomendable, en algunos casos puede resultar de utilidad crear un ciclo que no tenga una instrucción de parada en su estructura de control principal. La salida del ciclo se realizará mediante una instrucción **break**. Es posible crear un ciclo infinito de las siguientes formas:

> Mediante un **while**

	:::c
    int nota;
    while(1)
	{
		printf("Dame nota: ");
		scanf("%i", &nota);
		if(nota >= 0 && nota <= 10)
		{
			break;
		}
		else
		{
			printf("Introduzca nota entre 0 y 10\n");
		}
	}

> Mediante un **for**

	:::c
	int nota;
    for( ; ; )
	{
		printf("Dame nota: ");
		scanf("%i", &nota);
		if(nota >= 0 && nota <= 10)
		{
			break;
		}
		else
		{
			printf("Introduzca nota entre 0 y 10\n");
		}
	}

> Resultado:

	Dame nota: 14
	Introduzca nota entre 0 y 10
	Dame nota: -5
	Introduzca nota entre 0 y 10
	Dame nota: 9