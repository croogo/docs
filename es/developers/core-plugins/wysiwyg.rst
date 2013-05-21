Wysiwyg
#######

Wysiwyg es un wrapper plugin generico para permitir la interfaz y configurado de Editores de Texto Rico.

Configuracion
=============

No hay configuracion que se requiera en el plugin. En vez de eso, debes activar los editores.. activandolos en su propio plugin. 
Por ejemplo el plugin de nodos `Nodes` activa los RTE (editores de texto rico) en su propio archivo `Config/bootstrap.php` ::

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