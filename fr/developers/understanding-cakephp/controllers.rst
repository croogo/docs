Controllers
###########

Lire la doc de CakePHP sur les Controllers:
http://book.cakephp.org/2.0/en/controllers.html.

Qu'est-ce qu'un Controller?
===========================

Un controller est utilisé pour gérer la logique pour une partie de votre
application. La plus couramment, les controllers sont utilisés pour gérer la
logique pour un model unique. Par exemple, si vous construisez un site pour une
boulangerie en ligne, vous voudrez avoir un RecipesController et un
IngredientsController gérant vos recipes et leurs ingredients. Dans CakePHP,
controllers sont appelés d'après le model qu'ils gèrent, à la forme plurielle.

Le model Recipe est géré par le RecipesController, le model Product est géré
par ProductsController, et ainsi de suite.

Les controllers de votre application sont des classes qui étendent la classe
AppController de CakePHP, qui à son tour étend une classe Controller du coeur,
qui est une partie de la librairie de CakePHP. La classe AppController peut
être définie dans `/app/Controller/AppController.php` et elle devrait contenir
les méthodes qui sont partagées entre tous les controllers de votre application.

Les Controllers peuvent inclure un certain nombre de méthodes qui se référent
couramment aux actions. Les actions sont les méthodes du Controller utilisées
pour afficher les views. Une action et une méthode unique d'un controller.

Le dispatcher de CakePHP appelle les actions quanf une requête entrante
matche une URL à une action d'un controller (réferrez-vous à la "Configuration
des Routes" pour une explication sur la façon dont les actions du controller
et les paramètres sont mappés à partir de l'URL).

Code
====

En retournant à notre exemple de boulangerie en ligne, notre RecipesController
pourrait contenir les actions view(), share(), et search(). Le controller
serait trouvé dans /app/Controller/RecipesController.php::

    <?php
    class RecipesController extends AppController {
    
        public function view($id)     {
            //action logic goes here..
        }

        public function share($customer_id, $recipe_id) {
            //action logic goes here..
        }
    
        public function search($query) {
            //action logic goes here..
        }
    
    }


Les Controllers du Plugin
-------------------------

Si c'est un controller du plugin Recipes, il sera trouvé dans
`/app/Plugin/Recipe/Controller/RecipesController.php`.

Comment le voir en action?
==========================

Les Controllers peuvent être accessibles à partir du navigateur à l'adresse
yoursite.com/controller_name/action_name. Mais il va maintenant montrer des
erreurs, et nécessitera aussi de créer des models et views pour celui-ci.
