Les Blocks de View
##################

Les blocks de view de CakePHP ont été implementés dans Croogo 1.4 pour
admin_index, admin_add, et admin_edit.

Lisez la doc de CakePHP sur les blocks de view:
http://book.cakephp.org/2.0/en/views.html#using-view-blocks.

Vous pouvez surcharger les blocks par défaut de Croogo::

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

Les blocks suivants sont disponibles:

- title: Surcharge le titre.
- tabs: Surcharge les li link tabs.
- paging: Surcharge les nombres et le compteur de la pagination.

admin_edit / admin_add
======================

Les blocks suivants sont disponibles:

- title: Surcharge le titre.
- actions: Surcharge les li link actions.
- buttons: Surcharge les boutons Save et Cancel.
