Plugins
#######

Comment les uploader?
=====================

Si vous avez votre plugin dans un fichier zip, suivez ces instructions:

- Connectez-vous dans votre panneau admin
- Allez à la page Extensions > Plugins
- Remarquez le lien Upload en haut. Cela va vous emmener sur une nouvelle
  page où vous pouvez uploader le fichier zip.

Manuel d'upload
===============

Placez votre plugin dans ``/app/Plugin/YourPluginName``

Comment l'activer/le désactiver?
================================

Après avoir uploadé votre locale, vous avez besoin de l'activer.

- A partir de votre panneau admin, allez sur la page Extensions > Plugins
- Clickez sur l'icon de croix/tick va activer ou désactiver votre plugin

Migrations
==========

Quand vous uploadez un nouveau plugin, un lien "Migrate" peu apparaitre
à gauche du lien "Deactivate". Cel lien permet de créer ou de mettre à jour
la base de données pour ce plugin.

Dans la plupart des cas, cette opérration est appliquée automatiquement quand
vous activez le plugin. Mais dans certains cas, le développeur du plugin peut
avoir besoin du manuel de migrations pour un meilleur contrôle, ou bien ajouter
des étapes supplémentaires sont nécessaires avant l'activation de la migration.
Dans ce cas, vous avez besoin de lire la documentation du plugin avant de
cliquer sur le lien "Migrate" pour connaître les conséquences possibles.
