Consolas
########

Croogo ahora tiene la habilidad de instalar y activar extensiones desde la linea de comandos. Para acceder a las consolas cd en tu carpeta `app` y corre los comandos usando: `./Console/cake [shell]`.


Instalar Consola
================

La mayoria de las extensiones que encontraras estan en Github.com. Para instalar el plugin de Megamenu desde github teclea::

    $ ./Console/cake install plugin https://github.com/rchavik/megamenu

O::

    $ ./Console/cake install plugin rchavik megamenu

Las plantillas tambien pueden ser instaladas de la misma manera::

    $ ./Console/cake install theme https://github.com/fahad19/themes

Si tienes un archivo ZIP ubicado en algun lugar, teclea::

    $ ./Console/cake install theme http://example.com/mytheme.zip

Consola Ext
===========

Puedes activar/desactivar plugins y plantillas desde la consola. Para activar la extension de Megamenu previamente installada::

    $ ./Console/cake ext activate plugin Megamenu

Para desactivar::

    $ ./Console/cake ext deactivate plugin Megamenu

Consola de configuraciones
==========================

El plugin de configuraciones provee unas pocas comandos utiles para manipular los valores de configuracion:

- Leer una configuracion::

    $ ./Console/cake settings.settings read Site.title

- Escribir un valor de configuracion::

    $ ./Console/cake settings.settings write Site.title "My Awesome Site"

- Borrar un valor de configuracion::

    $ ./Console/cake settings.settings delete Custom.settingValue

- Actualizar informacion de version despues de una actualizacion::

    $ ./Console/cake settings.settings upgrade_version_info

Consola de usuarios
===================

Puedes reinicializar un password de usuario desde la consola::

    $ ./Console/cake users.users reset admin password
