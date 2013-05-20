File structure
##############

A theme is identified by it's unique alias. If you have your theme under the directory app/View/Themed/MyTheme, then your theme's alias is MyTheme.

A theme.json file is also required. You can see the JSON file used for the default theme here: `theme.json <http://github.com/croogo/croogo/blob/1.4/webroot/theme.json>`_.

Structure
=========

For example, you have a theme with alias MyTheme. All your files should be placed like this:

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

Do not forget the theme.json file. Your theme will not be available in the admin panel otherwise.

