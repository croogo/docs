Models
######

Lire la doc de CakePHP sur les Models:
http://book.cakephp.org/2.0/en/models.html.

Qu'est-ce qu'un Model?
======================

Les Models représentent les données et sont utilisés dans les applications
CakePHP pour accéder aux données. Un model représente couramment une table
de base de données mais peut aussi être utilisé pour accéder à tout ce qui
stocke des données comme les fichiers, les enregistrements LDAP, les events
iCal ou les lignes dans un fichier CSV.

Un model peut être associé avec d'autres models. Par exemple, une Recipe peut
être associée avec l'Author de la recipe ainsi que l'Ingredient dans la recipe.
Code

Si vous avez une table nommée 'recipes' (avec les colonnes id, title, body), le
nom du model serait Recipe et trouvé dans `/app/Model/Recipe.php`::

    <?php
    class Recipe extends AppModel {

    }

Les Models du Plugin
--------------------

Si c'est un model du plugin Recipes, il sera trouvé dans
`/app/Plugin/Recipes/Model/Recipe.php`.

Utilisation des Models dans les Controllers
===========================================

::

    <?php
    class RecipesController extends AppController {

        public $uses = array(
            'Recipe', // 'Recipes.Recipe' if it is from Recipes plugin
        );

        public function view($id) {
            // retrieve record with ID 123 from recipes table
            $recipe = $this->Recipe->findById(123);

            // set the $recipe variable so it can be used by views later
            $this->set('recipe', $recipe); // or $this->set(compact('recipe'));
        }

    }
