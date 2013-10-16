Structure de Fichier
####################

Un plugin est identifié par son alias unique. Si vous avez votre plugin sous
le répertoire `app/Plugin/Example`, alors l'alias de votre plugin est Example.

Structure
=========

- app/Plugin/Example/
  - Config/
    - bootstrap.php
    - plugin.json
    - routes.php
    - ExampleActivation.php
  - Controller/
    - Component/
      - ExampleComponent.php
    - ExampleController.php
    - ExampleAppController.php
  - Model/
    - Behavior/
    - ExampleAppModel.php
  - View/
    - Elements/
    - Example/
    - Helper/
      - ExampleHelper.php
  - webroot/
    - css/
    - img/
    - js/

N'oubliez pas le fichier plugin.json. Il est nécessaire, sinon le plugin ne
sera pas disponible dans le panneau admin pour l'activation.

Un plugin totalement fonctionnel est disponible dans le répertoire.
 