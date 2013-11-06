Translate
#########

Le plugin Translate est l'un des plugins du coeur qui est fourni avec Croogo.
Si votre website nécessite du contenu dans plusieurs languages (i18n), activez
le juste et vous commencez à traduire à partir de votre panneau admin.

Une fois activé, vous verrz un lien Translate sous la colonne 'Actions' où
les liens Edit et Delete sont présents.

Par défaut, il s'occupe des traductions pour ces models:

- Node
- Block
- Link

Configuration
=============

La configuration pour ceci dans `/app/Plugin/Translate/Config/bootstrap.php`
ressemble à ceci::

    Configure::write('Translate.models', array(
        'Node' => array(
            'title' => 'titleTranslation',
            'excerpt' => 'excerptTranslation',
            'body' => 'bodyTranslation',
        ),
        'Block' => array(
            'title' => 'titleTranslation',
            'body' => 'bodyTranslation',
        ),
        'Link' => array(
            'title' => 'titleTranslation',
            'description' => 'descriptionTranslation',
        ),
    ));

Maintenant si vous voulez que les formulaires de contact soient aussi traduits,
ajoutez juste le nom du model Contact au bootstrap du plugin comme ceci::

    Configure::write('Translate.models', array(
        'Node' => array(
            'title' => 'titleTranslation',
            'excerpt' => 'excerptTranslation',
            'body' => 'bodyTranslation',
        ),
        'Block' => array(
            'title' => 'titleTranslation',
            'body' => 'bodyTranslation',
        ),
        'Link' => array(
            'title' => 'titleTranslation',
            'description' => 'descriptionTranslation',
        ),
        'Contact' => array(
            'title' => 'titleTranslation',
            'body' => 'bodyTranslation',
        ),
    ));
