Components
##########

Lire la doc de CakePHP sur les Components:
http://book.cakephp.org/2.0/en/controllers/components.html.

Qu'est-ce qu'un Component?
==========================

Les Components sont des packages de logique qui sont partagés entre les
controllers. Si vous trouvez vous-même que vous copiez et collez des choses
entre les controllers, vous devriez considérer d'emballer quelques
fonctionnalités dans un component.

Code
====

En admettant que vous vouliez créer un component Example, il sera trouvé dans
`/app/Controller/Component/ExampleComponent.php`::

    <?php
    class ExampleComponent extends Component {
    
        public function myMethod() {
            // your code here
        }

    }

Components de Plugin
--------------------

Si un component du plugin Example, il sera trouvé dans
`/app/Plugin/Example/Controller/Component/ExampleComponent.php`.

Utilisation de Components dans les Controllers
==============================================

::

    <?php
    class RecipesController extends AppController {

        public $components = array(
            'Example', // 'Example.Example' if it is from Example plugin
        );

        public function view($id)     {
            // call component method
            $this->Example->myMethod();
        }

    }
