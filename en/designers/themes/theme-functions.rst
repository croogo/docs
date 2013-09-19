Theme functions
###############

All theme specific functions (if you need any) go to CustomHelper. If your theme alias is MyTheme, your CustomHelper should be placed in `app/View/Themed/MyTheme/Helper/CustomHelper.php`::

	<?php
	class CustomHelper extends Helper {

	    public function myCustomMethod() {
	        // code here
	    }

	}
	?>

CustomHelper is automatically loaded, so you can use it like this your views (.ctp files)::
	
	<?php
	$this->Custom->myCustomMethod();