Ckeditor
########

Configuration
=============

Le plugin `Example` contient un code d'exemple pour activer Ckeditor
dans le fichier `Plugin/Example/Config/bootstrap.php`::

    $Localization = new L10n();
    Croogo::mergeConfig('Wysiwyg.actions', array(
        'Example/admin_rte_example' => array(
            array(
                'elements' => 'ExampleBasic',
                'preset' => 'basic',
            ),
            array(
                'elements' => 'ExampleStandard',
                'preset' => 'standard',
                'language' => 'ja',
            ),
            array(
                'elements' => 'ExampleFull',
                'preset' => 'full',
                'language' => $Localization->map(Configure::read('Site.locale')),
            ),
            array(
                'elements' => 'ExampleCustom',
                'toolbar' => array(
                    array('Format', 'Bold', 'Italic'),
                    array('Copy', 'Paste'),
                ),
            'uiColor' => '#ffe79a',
            'language' => 'fr',
            ),
        ),
    ));

Il y en a trois prédéfinis: `basic`, `standard`, et `full`.
Le code ci-dessus active les multiples instances de Ckeditor avec les différents
prédéfinis.
Le dernier éditeur de l'element `ExampleCustom` montre comment configurer la
barre d'outils avec des boutons spécifiques, la couleur et le language.

Consultez la documentation de Ckeditor pour plus de détails.
