Modelos
#######

Lee la documentacion de CakePHP de Modelos:
http://book.cakephp.org/2.0/en/models.html.

Que es un modelo?
=================

Los modelos representan la informacion y son usados en las aplicaciones de CakePHP para accesar a la informacion. Un Modelo usualmente representa una tabla de base de datos pero tambien para accesar cualquier cosa que almacene informacion como archivos, registros LDAP, eventos de iCal o filas de un archivo CSV.

Un modelo puede ser asociado con otros modelos. Por ejemplo, una Receta puede estar asociada con el Autor de esa receta como tambien con los Ingredientes de la receta.
Codigo

Si tienes una tabla llamada 'recipes' (con columnas id, title, body), el modelo deberia llamarse Recipe y estar en  `/app/Model/Recipe.php`::

    <?php
    class Recipe extends AppModel {

    }


Modelo de Plugins
-----------------

Si es el modelo del plugin de Recipes, entonces estaria en:

`/app/Plugin/Recipes/Model/Recipe.php`.


Usando modelos en Controladores
==============================

::

    <?php
    class RecipesController extends AppController {

        public $uses = array(
            'Recipe', // 'Recipes.Recipe' Si es parte del plugin Recipes
        );

        public function view($id) {
            // Obtener el record con ID 123 de la tabla de recetasretrieve record with ID 123 from recipes            $recipe = $this->Recipe->findById(123);

	    // Establecer la variable $recipe para que pueda ser accesada despues por una vista
            $this->set('recipe', $recipe); // or $this->set(compact('recipe'));
        }

    }