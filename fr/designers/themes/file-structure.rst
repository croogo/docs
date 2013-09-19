Structure de fichier
####################

Un thème est identifié par son alias unique. Si vous avez votre thème dans le
répertoire `app/View/Themed/MyTheme`, alors l'alias de votre thème est MyTheme.

Un fichier `theme.json` est aussi nécessaire. Vous pouvez utiliser le fichier
JSON utilisé pour le thème par défaut ici: `theme.json <http://github.com/croogo/croogo/blob/1.4/webroot/theme.json>`_.

Structure
=========

Par exemple, vous avez un thème avec l'alias MyTheme. Tous les fichiers doivent
être placés comme ceci:

- app/View/Themed/MyTheme/
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

N'oubliez pas le fichier theme.json. Votre thème ne sera pas disponible dans
le panneau admin sinon.
