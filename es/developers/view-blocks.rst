Bloques de Vista
################

Los bloques de vista han sido implementados en Croogo 1.4 para admin_index, admin_add, y admin_edit.

Lee acerca de los bloques de vista en la documentacion de CakePHP:
http://book.cakephp.org/2.0/en/views.html#using-view-blocks.

Puedes sustituir los bloques por defecto de Croogo::

    <?php
    $this->extend('/Common/admin_index');
    // Use assign for single line overrides
    $this->assign('title', 'My Custom Title');
    ?>
    <!-- Or start() and end() for multiline overrides -->
    <?php $this->start('tabs'); ?>
        <li>
            <?php echo $this->Html->link('My Link', '/somewhere'); ?>
        </li>
    <?php $this->end(); ?>

    <p>Any remaining content will override the content block.</p>

admin_index
===========

Los siguientes bloques estan disponibles:

- title: Sustituye el titulo.
- tabs: Sustituye los vinculos de la etiqueta li de pestañas.
- paging: Sustituye los numeros y el contador de paginacion.

admin_edit / admin_add
======================

Los siguientes bloques estan disponibles:

- title: Sustituye el titulo.
- actions: Sustituye los vinculos de acciones de la etiqueta li.
- buttons: Sustituye los botones de Guardar y Cancelar.
