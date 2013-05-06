Archivo JSON
#########

Un archivo theme.json es requerido para cada tema en Croogo. Este es requerido porque ahi se almacena informacion util como los menus y regiones que usa. De esta manera le permite a Croogo hacer peticiones a la base de datos y estar disponible sin romper el esquema MVC.

El contenido de un ejemplo de theme.json puede ser encontrado en: `app/View/Themed/MyTheme/webroot/theme.json` y se muestra abajo ::

    {
      "name" : "Sample",
      "description" : "Sample theme for Croogo",
      "screenshot" : "screenshot.png",

      "author" : "Author Name",
      "authorEmail" : "author@email.com",
      "authorUrl" : "http://authorswebsite.com",

      "menus" : [
        "main",
        "footer"
        ],

      "regions" : [
        "right"
        ]
    }

- name: El nombre de la plantilla
- description: La descripcion de la plantilla
- screenshot: Una vista preliminar de tu plantilla, ubicada en `app/View/Themed/MyTheme/webroot/img/screenshot.png`
- author: tu nombre
- authorEmail: tu email
- authorUrl: tu pagina web
- menus: una lista de menus que la plantilla usa
- regions: una lista de regiones que tu plantilla usa para mostrar bloques
- vocabularies (opcional): una lista de alias de vocabularios que tu plantilla usa.
