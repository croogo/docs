Wysiwyg
#######

Wysiwyg est un plugin de wrapper générique pour permettre l'interface et la
configuration d'Editeurs de Texte Riche.

Configuration
=============

Il n'y a pas de configuration nécessaire pour le plugin lui-même. A la place,
vous activez les éditeurs en les activant dans votre propre plugin. Par
exemple, le plugin `Nodes` active les RTEs dans son propre fichier
`Config/bootstrap.php`::

    Croogo::mergeConfig('Wysiwyg.actions', array(
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
