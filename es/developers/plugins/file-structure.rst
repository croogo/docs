Estructura de archivos
######################

Un plugin es identificado por un alias único. Si tu tienes un plugin en el directorio `app/Plugin/Example`, entonces el alias de tu plugin es Example.

Estructura
==========

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

No olvides el arhivo plugin.json. Este es requerido, de otra manera el plugin no estara disponible en el panel de administracion para su activacion.

Un plugin completamente funcional esta disponible en el repositorio. 