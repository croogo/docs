Sistema de repliegue
####################

Es completamente aceptable si no quieres crear todas y cada una de las vistas de tu plantilla. Por ejemplo, si `app/View/Themed/MyTheme/Users/add.ctp` no se encuentra, CakePHP intentara localizar  `app/View/Users/add.ctp`.

Sistemas de repliegue adicionales para Nodos
============================================

En las plantillas, Croogo soporta distintos tipos de repliegues para nodos, y cualquier archivo de vista que encuentre primero es renderizado. Debajo hay una lista de 4 acciones para el Controlador NodesController donde se soportan las vistas adicionales.

index
-----

- `app/View/Themed/MyTheme/Nodes/index_{tipo}.ctp`: donde {type} es el alias del tipo de contenido. Por ejemplo 'blog'
- `app/View/Themed/MyTheme/Nodes/index.ctp`
- `app/View/Nodes/index.ctp`

search
--------

- `app/View/Themed/MyTheme/Nodes/search_{tipo}.ctp`
- `app/View/Themed/MyTheme/Nodes/search.ctp`
- `app/View/Nodes/search.ctp`

term
----

- `app/View/Themed/MyTheme/Nodes/term_{id}.ctp`: donde {id} is el identificador del Termino
- `app/View/Themed/MyTheme/Nodes/term_{tipo}.ctp`
- `app/View/Themed/MyTheme/Nodes/term.ctp`
- `app/View/Nodes/term.ctp`

view
----

- `app/View/Themed/MyTheme/Nodes/view_{id}.ctp`: donde {id} es el identificador del Nodo.
- `app/View/Themed/MyTheme/Nodes/view_{type}.ctp`
- `app/View/Themed/MyTheme/Nodes/view.ctp`
- `app/View/Nodes/view.ctp`
