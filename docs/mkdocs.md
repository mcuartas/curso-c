# Acerca de mkdocs

[mkdocs](http://www.mkdocs.org) es una herramienta para crear documentación.  
Entre sus ventajas destacan las siguientes:

* Permite escribir en lenguaje markdown.
* Es posible utilizar extensiones, por ejemplo, para resaltar en colores código.
* Incluye un servidor web que permite visualizar los cambios según vamos escribiendo.
* Permite crear facilmente un sitio web estático con la documentación generada.

## Instalación

Comprobaremos si tenemos instalado Python y PIP con los siguientes comandos:

	:::bash
	python --version
	pip --version

En caso de no tenerlos instalados, podemos hacerlo instalando [Anaconda](https://anaconda.org/). En caso de tenerlos instalados, actualizaremos pip a la última versión con el siguiente comando:

	:::bash
	pip install --upgrade pip

A continuación ya podemos instalar mkdocs con el siguiente comando:

	:::bash
	pip install mkdocs

Tras la instalación podemos comprobar la versión instalada con:

	:::bash
	mkdocs --version 

En caso de utilizar el tema [material](https://squidfunk.github.io/mkdocs-material/) para mkdocs lo instalaremos de la siguiente forma:

	:::bash
	pip install mkdocs-material

Para utilizar la extensión CodeHilite es necesario instalar pygments:

	:::bash
	pip install pygments

Para utilizar la extensión PyMdown que entre otros paquetes incluye arithmatex (MathJax) es necesario instalarla:

	:::bash
	pip install pymdown-extensions

## Repositorio GIT

### [GitHub](https://github.com)

#### Crear un nuevo repositorio local

Para crear un nuevo respositorio local seleccionaremos una carpeta y crearemos un archivo **README.md** explicativo del proyecto. Luego, desde una consola, escribiremos los siguientes comandos para crear el repositorio local:

	#!bash
	git init
	git add README.md
	git commit -m "first commit"
	git remote add origin https://github.com/mcuartas/curso-c.git
	git push -u origin master

En el caso de que el repositorio local ya exista, solo serán necesarias las dos últimas instrucciones (4 y 5) del código anterior.

### GoDaddy

#### Crear un repositorio remoto

Nos conectamos al servidor donde queremos crear el repositorio con:

	:::bash
	ssh mcuartas@cuartas.es

Creamos un nuevo directorio llamado 'git' y dentro de él otro llamado 'curso-c.git' para alojar el repositorio. Después inicializamos el repositorio:

	:::bash
	mkdir git
	cd git
	mkdir curso-c.git
	cd curso-c.git
	git --bare init

En nuestra copia local, accedemos a la carpeta del proyecto e inicializamos el repositorio local con el siguiente comando:

	:::bash
	git init

Opcionalmente podemos crear un fichero llamado .gitignore para excluir las carpetas que no queremos someter a control de versiones. En este caso su contenido será:

	site/
	c/

Una vez realizado el commit inicial con Visual Studio Code, podemos subir la versión al repositorio remoto con:

	:::bash
	git remote add daddy mcuartas@cuartas.es:/home/mcuartas/git/curso-c.git
	git push daddy master

Para sincronizar localmente con los cambios del respositorio sería:

	:::bash
	git pull daddy master

#### Crear una copia de trabajo local

En primer lugar necesitamos clonar el proyecto, esto lo haremos desde la carpeta donde queremos crear la copia local. En esta carpeta se creará una carpeta llamada curso-c con el proyecto:

	:::bash
	git clone mcuartas@cuartas.es:/home/mcuartas/git/curso-c curso-c

Al clonar el proyecto al servidor remoto se le asigna el nombre 'origin'. Podemos consultarlo con:

	:::bash
	git remote -v

Podemos modificar este nombre y cambiarlo por otro, por ejemplo:

	:::bash
	git remote rename origin daddy

A partir de aquí podemos subir nuevas versiones y/o actualizar nuestra copia local a partir del servidor con los siguientes comandos:

	:::bash
	git push daddy master
	git pull daddy masters

## Comandos

* `mkdocs new [dir-name]` - Create a new project.
* `mkdocs serve` - Start the live-reloading docs server.
* `mkdocs build` - Build the documentation site.
* `mkdocs help` - Print this help message.

## Estructura del proyecto

    mkdocs.yml    	# Fichero de configuración.
    docs/
        index.md  	# La página de inicio.
        mkdocs.md   # Tutorial sobre mkdocs.
        markdown.md # Tutorial sobre markdown.
        about.md    # Informacion acerca del curso.

## Pasos para comenzar la edición

1. 	Abrir una consola DOS
2. 	Teclear:  

		:::bash
		cd Documents/mkdocs/curso-c
		mkdocs serve

3.  Abrir el navegador en http://127.0.0.1:8000/
4.  Comenzar la edición



