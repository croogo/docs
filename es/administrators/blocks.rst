Bloques
#######

Bloques son lo que ves en la barra lateral (region 'Derecha' en la plantilla por defecto) como cajas. Pertenecen a una region en particular.

Elementos
=========

Todos los bloques son mostrados a traves del elemento block.ctp (que se encuentra en app/Plugin/Blocks/View/Elements/block.ctp). Puedes hacer uso de tu propio elemento tambien para tus bloques al editar el campo de 'elemento' cuando agregas un bloque.

Tip: Si es un elemento de un plugin, ingresa 'NombrePlugin.nombre_elemento'.

Como mostrar "Esto" y "Aquello" en un bloque?
=============================================

Puedes mostrar un elemento, menu, vocabulario (lista anidada de terminos), o una lista de nodos al ingresarla con un formato especial en el cuerpo de tu bloque.

Elemento
--------

Para un elemento con un nombre de archivo mi_elemento.ctp
    [element:mi_elemento] O [e:mi_elemento]

Pasando una variable a tu elemento:

    [element:mi_elemento miVar="valor aqui" otraVar="valor aqui"]

Para elemento de plugins:

    [element:mi_elemento plugin="mi_plugin"]


Menu
----

Para un menu con alias de 'principal'
    [menu:principal] o [m:principal]


Vocabulario
-----------

Para un vocabulario con alias de 'categorias':

    [vocabulary:categorias] OR [v:categorias]

Nodos
-----

Por ejemplo, si quieres mostrar una lista de los 5 nodos mas recientes como un bloque:
    [node:recent_posts conditions="Node.type:blog;Node.status:1" order="Node.id DESC" limit="5"]