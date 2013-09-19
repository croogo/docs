Fonctions de thème
##################

Toutes les fonctions de thème sont des fonctions spécifiques (si vous en avez
besoin) se trouvant dans CustomHelper. Si l'alias de votre thème est MyTheme,
votre CustomHelper devra être placé dans
`app/View/Themed/MyTheme/Helper/CustomHelper.php`::

	<?php
	class CustomHelper extends Helper {

	    public function myCustomMethod() {
	        // code ici
	    }

	}
	?>

CustomHelper est automatiquement chargé, ainsi vous pouvez l'utiliser comme
ceci dans vos vues (.ctp files)::

	<?php
	$this->Custom->myCustomMethod();