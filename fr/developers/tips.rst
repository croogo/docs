Astuces
#######

Rendez-le plus rapide
=====================

Croogo est fourni avec un niveau de debug activé à 1. Vous pouvez le désactiver
dans `/app/Config/croogo.php` pour le rendre plus rapide. Remplacez la ligne 37
avec ceci::

    Configure::write('debug', 0);
