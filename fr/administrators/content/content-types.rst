Types de Contenu
================

Par défaut, il y a trois types de contenu:

- Page: pour les pages
- Blog: pour les posts de blog
- Node: A moins que vous soyez sur du type de contenu à utiliser

Si vous pensez que vous avez besoin d'un nouveau type de contenu, vous êtes
capable d'en créer un à partir du panneau admin.


Paramètres
==========

Quand vous ajoutez ou modifiez des types de contenu, vous allez remarquer un
champ 'Params' où vous pouvez entrer des paramètres. Il s'attend à ce qu'un
paramètre soit entré par ligne avec une clé/valeur utilisant un signe égal
en séparateur. Des exemples ci-dessous:

    my_param_key=value_here
    another_key=another_value

Les clés de paramètre supportés pour les types de contenu:

- nodes_per_page: Attend un nombre entier supérieur à 0 pour la limite de la
  pagination des nodes
- routes: Attend 0 ou 1 pour de belles URLs de type `/type-alias/node-slug`

Vous êtes libre d'utiliser plus de clés pour les paramètres et elles seront
disponibles dans un formatage sympa pour le behavior
`ParamsBehavior <http://github.com/croogo/croogo/blob/master/models/behaviors/params.php>`_.
