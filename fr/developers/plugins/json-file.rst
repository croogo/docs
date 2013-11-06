Fichier JSON
############

Un fichier plugin.json est nécessaire pour chaque plugin dans Croogo qui a
besoin d'être activé à partir du panneau admin. Il stocke des informations
utiles comme les détails de contact du développeur, ainsi que des informations
sur ses dépendances.

Si le nom de votre plugin est Example, le contenu du fichier `plugin.json`
dans `app/Plugin/Example/Config/plugin.json` pourrait être::

    {
        "name": "Example",
        "description": "Example plugin for demonstrating hook system",

        "author": "Author Name",
        "authorEmail": "author@example.com",
        "authorUrl": "http://example.com",

        "dependencies": {
          "plugins": [
            "acl",
              "extensions"
              ]
            }
    }

- name: le nom de votre plugin
- description: la description de votre plugin
- author: votre nom
- authorEmail: votre adresse email
- authorUrl: votre website
- dependencies (optional): liste des autres plugins dont ce plugin a besoin
