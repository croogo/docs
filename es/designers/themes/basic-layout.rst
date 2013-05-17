Distribucion Basica
###################

Llamaremos a nuestra plantilla "MiTema", asi que pondremos nuestra distribucion basica en:

`/app/View/Themed/MiTema/Layouts/default.ctp`.

Al principio, podemos tener algo asi:

    <!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
    <html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
        <head>
        </head>

        <body>
        </body>
    </html>

La seccion HEAD
===============

Aqui es donde el titulo de tu pagina, la informacion Meta, css y javascript son mostrados. Croogo tiene un LayoutHelper para hacer las cosas mas faciles para ti. Puedes usar tambien los helpers del nucleo de CakePHP para tareas mas generales.

Titulo de pagina
----------------

La variable `$title_for_layout` es definida desde tu controlador (puede ser declarada en las vistas tambien). Y `Configure::read('Site.title')` es el titulo de tu pagina que puedes definir en el panel de administracion dentro de Configuraciones > Sitio.

::

    <head>
        <title><?php echo $title_for_layout . ' | ' . Configure::read('Site.title'); ?></title>
    </head>

Etiquetas Meta
--------------

Esto se hace con una llamada simple al metodo del LayourHelper `$this->Layout->meta()`, este regresa todas las etiquetas meta de tu contenido.

::

    <head>
        <title><?php echo $title_for_layout . ' | ' . Configure::read('Site.title'); ?></title>
        <?php echo $this->Layout->meta(); ?>
    </head>

Fuentes web
-----------

`$this->Layout->feed()` dara como salida una fuente RSS a tu contenido promovido

::

    <head>
        <title><?php echo $title_for_layout . ' | ' . Configure::read('Site.title'); ?></title>
        <?php 
            echo $this->Layout->meta();
            echo $this->Layout->feed();
        ?>
    </head>

CSS
---

Si tienes tus archivos CSS ubicados en `/app/View/Themed/MyTheme/webroot/css/theme.css`::

    <head>
        <title><?php echo $title_for_layout . ' | ' . Configure::read('Site.title'); ?></title>
        <?php 
            echo $this->Layout->meta();
            echo $this->Layout->feed();
            echo $this->Html->css(array('theme'));
        ?>
    </head>

Javascript
----------

Croogo tiene un objeto Croogo en javascript que almacena informacion como la ruta base de la aplicacion, etc. Esto es util cuando tienes tareas relacionadas con Javascript para completar. Se puede lograr llamando al metodo `$this->Layout->js()`::

    <head>
        <title><?php echo $title_for_layout . ' | ' . Configure::read('Site.title'); ?></title>
        <?php 
            echo $this->Layout->meta();
            echo $this->Layout->feed();
            echo $this->Html->css(array('theme'));
            echo $this->Layout->js();
        ?>
    </head>

CakePHP permite cargar javascript desde tus vistas para que puedan ir directamente a HEAD. Para hacer esto necesitaras hacer echo a la variable `$scripts_for_layout`.

::

    <head>
        <title><?php echo $title_for_layout . ' | ' . Configure::read('Site.title'); ?></title>
        <?php 
            echo $this->Layout->meta();
            echo $this->Layout->feed();
            echo $this->Html->css(array('theme'));
            echo $this->Layout->js();
            echo $scripts_for_layout;
        ?>
    </head>

La etiqueta BODY
================

Aqui es donde vas a dar salida al contenido que es visible para el navegador.

Contenido
---------

La salida generada por tus vistas esta disponible en la varible `$content_for_layout`:

::

    <body>
        <div id="content">
            <?php echo $content_for_layout; ?>
        </div>
    </body>

Menu
----

Si quieres mostrar un menu con el alias 'main', es tan simple como llamar a `$this->Layout->menu('main')`. Esto generara una lista anidada no ordenada de tu menu main:

::

    <body>
        <div id="nav">
            <?php echo $this->Layout->menu('main'); ?>
        </div>

        <div id="content">
            <?php echo $content_for_layout; ?>
        </div>
    </body>


Bloques
-------

Si quieres mostrar los bloques que le pertenecen a la region 'derecha', solo agrega `$this->Layout->blocks('derecha')`:

::

    <body>
        <div id="nav">
            <?php echo $this->Layout->menu('main'); ?>
        </div>

        <div id="content">
            <?php echo $content_for_layout; ?>
        </div>

        <div id="sidebar">
            <?php echo $this->Layout->blocks('derecha'); ?>
        </div>
    </body>


Codigo final de default.ctp
=========================

::

    <!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
    <html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
        <head>
            <title><?php echo $title_for_layout . ' | ' . Configure::read('Site.title'); ?></title>
            <?php 
                echo $this->Layout->meta();
                echo $this->Layout->feed();
                echo $this->Html->css(array('theme'));
                echo $this->Layout->js();
                echo $scripts_for_layout;
            ?>
        </head>

        <body>
            <div id="nav">
                <?php echo $this->Layout->menu('main'); ?>
            </div>

            <div id="content">
                <?php echo $content_for_layout; ?>
            </div>

            <div id="sidebar">
                <?php echo $this->Layout->blocks('derecha'); ?>
            </div>
        </body>
    </html>

