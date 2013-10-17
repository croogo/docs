Callbacks
#########

Components
==========

Les callbacks suivants sont supportés pour les components par CakePHP.

- initialize: Appelé avant Controller::beforeFilter()
- startup: Appelé après the Controller::beforeFilter() et avant l'action du controller
- beforeRender: Appelé après le Controller::beforeRender(), après que la classe de view est chargé, et avant le Controller::render()
- shutdown: Appelé après Controller::render() et avant que la sortie soit affichée au navigateur.

Code
----

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

Apprenez plus sur les components dans
http://book.cakephp.org/2.0/en/controllers/components.html.

Helpers
=======

Les callbacks suivants sont supportés pour les helpers par CakePHP:

- beforeRender: Appelé avant que le fichier de view soit rendu.
- afterRender: Appelé après que le fichier de view est rendu mais avant que le layout ait été rendu.
- beforeLayout: Appelé avant que le layout soit rendu.
- afterLayout: Appelé après que le layout est rendu.

Les callbacks supplémentaires dans Croogo pour une meilleure intégration

- afterSetNode: Appelé après LayoutHelper::setNode(). Une bonne place pour modifier le contenu du node.
- beforeNodeInfo: Appelé avant LayoutHelper::nodeInfo().
- afterNodeInfo: Appelé après LayoutHelper::nodeInfo().
- beforeNodeBody: Appelé avant LayoutHelper::nodeBody().
- afterNodeBody: Appelé après LayoutHelper::nodeBody().
- beforeNodeMoreInfo: Appelé avant LayoutHelper::nodeMoreInfo().
- afterNodeMoreInfo: Appelé après LayoutHelper::nodeMoreInfo()

Code
----

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

En lire plus sur les helpers dans
http://book.cakephp.org/2.0/en/views/helpers.html.
