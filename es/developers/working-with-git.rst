Trabajando con Git
##################

El repositorio git de Croogo esta hospedado en GitHub. El repositorio contiene el contenido del directorio `app` solamente, asi que necesitaras descargar CakePHP antes de clonarlo.

Una vez que descargues y extraigas el archivo de CakePHP, navega a la carpeta `app` y vacíala. Ahora corre lo siguiente ::

    $ cd app
    $ git init
    $ git remote add origin git://github.com/croogo/croogo.git
    $ git pull origin master
    $ git submodule update --init

Contribuyendo
=============

La mejor manera de contribuir al codigo del nucleo es haciendo un fork al repositorio en GitHub, haciendo cambios y despues enviando un pull request. Para hacerlo:

- Obten una cuenta de GitHub
- Haz un Fork en Croogo
- Entonces tendras un fork en http://github.com/tuusuario/croogo.
- Haz los cambios que requieras, envia un pull request.