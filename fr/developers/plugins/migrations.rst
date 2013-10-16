Migrations
##########

Générer des Migrations
----------------------

Premièrement, vous aurez besoin d'activer votre plugin dans l'administration

Deuxièmement, vous aurez besoin de générer votre schema.php::

		./Console/cake schema generate -p yourPlugin

Vous devez éditer "schema.php" pour un peu de nettoyage et de refactoring.
Puisque `schema.php` contient toutes les tables existantes de l'application,
vous devrez les retirer manuellement avant de l'inclure dans votre schema de
plugin. Par exemple, les tables "acos", "aros", "aros_acos" et "i18n"
appartiennent au coeur de Croogo et doivent être retirées du fichier généré.
De plus, les tables jointes ne sont pas ajoutées dans `schema.php` et vous
devez les ajouter vous-même.

Ensuite, vous devez créer votre fichier de migrations. Son nom doit être
unique::

		./Console/cake Migrations.migration generate -p yourPlugin

Votre fichier de migrations est maintentant créé!

Appliquer les Migrations
------------------------

Il est de votre responsabilité d'appliquer les migrations pendant l'activation
de votre plugin. Vous devez créer (si le fichiern'existe pas)
``YourPluginActivation.php`` dans votre dossier Config:
``app/Plugin/YourPlugin/Config``

Dans la méthode ``onActivation(&$controller)``, vous devez ajouter ces 3
lignes::

		<?php
		App::uses('CroogoPlugin', 'Extensions.Lib');
		$CroogoPlugin = new CroogoPlugin();
		$CroogoPlugin->migrate('YourPlugin');

Retirer les Migrations
----------------------

Si vous voulez retirer toutes les migrations pendant la désactivation, vous
avez juste besoin de ces 3 lignes dans la méthode
``onDeactivation(&$controller)``::

		<?php
		App::uses('CroogoPlugin', 'Extensions.Lib');
		$CroogoPlugin = new CroogoPlugin();
		$CroogoPlugin->unmigrate('YourPlugin');
