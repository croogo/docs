Auxiliares (helpers)
####################

Lee la documentacion de CakePHP de los auxiliar (helper):
http://book.cakephp.org/2.0/en/views/helpers.html.

Que es un auxiliar (helper)?
============================

Los auxiliares son clases similares a los componentes para la capa de presentacion de tu aplicacion. Contienen la logica de presentacion que es compartida entre distintas vistas, elementos y distribucion. En este capitulo mostraremos como crear tus propios auxiliares (helpers), y delinear las tareas basicas que los auxiliares del nucleo de CakePHP te pueden ayudar a lograr.

Codigo
======

Digamos que le ponemos Example a nuestro auxiliar, y puede ser encontrado en `/app/View/Helper/ExampleHelper.php`::

    <?php
    class ExampleHelper extends AppHelper {

        public function lowercase($text) {
            return strtolower($text);
        }

    }

Auxiliares de plugins
---------------------

Si es el auxiliar del plugin Example, entonces estaria encontrado en `/app/Plugin/Example/View/Helper/ExampleHelper.php`.

Usando auxiliares en las vistas
===============================

Antes de usar auxiliares en las vistas, debemos hacerle saber a nuestro controlador que debe cargarlo::

    <?php
    class RecipesController extends AppController {

        public $uses = array(
            'Recipe',
        );

        public $helpers = array(
            'Example', // 'Example.Example' si es el auxiliar del plugin Example
        );

        public function view($id) {
            $recipe = $this->Recipe->findById($id);
            $this->set('recipe', $recipe);
        }

    }

Ahora en nuestra vista podemos usar el auxiliar en /app/View/Recipes/view.ctp::

    <div class="recipes view">
        <h2><?php echo $recipe['Recipe']['title']; ?></h2>

        <p><?php echo $recipe['Recipe']['body']; ?></p>

        <p><?php echo $this->Example->lowercase('ESTE TEXTO SERA CONVERTIDO EN MINUSCULAS'); ?></p>
    </div>