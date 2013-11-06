TinyMCE
#######

.. versionchanged:: 1.5.1
    TinyMCE n'est pas inclu dans 1.5.1. Ckeditor est maintenant le RTE par
    défaut.

TinyMCE est un éditeur WYSIWYG populaire de Moxiecode Systems. Il est packagé
et distribué en plugin avec Croogo.

Par défaut, l'éditeur se charge quand vous ajoutez/modifiez les Nodes dans votre
panneau admin. Pour le charger à d'autres endroits et avoir plus de contrôle
sur ses configurations, regardez les informations de configuration ci-dessous.

Configuration
=============

La configuration se trouve dans `/app/Plugin/Tinymce/Config/bootstrap.php` et
ressemble à ceci::

    Configure::write('Tinymce.actions', array(
        'Nodes/admin_add' => array(
            array(
                'elements' => 'NodeBody',
            ),
        ),
        'Nodes/admin_edit' => array(
            array(
                'elements' => 'NodeBody',
            ),
        ),
        'Translate/admin_edit' => array(
            array(
                'elements' => 'NodeBody',
            ),
        ),
    ));

Par exemple, si vous souhaitez charger l'éditeur dans la méthode add du champ
body du model Product de votre controller Products, ajoutez cette ligne à la
fin::

    Configure::write('Tinymce.actions', array(
        'Nodes/admin_add' => array(
            array(
                'elements' => 'NodeBody',
            ),
        ),
        'Nodes/admin_edit' => array(
            array(
                'elements' => 'NodeBody',
            ),
        ),
        'Translate/admin_edit' => array(
            array(
                'elements' => 'NodeBody',
            ),
        ),
        'Products/add' => array(
            array(
                'elements' => 'ProductBody',
            ),
        ),
    ));
