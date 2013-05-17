Bootstrap
#########

Los plugins tienen su propio bootstrat. Si tienes un plugin llamado Example, entonces tendra su archivo en `app/Plugin/Example/Config/bootstrap.php`. Este archivo es requerido por todos los plugins y es cargado (siempre que este activo) cada vez que la aplicacion arranca.

Esto es util para guardar configuracion basica como::

    Configure::write('NombrePlugin.mi_configuracion', 'algun valor');

Despues puede ser accesada donde sea por la aplicacion de la siguiente manera::

    $myVar = Configure::read('NombrePlugin.mi_configuracion');