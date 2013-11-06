Permissions
###########

Croogo utilise les ACLs de CakePHP pour la gestion des permissions des
utilisateurs. Pour être honnete, il peut être très compliqué de comprendre
les ACLs pour les débutants. Mais Croogo supporte la difficulté en fournissant
une interface utilisable et simple pour la gestion des permissions.

Puisque l'application est construite avec un framework MVC, toute url (autre
que les fichiers normaux comme CSS et images) que vous pouvez accéeder
est la sortie d'une action d'un Controller. Par exemple, quand vous visitez
un post de blog 'Hello World', il montre la vue de l'action du controller
des Noeuds.

Maintenant pour gérer les permissions pour cette action:

- Connectez-vous dans votre panneau admin
- Allez sur la page Users > Permissions
- Clickez sur Nodes, cela va montrer toutes ses actions

Ensuite clickez sur l'icone tick/cross icon de la ligne de la vue pour
activer ou désactiver l'accès à cette action pour certains roles.
