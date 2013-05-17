Ckeditor
########

Configuracion
=============

El plugin `Example` contiene una muestra de como activar el Ckeditoren  el archivo `Plugin/Example/Config/bootstrap.php` ::

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

Hay 3 preconfiguraciones: `basic`, `standard`, and `full`.
Lo anterior activa diferentes instanacias del Ckeditor con diferentes preconfiguraciones.
El ultimo editor en el elemento `ExampleCustom` muestra como configurar una barra de herramientas con botones especificos, color y lenguage.

Revisa la documentacion de Ckeditor para mas detalles.