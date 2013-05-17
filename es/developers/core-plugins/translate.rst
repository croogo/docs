Traduccion
##########

El plugin de traduccion es uno de los plugins del nucleo que se envian con Croogo. Si tu sitio requiere el contenido en multiples lenguajes (i18n), solo activalo y empieza a traducir desde tu panel de administracion.

Una vez activo, veras una link de Traducir en la columna de 'Acciones'  donde los vinculos de Editar y Borrar estan presentes.

Por defecto, puede traducir contenido para los siguientes modelos:

- Node
- Block
- Link

Configuracion
=============

La configuracion para esto está en `/app/Plugin/Translate/Config/bootstrap.php` y es la siguiente ::

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

Ahora que si queremos que tus formularios de contacto sean traducidos tambien, entonces agrega el nombre del modelo de Contacto (Contact) en el bootstrap del plugin de la siguiente manera::

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