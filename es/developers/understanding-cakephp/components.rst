Componentes
###########

Lee la documentacion de CakePHP de componentes:
http://book.cakephp.org/2.0/en/controllers/components.html.

Que es un componente?
=====================

Los componentes son paquetes de logica que son compartidos entre controladores. Si te encuentras con la situacion de querer copiar y pegar cosas entre tus controladores, deberias considerar meter esa funcionalidad en un componente.

Codigo
======

Asumiendo que quieres crear el componente Example, este deberia estar en: `/app/Controller/Component/ExampleComponent.php`::

    <?php
    class ExampleComponent extends Component {
    
        public function myMethod() {
            // Tu codigo aqui
        }

    }

Componentes de plugins
----------------------

Si es el compoente del plugin Example, entonces deberia encontrarse en `/app/Plugin/Example/Controller/Component/ExampleComponent.php`.


Usando Componentes en los controladores
=======================================

::

    <?php
    class RecipesController extends AppController {

        public $components = array(
            'Example', // 'Example.Example' Si es el componente del plugin Example
        );

        public function view($id)     {
            // Llamar al metodo del componente
            $this->Example->myMethod();
        }

    }