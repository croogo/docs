JSON file
#########

Un fichier theme.json est nécessaire pour chaque thème dans Croogo. C'est
nécessaire parce que les thèmes peuvent stocker des informations utiles comme
les menus et les regions qu'il utilise, et de cette façon, il permet à Croogo
de rechercher la base de données et de rendre ces informations disponibles
pour le thème sans casser MVC.

Le contenu d'un fichier d'exemple theme.json file se trouvant dans
`app/View/Themed/MyTheme/webroot/theme.json` est montré ci-dessous::

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

- name: le nom de votre thème
- description: la description de votre thème
- screenshot: Une petite preview de votre thème placée dans `app/View/Themed/MyTheme/webroot/img/screenshot.png`
- author: votre nom
- authorEmail: votre email
- authorUrl: votre site internet
- menus: une liste d'alias de de menu que le thème utilise
- regions: une liste de regions que le thème utilise pour montrer les blocks
- vocabularies (optionel): une liste d'alias de vocabulaires que le thème utilise
