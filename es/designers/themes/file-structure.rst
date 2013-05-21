Estructura de archivos
######################

Cada plantilla esta identificada por su alias unico. Si tienes una plantilla en el directorio `app/View/Themed/MiTema`, Entonces el alias de tu plantilla sera MiTema.

Un archivo `theme.json` tambien es requerido. Puedes ver el archivo JSON usado en la plantilla por defecto aqui: `theme.json <http://github.com/croogo/croogo/blob/1.4/webroot/theme.json>`_.

Estructura
==========

Por ejemplo, si tienes una plantilla con el alias MiTema. Todos tus archivos deberan estar ubicados de la siguiente manera:

- app/View/Themed/MiTema/
  - Elements/
  - Helper/
    - custom.php
  - Layouts/
    - default.ctp
  - Nodes/
    - view.ctp
  - ...
  - webroot/
    - css/
      - theme.css
    - js/
      - theme.js
    - img/
      - screenshot.png
    - theme.yml

No olvides el archivo theme.json. Tu tema no estara disponible en el panel de administracion si no se encuentra este archivo.
