Migrations
##########

Generate Migrations
-------------------

Firstly, you need to activate your plugin in the administration

Secondly, you need to generate your schema.php::

		./Console/cake schema generate -p yourPlugin

You must edit "schema.php" for some cleanup and refactoring. Since `schema.php`
contains all existing tables in the application, you will need to remove them
manually before including it in your plugin schema.  For example, table "acos", "aros", "aros_acos" and "i18n" belongs to Croogo core and must be removed from
the generated file. Moreover join tables aren't added in `schema.php` and you 
must add them by yourself.

Next, you must create your migrations file. Its name must be unique::

		./Console/cake Migrations.migration generate -p yourPlugin

Your migrations file is now created!

Apply Migrations
----------------

It's your responsibility to apply migrations during activation of your plugin.
You need to create (if the file doesn't exist) ``YourPluginActivation.php`` in your Config folder: ``app/Plugin/YourPlugin/Config``

In the method ``onActivation(&$controller)`` you must add this 3 lines::

		<?php
		App::uses('CroogoPlugin', 'Extensions.Lib');
		$CroogoPlugin = new CroogoPlugin();
		$CroogoPlugin->migrate('YourPlugin');

Remove Migrations
-----------------

If you want to remove all migrations during the deactivation you just need this 3 lines in method ``onDeactivation(&$controller)``::

		<?php
		App::uses('CroogoPlugin', 'Extensions.Lib');
		$CroogoPlugin = new CroogoPlugin();
		$CroogoPlugin->unmigrate('YourPlugin');
