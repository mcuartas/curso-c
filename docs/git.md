# Repositorio GIT

Algunas notas para recordar como crear o clonar repositorios GIT.

## [GitHub](https://github.com)

### Crear un nuevo repositorio local y subirlo a GitHub

Para crear un nuevo respositorio local seleccionaremos una carpeta y crearemos un archivo **README.md** explicativo del proyecto. Luego, desde una consola, escribiremos los siguientes comandos para crear el repositorio local:

	#!bash
	git init
	git add .
	git commit -m "first commit"
	git remote add origin https://github.com/mcuartas/curso-c.git
	git push -u origin master

En el caso de que el repositorio local ya exista, solo serán necesarias las dos últimas instrucciones (4 y 5) del código anterior.

## GoDaddy

### Crear un repositorio remoto

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

### Crear un repositorio local

En nuestra copia local, accedemos a la carpeta del proyecto e inicializamos el repositorio local con el siguiente comando:

	:::bash
	git init

Opcionalmente podemos crear un fichero llamado .gitignore para excluir las carpetas que no queremos someter a control de versiones. En este caso su contenido será:

	site/
	c/

Realizamos el commit inicial con los siguientes comandos:

	:::bash
	git add .
	git commit -m "initial commit"

A continuación, podemos subir la versión al repositorio remoto con:

	:::bash
	git remote add daddy mcuartas@cuartas.es:/home/mcuartas/git/curso-c.git
	git push daddy master

Para sincronizar localmente con los cambios del respositorio sería:

	:::bash
	git pull daddy master

### Crear una copia de trabajo local en otro equipo

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
	git pull daddy master

## Consolidar una nueva versión

Para consolidar una nueva versión en el repositorio, nos situamos en el directorio de trabajo y ejecutamos desde la línea de comandos:

	:::bash
	git add .
	git commit -m "nombre de la version"
	git push origin master

!!! note ""
	Es posible que sea necesario sustituir **origin** por el nombre que le hemos dado al repositorio remoto.

Luego podemos generar el sitio estático con:

	:::bash
	mkdocs build

Por último, subimos la nueva versión a la web mediante FileZilla o similar copiando el directorio.