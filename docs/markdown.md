# Escribiendo Markdown

Markdown es un lenguaje de marcado ligero creado por John Gruber en 2004. Su objetivo es escribir utilizando un formato de texto plano fácil de escribir y fácil de leer. Basicamente consiste en decorar el texto de la forma más simple posible para poder incluir encabezados, listas, hyperenlaces, imagenes, negrita, bloques de cita, etc. Es posible encontrarlo en sitios tan relevantes como [GitHub](https://github.com/) o [Jupyter Notebooks](http://jupyter.org/). 

## Elementos básicos

Un parrafo es simplemente una o más lineas de texto consecutivas, separadas por una o más líneas vacias. (Una linea vacia es aquella que no contiene nada, o solamente espacios y/o tabulaciones). También es posible marcar un nuevo párrafo con dos o más espacios en blanco al final de la última línea.

#### Encabezados

Para marcar encabezados se colocarán de 1 a 6 almohadillas al comienzo de una línea.

	:::markdown
    # Encabezado de nivel 1
	## Encabezado de nivel 2
	### Encabezado de nivel 3

#### Bloques de cita

Para marcar bloques de cita se utilizara el carácter 'mayor que'.

	:::markdown
	> Esto es un ejemplo de  
	> bloque de cita

>Esto es un ejemplo de  
>bloque de cita

Se puede poner solo en la primera línea y marcará todo el párrafo. Es posible indentar niveles de bloque de cita dentro de otros bloques de cita con simbolos 'mayor que' adicionales.

#### Enfasis

Para marcar énfasis se utilizarán uno o dos asteriscos.

	:::markdown
	Alguna de estas *palabras* tiene énfasis.
	Alguna de estas **palabras** tiene énfasis.

Alguna de estas *palabras* tiene énfasis.    
Alguna de estas **palabras** tiene énfasis.   

#### Listas

Para marcar listas no numeradas utilizaremos el asterisco. 

	:::markdown
	*	Elemento 1
	*	Elemento 2
	* 	Elemento 3

* Elemento 1
* Elemento 2
* Elemento 3

Si las listas son numeradas, utilizaremos números seguidos de un punto.

	:::markdown
	1. Primer elemento
	2. Segundo elemento
	3. Tercer elemento

1. Primer elemento
2. Segundo elemento
3. Tercer elemento

Si un elemento de lista consiste en varios párrafos, cada párrafo consecutivo debe de estar indentado por 4 espacios o una tabulación.

#### Hyperenlaces

Para asignar un hyperenlace utilizaremos los corchetes para rodear el texto. La ruta la podemos poner a continuación entre paréntesis.

	:::markdown
	Esto es un enlace a [mi página](http://www.cuartas.es).

Esto es un enlace a [mi página](http://www.cuartas.es)

Existe la posibilidad de utilizar referencias a enlaces que se definen posteriormente. En ese caso unicamente incluimos el número de enlace. Más adelante es necesario definir el enlace que corresponde con cada número y, opcionalmente, un texto descriptivo.

	:::markdown
	Podemos comprar un ordenador (Dell)[1] o (Apple)[2].

	[1]: http://dell.com/	"Comprar en Dell"
	[2]: http://apple.com/	"Comprar en Apple"

Podemos comprar un ordenador [Dell][1] o [Apple][2].

[1]: http://dell.com/	"Comprar en Dell"
[2]: http://apple.com/	"Comprar en Apple"

#### Imagenes

La sintaxis es similar a los hyperenlaces. Para incluir imagenes in-situ se pone la ruta entre paréntesis, después de una exclamación y un texto alternativo entre corchetes. Opcionalmente se puede incluir un texto descriptivo.

	:::markdown
	![texto alternativo](/img/md-logo.png "Titulo opcional")

![texto alternativo](/img/md-logo.png "Titulo opcional")

También es posible utilizar referencias que es necesario definir posteriormente.

	:::markdown
	![texto alternativo][id]

	[id]: /img/md-logo.png "Titulo opcional"

![texto alternativo][id]

[id]: /img/md-logo.png "Titulo opcional"

#### Código

Para marcar texto como código es necesario indentar cada línea del bloque con cuatro espacios o una tabulación. Si el código va embebido en un párrafo, es neceario rodearlo por comillas simples invertidas. Consultar la sección de CodeHilite y de InlineHilite para funcionalidades extendidas.

#### Separadores

Para crear un separador se escriben tres o más asteriscos en una línea.

	:::markdown
	Entre esta línea...
	**** 
	y esta otra línea hay un separador.

Entre esta línea...
****
y esta otra línea hay un separador.

#### Secuencias de escape

Puede ocurrir que alguno de los caracteres especiales utilizados en markdown aparezcan de forma fortuita en el texto y originen efectos no deseados. Para evitarlo podemos utilizar las secuencias de escape para especificar que deseamos utilizar el caracter como texto sin que tenga ningún efecto colateral. Podemos utilizar el caracter '\' junto con cualquiera de los siguientes para crear una secuencia de escape.

	\ backslash
	` backtick
	* asterisco
	_ underscore
	{} curly braces
	[] square brackets
	() parentheses
	# hash mark
	+ plus sign
	- minus sign (hyphen)
	. dot
	! exclamation mark

## Extensiones

### Tablas

Una tabla simple se crea con guiones y barras verticales.

	:::markdown
	Cabecera 1 | Cabecera 2 | Cabecera 3
	-----------|------------|-----------
	Celda 1	   | Celda 2    | Celda 3
	Celda 4    | Celda 5    | Celda 6

Cabecera 1 | Cabecera 2 | Cabecera 3
-----------|------------|-----------
Celda 1	   | Celda 2    | Celda 3
Celda 4    | Celda 5    | Celda 6

Opcionalmente se pueden incluir barras verticales también al principio y final.

	:::markdown
	|Cabecera 1 | Cabecera 2 | Cabecera 3|
	|-----------|------------|-----------|
	|Celda 1	| Celda 2    | Celda 3   |
	|Celda 4    | Celda 5    | Celda 6   |

|Cabecera 1 | Cabecera 2 | Cabecera 3|
|-----------|------------|-----------|
|Celda 1	| Celda 2    | Celda 3   |
|Celda 4    | Celda 5    | Celda 6   |

Se puede indicar el alineamiento de cada columna con 'dos puntos' en las lineas de separación.

	:::markdown
	Cabecera 1    | Cabecera 2   | Cabecera 3
	:-------------|:------------:|--------------:
	Izquierda	  | Centro       | Derecha
	Izquierda     | Centro       | Derecha

Cabecera 1    | Cabecera 2   | Cabecera 3
:-------------|:------------:|--------------:
Izquierda	  | Centro       | Derecha
Izquierda     | Centro       | Derecha	

### Admonition

Extensión incluida en la librería estándar de Markdown que permite incluir contenido adicional en cajas de color con un título y un icono. Por ejemplo para resúmenes, notas, consejos o avisos.

```` markdown
!!! note
	Esto es un ejemplo de nota (note, seealso).
````

!!! note
	Esto es un ejemplo de nota (note, seealso).

```` markdown
!!! note "Esta es una nota con título"
	Lorem ipsum dolor sit amet, consectetur adipiscing elit.
	Nulla et euismod nulla. Curabitur feugiat, tortor non
	consequat finibus, justo purus auctor massa, nec semper
	lorem quam in massa.
````

!!! note "Esta es una nota con título"
	Lorem ipsum dolor sit amet, consectetur adipiscing elit.
	Nulla et euismod nulla. Curabitur feugiat, tortor non
	consequat finibus, justo purus auctor massa, nec semper
	lorem quam in massa.

```` markdown
!!! note ""
	Esta nota va sin título.
````

!!! note ""
	Esta nota va sin título.

En vez de note es posible utilizar las siguientes etiquetas: summary, info, tip, success, question, warning, failure, danger, bug y quote.

!!! summary
	Esto es un ejemplo de sumario (summary, tldr).

!!! info
	Esto es un ejemplo de bloque informativo (info, todo).

!!! tip
	Esto es un ejemplo de consejo o truco (tip, hint, important).

!!! success
	Esto es un ejemplo de bloque de éxito (success, check, done).

!!! question
	Esto es un ejemplo de pregunta (question, help, faq).

!!! warning
	Esto es un ejemplo de precaución (warning, caution, attention).

!!! failure
	Esto es un ejemplo de fallo (failure, fail, missing).

!!! danger
	Esto es un ejemplo de peligro (danger, error).

!!! bug
	Esto es un ejemplo de error (bug).

!!! quote
	Esto es un ejemplo de cita (quote, cite).

### Details

Para crear bloques colapsables que puedan ocultar su contenido.

Ejemplo:
```` markdown
??? "Bloque cerrado. Abreme !!!"
    Ahora lo has abierto.
````
Resultado:
??? "Bloque cerrado. Abreme !!!"
    Ahora lo has abierto.

Ejemplo:
```` markdown
???+ "Bloque abierto inicialmente"

    ??? "Bloque dentro de otro bloque"
        Algo de contenido.
````
Resultado:
???+ "Bloque abierto inicialmente"

    ??? "Bloque dentro de otro bloque"
        Algo de contenido.

Ejemplo:
```` markdown
??? danger "Bloque con tema de peligro"
    Algo de contenido.
````
Resultado:
??? danger "Bloque con tema de peligro"
    Algo de contenido.

??? warning "Bloque con tema de precaución"
    Algo de contenido.

??? success "Bloque con tema de éxito"
    Algo de contenido.

### CodeHilite

Extensión incluida en la librería estándar de Markdown que permite resaltar la sintaxis de los bloques de código. Como lenguajes soportados están entre otros: markdown, python, c, cpp, csharp, html, javascript, JSON, XML.

Ejemplo utilizando comillas simples. 

```` markdown
``` python
import tensorflow as tf
```
````

Resultado:

``` python
import tensorflow as tf
```

Ejemplo utilizando bloque tabulado con cuatro espacios:

```` markdown
    :::python
    """ Bubble sort """
    def bubble_sort(items):
        for i in range(len(items)):
            for j in range(len(items) - 1 - i):
                if items[j] > items[j + 1]:
                    items[j], items[j + 1] = items[j + 1], items[j]
````

Resultado:

    :::python
    """ Bubble sort """
    def bubble_sort(items):
        for i in range(len(items)):
            for j in range(len(items) - 1 - i):
                if items[j] > items[j + 1]:
                    items[j], items[j + 1] = items[j + 1], items[j]

Ejemplo utilizando bloque tabulado y números de línea:

```` markdown
    #!python
    """ Bubble sort """
    def bubble_sort(items):
        for i in range(len(items)):
            for j in range(len(items) - 1 - i):
                if items[j] > items[j + 1]:
                    items[j], items[j + 1] = items[j + 1], items[j]
````

Resultado:

    #!python
    """ Bubble sort """
    def bubble_sort(items):
        for i in range(len(items)):
            for j in range(len(items) - 1 - i):
                if items[j] > items[j + 1]:
                    items[j], items[j + 1] = items[j + 1], items[j]

Es posible resaltar líneas concretas de código con hl_lines.

```` markdown
    #!python hl_lines="3 4"
````

Resultado:

    #!python hl_lines="3 4"
    """ Bubble sort """
    def bubble_sort(items):
        for i in range(len(items)):
            for j in range(len(items) - 1 - i):
                if items[j] > items[j + 1]:
                    items[j], items[j + 1] = items[j + 1], items[j]

### InlineHilite

Permite embeber código en el texto mediante ` #!languaje code` o bien ` :::languaje code` entre comillas simples inversas.

Ejemplo:
```` markdown
Aqui se presenta este código `#!c #include <stdio.h>` embebido en el texto.
````
Resultado:

Aqui se presenta este código `#!c #include <stdio.h>` embebido en el texto.

Ejemplo:
```` markdown
Aqui se presenta este otro código `:::c #include <stdlib.h>` embebido en el texto.
````
Resultado:

Aqui se presenta este otro código `:::c #include <stdlib.h>` embebido en el texto.

Ejemplo:
```` markdown
Código javascript: `#!js function pad(v){return ('0'+v).split('').reverse().splice(0,2).reverse().join('')}`.
````
Resultado:

Código javascript: `#!js function pad(v){return ('0'+v).split('').reverse().splice(0,2).reverse().join('')}`.

### Mark

Permite marcar texto en ==amarillo fosforito==.

La anterior frase se ha generado así:
```` markdown
Permite marcar texto en ==amarillo fosforito==.
````

### Footnotes

Otra extensión de la libreria estándar para incluir notas al pie de página. Se inserta una referencia en el texto, la cual puede ser definida en cualquier parte del documento. La definición aparecerá en el pie de página. La referencia consiste en un sombrerete seguido de un identificador numérico [1, 2, 3, ...] o bien de nombres [Cuartas et al. 2012].

Ejemplo:

```` markdown
Lorem ipsum[^1] dolor sit amet, consectetur adipiscing elit.[^2]
````

Resultado:

Lorem ipsum[^1] dolor sit amet, consectetur adipiscing elit.[^2]

La definición de los contenidos de la nota al pie puede realizarse en una única línea si el texto es corto:

```` markdown
[^1]: Lorem ipsum dolor sit amet, consectetur adipiscing elit.
````

o bien en un bloque de texto indentado cuatro espacios, que comienze en la siguiente línea de la etiqueta, si el texto es largo.

```` markdown
[^2]:
    Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla et euismod
    nulla. Curabitur feugiat, tortor non consequat finibus, justo purus auctor
    massa, nec semper lorem quam in massa.
````

[^1]: Lorem ipsum dolor sit amet, consectetur adipiscing elit.

[^2]:
    Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla et euismod
    nulla. Curabitur feugiat, tortor non consequat finibus, justo purus auctor
    massa, nec semper lorem quam in massa.

### Arithmatex <small>MathJax</small>

Basado en [MathJax][10]. Permite introducir equaciones escritas en TeX dentro de bloques o en línea con el texto. Ver [este hilo][11] para una rápida referencia sobre la sintaxis TeX.

Ejemplo:
```` markdown
$$\frac{n!}{k!(n-k)!} = \binom{n}{k}$$

$$\sum_{i=0}^n i^2 = \frac{(n^2+n)(2n+1)}{6}$$
````
Resultado:

$$\frac{n!}{k!(n-k)!} = \binom{n}{k}$$

$$\sum_{i=0}^n i^2 = \frac{(n^2+n)(2n+1)}{6}$$

Ejemplo:
```` markdown
Lorem ipsum dolor sit amet: $p(x|y) = \frac{p(y|x)p(x)}{p(y)}$
````

Resultado:

Lorem ipsum dolor sit amet: $p(x|y) = \frac{p(y|x)p(x)}{p(y)}$

#### Letras griegas

`:::markdown $\alpha, \beta, ..., \omega$`

$\alpha, \beta, ..., \omega$

`:::markdown $\Gamma, \Delta, ..., \Omega$`

$\Gamma, \Delta, ..., \Omega$

#### Superindices y subindices

`:::markdown $x_i^2  \log_2 x$`

$x_i^2  \log_2 x$

#### Grupos

Superíndices, subíndices y otras operaciones aplican
solamente al siguiente "grupo". Un "grupo" es un único
símbolo o un cualquier fórmula ubicada entre llaves {...}

`:::markdown $10^10$`

$10^10$

`:::markdown $10^{10}$`

$10^{10}$

`:::markdown ${x^y}^z$`

${x^y}^z$

[10]: https://www.mathjax.org/
[11]: http://meta.math.stackexchange.com/questions/5020/

