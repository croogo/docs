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

Feeds
-----

`$this->Layout->feed()` will output your RSS feed link for your promoted content.

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

If you have your css file placed under `/app/View/Themed/MyTheme/webroot/css/theme.css`::

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

Croogo has a Croogo object in javascript that stores information like the application's base path, etc. This is useful for other javascript related tasks. It can done by calling a single method `$this->Layout->js()`::

    <head>
        <title><?php echo $title_for_layout . ' | ' . Configure::read('Site.title'); ?></title>
        <?php 
            echo $this->Layout->meta();
            echo $this->Layout->feed();
            echo $this->Html->css(array('theme'));
            echo $this->Layout->js();
        ?>
    </head>

CakePHP allows you to load javascript from your views so they go directly inside HEAD. For this, you need to echo out the variable `$scripts_for_layout`.

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

The BODY
========

This is where you output the actual content that is visible in the browser.

Content
-------

The output generated from your view is available in the variable `$content_for_layout`:

::

    <body>
        <div id="content">
            <?php echo $content_for_layout; ?>
        </div>
    </body>

Menu
----

If you want to show a menu with alias main, it is as simple as `$this->Layout->menu('main')`. This will generate a nested unordered list of your main menu:

::

    <body>
        <div id="nav">
            <?php echo $this->Layout->menu('main'); ?>
        </div>

        <div id="content">
            <?php echo $content_for_layout; ?>
        </div>
    </body>


Blocks
------

If you want to show the blocks that belong to right region, just add `$this->Layout->blocks('right')`:

::

    <body>
        <div id="nav">
            <?php echo $this->Layout->menu('main'); ?>
        </div>

        <div id="content">
            <?php echo $content_for_layout; ?>
        </div>

        <div id="sidebar">
            <?php echo $this->Layout->blocks('right'); ?>
        </div>
    </body>

Final code of default.ctp
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
                <?php echo $this->Layout->blocks('right'); ?>
            </div>
        </body>
    </html>

