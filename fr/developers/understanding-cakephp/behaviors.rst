Behaviors
#########

Lire la doc CakePHP sur les Behaviors:
http://book.cakephp.org/2.0/en/models/behaviors.html.

Les behaviors du Model sont une façon d'organiser quelques unes des
fonctionnalités définies dans les models de CakePHP. Ils nous permettent
de séparer la logique qui n'est pas forcément directement lié au model, mais
a besoin d'être là. En fournissant une façon simple et pourtant puissante
d'étendre les models, behaviors nous permet d'attacher une fonctionnalité aux
models en définissant une variable de classe simple. C'est la façon dont
les behaviors permettent d'autoriser les models d'utiliser tous le poids
supplémentaire qui ne sera pas partie du contrat de business qu'ils modèlent,
ou qui est aussi nécessaire dans différents models et peuvent être extrapolés.

En exemple, considérons un model qui nous donne un accès à une table de la base
de données qui stocke l'information structurelle sur un Tree. Retirer, ajouter,
et migrer les nodes dans le tree n'est pas aussi simple que de supprimer,
insérer et éditer des lignes dans la table. Plusieurs enregistrements peuvent
être mis à jour puisque les choses bougent autour. Plutôt que de créer ces
méthodes de manipulation-tree sur les bases d'un model (pour chaque model qui
a besoin de cette fonctionnalité), nous pourrions simplement dire à notre
model d'utiliser le TreeBehavior, ou dans des termes plus formels, nous
disons à notre model de se comporter en Tree. On le fait en attachant un
behavior à un model. Avec juste une ligne de code, notre model de CakePHP prend
un nouvel ensemble de méthodes qui lui permet d'intéragir avec la structure
soulignée.

Code
####

Si le nom de votre Behavior est Example, il sera trouvé dans
`/app/Model/Behavior/ExampleBehavior.php`::

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

Behaviors de Plugin
-------------------

Si il y a un behavior du plugin Example, il sera trouvé dans
`/app/Plugin/Example/Model/Behavior/ExampleBehavior.php`.

Utilisation des Behaviors dans les Models
=========================================

::

    <?php
    class Recipe extends AppModel {

        public $actsAs = array(
            'Example' => array( // 'Example.Example' if it is from Example plugin
                'config1' => 'value here',
                'config2' => 'value here',
            ),
        );

    }
