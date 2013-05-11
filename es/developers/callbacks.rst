Retrollamadas
#############

Componentes
===========

Las siguientes retrollamadas son soportadas por componentes por CakePHP

- initialize: Llamada antes de Controller::beforeFilter()
- startup: Llamada despues de Controller::beforeFilter() y antes de la accion del controlador.
- beforeRender: Llamada despues de Controller::beforeRender(), despues de que la clase de vista es llamada y antes de Controller::render()
- shutdown: Llamada despues de Controller::render() y antes de que la salida sea impresa al navegador.

Codigo
------

::

    <?php
    class ExampleComponent extends Component {

        //called before Controller::beforeFilter()
        public function initialize(&$Controller, $settings = array()) {
            // saving the controller reference for later use
            $this->Controller =& $Controller;
        }

        //called after Controller::beforeFilter()
        public function startup(&$Controller) {
        }

        //called after Controller::beforeRender()
        public function beforeRender(&$Controller) {
        }

        //called after Controller::render()
        public function shutdown(&$Controller) {
        }

        //called before Controller::redirect()
        public function beforeRedirect(&$Controller, $url, $status = null, $exit = true) {
        }

        public function redirectSomewhere($value) {
            // utilizing a controller method
            $this->controller->redirect($value);
        }

    }

Lee mas acerca de los componentes en http://book.cakephp.org/2.0/en/controllers/components.html.

Helpers (Auxiliares)
====================

Las siguientes retrollamadas son soportadas por Helpers por CakePHP:

- beforeRender: Llamada antes de que el archivo de vista sea reproducido.
- afterRender: Llamada despues que el archivo de vista es reproducido pero antes que la distribucion sea reproducida.
- beforeLayout: Llamada antes de que la distribucion sea reproducida.
- afterLayout: Llamada despues de que la distribucion es reproducida.

Retrollamadas adicionales por Croogo para una mejor integracion.

- afterSetNode: Llamada despues de LayoutHelper::setNode(). Un buen lugar para modificar el contenido de los nodos.
- beforeNodeInfo: Llamada antes de LayoutHelper::nodeInfo().
- afterNodeInfo: Llamada despues de LayoutHelper::nodeInfo().
- beforeNodeBody: Llamada antes de  LayoutHelper::nodeBody().
- afterNodeBody: Llamada despues de LayoutHelper::nodeBody().
- beforeNodeMoreInfo: Llamada antes de LayoutHelper::nodeMoreInfo().
- afterNodeMoreInfo: Llamada despues de LayoutHelper::nodeMoreInfo()

Codigo
------

::

    <?php
    class ExampleHelper extends AppHelper {

        public $helpers = array(
            'Html',
            'Layout',
        );

        public function beforeRender() {
        }

        public function afterRender() {
        }

        public function beforeLayout() {
        }

        public function afterLayout() {
        }

        public function afterSetNode() {
            // field values can be changed from hooks
            $currentTitle = $this->Layout->node('title');
            $modifiedTitle = $currentTitle . ' [Modified by ExampleHelper]';
            $this->Layout->setNodeField('title', $modifiedTitle);
        }

        public function beforeNodeInfo() {
            return '<p>beforeNodeInfo</p>';
        }

        public function afterNodeInfo() {
            return '<p>afterNodeInfo</p>';
        }

        public function beforeNodeBody() {
            return '<p>beforeNodeBody</p>';
        }

        public function afterNodeBody() {
            return '<p>afterNodeBody</p>';
        }

        public function beforeNodeMoreInfo() {
            return '<p>beforeNodeMoreInfo</p>';
        }

        public function afterNodeMoreInfo() {
            return '<p>afterNodeMoreInfo</p>';
        }

    }

Lee mas acerca de los helpers en http://book.cakephp.org/2.0/en/views/helpers.html.