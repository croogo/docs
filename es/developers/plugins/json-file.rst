Archivo JSON
############

Un archivo plugin.json es requerido para cada plugin en Croogo que requiera ser activado desde el panel de administracion.Almacena Informacion util como los detalles de contacto del desarrollador, asi como informacion de sus dependencias.

Si tu plugin se llama Example, el contenido del archivo plugin.json en `app/Plugin/Example/Config/plugin.json` podria ser ::

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

- name: El nombre del plugin
- description: Descripcion del plugin
- author: tu nombre
- authorEmail: Tu direccion de email
- authorUrl: Tu sitio web
- dependencies (optional): Lista de plugins de los cuales depende este plugin
