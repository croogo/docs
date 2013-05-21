Tipos de contenido
=============

Por defecto, hay 3 tipos de contenido
- Paginas: para paginas
- Blog: para publicaciones
- Nodo: si no estas seguro de que tipo de contenido usar

Si crees que requieres un tipo de contenido nuevo, puedes crearlo desde el panel de control

Parametros
==========

Cuando agrega o edita tipos de contenido, encontraras un campo de 'Params' (parametros), donde podras ingresar parametros. Se espera que ingrese un parametro por linea con los segmentos de indice, valor utilizando el signo de "igual". Ejemplo:

    my_indice_parametro=valor_aqui
    otro_indice=otro_valor

Los valores validos para indices en los tipos de contenido son:
- nodes_per_page: Espera un valor unitario mayor a 0 para los limites de paginacion de los nodos
- routes: Espera 0 o 1 para urls limpias como `/type-alias/node-slug`

Eres libre de ingresar mas parametros conforme sean disponibles en un formato correcto desde `ParamsBehavior <http://github.com/croogo/croogo/blob/master/models/behaviors/params.php>`_.
