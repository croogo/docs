Helpers
#######

Lire la doc de CakePHP sur les Helpers:
http://book.cakephp.org/2.0/en/views/helpers.html.

Qu'est-ce qu'un Helper?
=======================

Les Helpers sont les classes comme les components mais pour la couche de
présentation de votre application. Ils contiennent une logique de présentation
partagée entre plusieurs views, elements ou layouts. Ce chapitre va vous
montrer comment créer vos propres helpers, et souligne les tâches basiques que
les helpers du coeur de CakePHP peuvent aider à accomplir.

Code
====

Disons que nous appelons notre helper Example, et il serait trouvé dans
`/app/View/Helper/ExampleHelper.php`::

    <?php
    class ExampleHelper extends AppHelper {

        public function lowercase($text) {
            return strtolower($text);
        }

    }

Les helpers du Plugin
---------------------

Si c'est un helper du plugin Example, il sera trouvé dans
`/app/Plugin/Example/View/Helper/ExampleHelper.php`.

Utilisation des Helpers dans les Views
======================================

Avant d'utiliser les helpers dans les views, nous avons besoin de le faire
connaître à notre Controller en le chargeant::

    <?php
    class RecipesController extends AppController {

        public $uses = array(
            'Recipe',
        );

        public $helpers = array(
            'Example', // 'Example.Example' if it is from Example plugin
        );

        public function view($id) {
            $recipe = $this->Recipe->findById($id);
            $this->set('recipe', $recipe);
        }

    }

Maintenant, nous pouvons utiliser le helper à partir de notre view dans
/app/View/Recipes/view.ctp::

    <div class="recipes view">
        <h2><?php echo $recipe['Recipe']['title']; ?></h2>

        <p><?php echo $recipe['Recipe']['body']; ?></p>

        <p><?php echo $this->Example->lowercase('TEXT WILL BE CONVERTED TO LOWERCASE'); ?></p>
    </div>
