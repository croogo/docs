Controladores
#############

Lee la documentacion de CakePHP en los Controladores:
http://book.cakephp.org/2.0/en/controllers.html.

Que es un controlador?
======================

Un controlador es usado para manejar la parte logica de tu aplicacion. Mas comunmente, los controladores son usados para manejar la logica de un modelo individual. Por ejemplo, si fueras a construir un sitio para una panaderia en linea, deberias tener un controlador de recetas (RecipesController) y un controlador de ingredientes (IngredientController) administrando las recetas y sus ingredientes. En CakePHP, los controladores son nombrados en base al modelo que manejan, en forma plural.

El modelo Recipe (receta) es manejado por el controlador RecipesController (Controlador de recetas), el modelo Product es manejado por el controlador ProductsController y asi sucesivamente.

Los controladores de tu aplicacion son clases que extienden la clase de CakePHP llamada AppController, que a su vez extiende una clase controlador nucleo. que a su vez es parte de la bilbioteca CakePHP. La clase AppController puede ser definida en `/app/Controller/AppController.php` y debera contener ciertos metodos que son compartidos por todos los controladores de tu aplicacion.

Los controladores pueden incluir cualquier numero de metodos que son usualmente referenciados como acciones. Las acciones con los metodos del controlador para mostrar vistas. Una accion es un metodo individual de un controlador.

El despachador de CakePHP llama a las acciones cuando una url de una peticion entrante concuerda con una accion de un controlador (busque "Configuracion de rutas" para una explicacion de como las acciones y parametros de un controlador son mapeados desde una URL).

Codigo
======

Regresemos a nuestro ejemplo de la panaderia en linea. Nuestro controlador de recetas (RecipeController) puede contener las acciones view(), share(), y search() (ver, compartir y buscar respectivamente). El controlador se deberia encontrar en  /app/Controller/RecipesController.php::

    <?php
    class RecipesController extends AppController {
    
        public function view($id)     {
            //La logica de la accion va aqui
        }

        public function share($customer_id, $recipe_id) {
            //La logica de la accion va aqui
        }
    
        public function search($query) {
            //La logica de la accion va aqui
        }
    
    }

Controladores de plugins
------------------------

Si es el controlador del plugin Recipes (recetas), entonces deberia encontrarse en: `/app/Plugin/Recipe/Controller/RecipesController.php`.


Como verlo en accion?
=====================

Los controladores pueden ser accesados desde tu navegador en la direccion tusitio.com/nombre_controlador/nombre_accion. Pero mostrara errores justo ahora y requerira crear modelos y vistas para el tambien.