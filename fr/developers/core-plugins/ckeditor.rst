Ckeditor
########

Configuration
=============

The `Example` plugin contains a sample code to activate Ckeditor
in `Plugin/Example/Config/bootstrap.php` file::

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

There are three presets: `basic`, `standard`, and `full`.
The above code activates multiple Ckeditor instances with different presets.
The last editor on `ExampleCustom` element shows how to configure the toolbar
with specific buttons, color and language.

Consult Ckeditor documentation for further details.