Vistas
######

Lee la documentacion de CakePHP para Vistas:
http://book.cakephp.org/2.0/en/views.html.

Que es una vista?
=================

Las vistas son la V en MVC. Las vistas son responsables de generar la salida especifica requerida por una peticion. Comunmente estan en la forma de HTML, XML o JSON, pero el streaming de archivos y crear PDFs que el usuario puede descargar tambien son responsabilidad de la capa de Vista.


Codigo
######

Del ejemplo previo de Recetas (Recipes), estaremos ubicando el archivo de Vista en `/app/View/Recipes/view.ctp`::

    <div class="recipes view">
        <h2><?php echo $recipe['Recipe']['title']; ?></h2>

        <p><?php echo $recipe['Recipe']['body']; ?></p>
    </div>

Vistas de plugins
-----------------

Si es la vista del plugin de recetas (Recipes), puede ser encontrado en: `/app/Plugin/Recipes/View/view.ctp`.