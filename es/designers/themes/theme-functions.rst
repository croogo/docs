Funciones de plantillas
#######################

Todas las funciones especificas de los temas (en case de ser necesarias) van en el CustomHelper. Si el alias de tu plantilla es MiTema, el CustomHelper debera estar ubicado en  `app/View/Themed/MiTema/Helper/CustomHelper.php`.

::

	<?php
	class CustomHelper extends Helper {

	    public function myCustomMethod() {
	        // code here
	    }

	}

CustomHelper es cargado automaticamente para ser usado de la siguiente manera en tus vistas (archivos .ctp)

    $this->Custom->miMetodoPersonalizado();