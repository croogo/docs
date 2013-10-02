Layout de base
##############

Appelons notre thème MyTheme, ainsi nous devons placer notre layout par défaut
dans `/app/View/Themed/MyTheme/Layouts/default.ctp`.

Au début, nous avons quelque chose comme ceci::

    <!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
    <html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
        <head>
        </head>

        <body>
        </body>
    </html>

Le HEAD
=======

C'est ici que se trouvent votre titre de page, les informations meta, le css,
le javascript. Croogo a un LayoutHelper pour vous faciliter la vie. Vous
pouvez aussi utiliser mes helpers du coeur de CakePHP pour des tâches plus
générales.

Page title
----------

La variable `$title_for_layout` est définie à partir de votre controller (peut
être fait à partir des vues aussi). Et `Configure::read('Site.title')` est
le titre de votre site web, que vous pouvez définir à partir d'un panneau
admin dans Settings > Site.

::

    <head>
        <title><?php echo $title_for_layout . ' | ' . Configure::read('Site.title'); ?></title>
    </head>

Les balises Meta
----------------

C'est aussi simple que d'appeler une méthode de LayoutHelper.
`$this->Layout->meta()` affiche toutes les balises meta pour votre contenu.

::

    <head>
        <title><?php echo $title_for_layout . ' | ' . Configure::read('Site.title'); ?></title>
        <?php echo $this->Layout->meta(); ?>
    </head>

Feeds
-----

`$this->Layout->feed()` va afficher le lien de votre feed RSS  pour du contenu
promu.

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

Si vous avez votre fichier css placé dans
`/app/View/Themed/MyTheme/webroot/css/theme.css`::

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

Croogo a un objet Croogo dans javascript qui stocke les informations comme
le chemin de base de l'application, etc. C'est utile pour les autres tâches
liés au javascript. Cela peut être fait en appelant une méthode unique
`$this->Layout->js()`::

    <head>
        <title><?php echo $title_for_layout . ' | ' . Configure::read('Site.title'); ?></title>
        <?php 
            echo $this->Layout->meta();
            echo $this->Layout->feed();
            echo $this->Html->css(array('theme'));
            echo $this->Layout->js();
        ?>
    </head>

CakePHP vous permet de charger le javascript à partir de vos vues, ainsi elles
vont directement à l'intérieur du HEAD. Pour ceci, vous avez besoin d'afficher
la variable `$scripts_for_layout`.

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

Le BODY
=======

C'est ici que vous affichez le contenu effectif qui est visible dans le
navigateur.

Content
-------

La sortie générée à partir de votre vue est disponible dans la variable
`$content_for_layout`:

::

    <body>
        <div id="content">
            <?php echo $content_for_layout; ?>
        </div>
    </body>

Menu
----

Si vous voulez montrer un menu avec l'alias main, c'est est aussi simple que
`$this->Layout->menu('main')`. Ce la générer une liste imbriquée non ordonnée
de votre menu main:

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

Si vous voulez montrer les blocks qui appartiennent à la région right, ajoutez
juste `$this->Layout->blocks('right')`:

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

Code final de default.ctp
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

