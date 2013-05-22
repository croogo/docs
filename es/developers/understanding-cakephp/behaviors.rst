Comportamientos
###############

Lee la documentacion de CakePHP de Comportamientos (Behaviors) en: http://book.cakephp.org/2.0/en/models/behaviors.html.

Los comportamientos son una manera de organizar algo de la funcionalidad definida en los modelos de CakePHP. Nos permiten separar la logica que no esta directamente relacionada al modelo, pero necesita estar ahi. Al proveer una manera poderosa de extender los modelos, los comportamientos nos permiten adjuntar funcionalidad a estos al definir una variable de clase simple. Asi es como los comportamientos permiten a los modelos deshacerse de todo el peso extra que no es parte del negocio que modelan, o tambien si se requiere extrapolar esta funcionalidad.

Como ejemplo, considera un modelo que nos da acceso a una base de dato que contiene informacion extructural de arbol. Remover, editar y migrar nodos en el arbol no es tan simple como borrar, insertar y editar filas en una tabla. Muchos records pueden necesitar ser actualizados cuando las cosas se mueve. En vez de crear esos metodos que manipulan el arbol por cada modelo, simplemente le decimos a nuestro modelo que use el TreeBehavior (comportamiento de arbol), o en terminos mas formales, le decimos que se comporte como Arbol. Esto es conocido como adjuntar un comportamiento a un modelo. Con solo una linea de codigo, nuestro modelo de CakePHP toma un nuevo set de metodos que le permitirian interactuar con la estructura subyacente.

Codigo
#######

Si tu compartamiento se llama Example, entonces deberia estar en  `/app/Model/Behavior/ExampleBehavior.php`::

    <?php
    class ExampleBehavior extends ModelBehavior {

        public function setup(&$Model, $config = array()) {
            $this->settings[$Model->alias] = $config;
        }

        public function beforeFind(&$Model, $query) {
            return $query;
        }

        public function afterFind(&$Model, $results, $primary) {

        }

        public function beforeDelete(&$Model, $cascade = true) {
            return true;
        }

        public function afterDelete(&$Model) {

        }

        public function beforeValidate(&$Model) {
            return true;
        }

    }

Comportamientos de plugins
--------------------------

Si es el comportamiento del plugin Example, deberia estar en: `/app/Plugin/Example/Model/Behavior/ExampleBehavior.php`.

Usando comportamientos en Modelos
=================================

::

    <?php
    class Recipe extends AppModel {

        public $actsAs = array(
            'Example' => array( // 'Example.Example' si pertenece al plugin Example
                'config1' => 'valor aqui',
                'config2' => 'valor aqui',
            ),
        );

    }

