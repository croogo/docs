Bootstrap
#########

Les Plugins peuvent avoir leur propre bootstrap. Si vous avez un plugin nommé
Example, vous aurez un fichier dans `app/Plugin/Example/Config/bootstrap.php`.
Ce fichier est nécessaire pour tous les plugins et sera chargé (si actif) à
chaque fois que l'application utilise les bootstraps.

C'est utile pour stocker l'information de configuration basique::

    Configure::write('PluginName.my_setting_key', 'value here');

Ensuite il est accesible depuis n'importe où dans l'application en faisant::

    $myVar = Configure::read('PluginName.my_setting_key');
