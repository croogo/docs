Migraciones
###########

Generar Migraciones
-------------------

Primeramente, necesitaras activar tu plugin en la administracion.

Segundo, necesitaras generar tu schema.php::

	./Console/cake schema generate -p yourPlugin

Debes editar "schema.php" para hacer una limpieza y refactoracion. Como `schema.php` contiene todas las bases de datos de la aplicacion, necesitaras removerlas manualmente antes de incluirla en el schema de tu plugin.

Por ejemplo, la tabla "acos", "aros", "aros_acos" and "i18n" le pertenecen al nucleo de Croogo y deben ser removidas del archivo generado. Ademas las tablas unidas no son agregadas en `schema.php` y tu deberas agregarlas por tu cuenta.

Seguido de esto, deberas crear un archivo de migraciones. Este nombre debe ser unico::

	./Console/cake Migrations.migration generate -p TuPlugin

El archivo de migraciones ha sido creado.

Aplicar Migraciones
-------------------

Es tu responsabilidad aplicar migraciones durante la activacion de tu plugin. Necesitaras crear (si el archivo no existe)
``TuPluginActivation.php`` en tu folder de configuracion: ``app/Plugin/TuPlugin/Config``

En el metodo ``onActivation(&$controller)`` deberas agregar estas 3 lineas
		<?php
		App::uses('CroogoPlugin', 'Extensions.Lib');
		$CroogoPlugin = new CroogoPlugin();
		$CroogoPlugin->migrate('YourPlugin');

Remover Migraciones
-------------------

Si deseas remover todas las migraciones durante la desactivacion deberas tener estas 3 lineas en el metodo ``onDeactivation(&$controller)``::

		<?php
		App::uses('CroogoPlugin', 'Extensions.Lib');
		$CroogoPlugin = new CroogoPlugin();
		$CroogoPlugin->unmigrate('TuPlugin');
