Wysiwyg
#######

Wysiwyg is a generic wrapper plugin to allow interfacing and setup or
web Rich Text Editors.

Configuration
=============

There is no configuration required on the plugin itself. Instead, you enable
editors by activating it in your own plugin.  For example, the `Nodes` plugin
activate the RTEs in its own `Config/bootstrap.php` file::

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