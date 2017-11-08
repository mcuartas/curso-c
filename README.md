# Curso C

Notas sobre el curso de programación en C.

## Acerca de mkdocs

[mkdocs](http://www.mkdocs.org) es una herramienta para crear documentación.  
Entre sus ventajas destacan las siguientes:

* Permite escribir en lenguaje markdown.
* Es posible utilizar extensiones, por ejemplo, para resaltar en colores código.
* Incluye un servidor web que permite visualizar los cambios según vamos escribiendo.
* Permite crear facilmente un sitio web estático con la documentación generada.

### Instalación

Comprobaremos si tenemos instalado Python y PIP con los siguientes comandos:

	python --version
	pip --version

En caso de no tenerlos instalados, podemos hacerlo instalando [Anaconda](https://anaconda.org/). En caso de tenerlos instalados, actualizaremos pip a la última versión con el siguiente comando:

	pip install --upgrade pip

A continuación ya podemos instalar mkdocs con el siguiente comando:

	pip install mkdocs

Tras la instalación podemos comprobar la versión instalada con:

	mkdocs --version 

En caso de utilizar el tema [material](https://squidfunk.github.io/mkdocs-material/) para mkdocs lo instalaremos de la siguiente forma:

	pip install mkdocs-material

Para utilizar la extensión CodeHilite es necesario instalar pygments:

	pip install pygments

Para utilizar la extensión PyMdown que entre otros paquetes incluye arithmatex (MathJax) es necesario instalarla:

	pip install pymdown-extensions

### Comandos

* `mkdocs new [dir-name]` - Create a new project.
* `mkdocs serve` - Start the live-reloading docs server.
* `mkdocs build` - Build the documentation site.
* `mkdocs help` - Print this help message.

### Pasos para comenzar la edición

1. 	Abrir una consola DOS
2. 	Teclear:  

		cd Documents/mkdocs/curso-c
		mkdocs serve

3.  Abrir el navegador en http://127.0.0.1:8000/
4.  Comenzar la edición