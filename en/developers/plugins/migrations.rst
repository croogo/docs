Migrations
##########

Generate Migrations :
---------------------

Firstly you need to activate your plugin in the administration

After you need to generate your schema.php

	cake Schema generate -p yourPlugin

You must edit "schema.php" for somes refactoring. Indeed schema.php contains too many informations, and table "acos", "aros", "aros_acos" and "i18n" must be removed. Moreover join tables aren't added in schema.php and you must add them by yourself.
After you must create your migrations file. It's name must be unique

	cake Migrations.migration generate -p yourPlugin

That's all, your migrations file is created !

Apply Migrations :
------------------

It's your responsabilities to apply migrations during activation of your plugin.
You need to create (if the file doesn't exist) YourPluginExample.php in your Config folder

	"app/Plugin/YourPlugin/Config"

In the method "onActivation(&$controller)" you must add this 3 lines

	App::uses('CroogoPlugin', 'Extensions.Lib');
	$CroogoPlugin = new CroogoPlugin();
	$CroogoPlugin->migrate('YourPlugin');`

Remove Migrations :
-------------------

If you want to remove all migrations during the deactivation you just need this 3 lines in method "onDeactivation(&$controller)"

	App::uses('CroogoPlugin', 'Extensions.Lib');
	$CroogoPlugin = new CroogoPlugin();
	$CroogoPlugin->unmigrate('YourPlugin');
