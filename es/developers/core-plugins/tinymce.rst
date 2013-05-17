TinyMCE
#######

.. versionchanged:: 1.5.1
    TinyMCE no esta incluido por defecto en 1.5.1. Ckeditor es ahora parte del RTE (editor de texto rico) por defecto

TinyMCE es un popular editor WYSIWYG por Moxiecode Systems. Es empacado y enviado como un plugin de Croogo.

Por defecto, el editor carga cuando agregas/editas Nodos en tu panel de administracion. Para cargarlo en otros lugares y tener mas control de sus configuracion, lee la informacion a continuacion.

Configuracion
=============

La configuracion para esto esta en  `/app/Plugin/Tinymce/Config/bootstrap.php` y es la siguiente::

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

Por ejemplo, si quisieras cargar el editor en tu metodo add del controlador Products, en el campo body del modelo Product, agregarias esta linea al final::

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