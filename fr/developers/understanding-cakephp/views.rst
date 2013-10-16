Views
#####

Lire la doc de CakePHP sur les Views: http://book.cakephp.org/2.0/en/views.html.

Quoi de neuf?
=============

Views sont le V dans MVC. Les Views sont responsables de la génération de
sortie spécifique nécessaire pour la requête. Souvent, c'est sous forme de
HTML, XML, ou JSON, mais le streaming de fichiers et la création de PDF que les
utilisateurs peuvent télécharger sont aussi des responsabilités de la Couche
View.

Code
####

A partir de l'exemple précédent des Recipes, nous allons afficher le fichier
de view dans `/app/View/Recipes/view.ctp`::

    <div class="recipes view">
        <h2><?php echo $recipe['Recipe']['title']; ?></h2>

        <p><?php echo $recipe['Recipe']['body']; ?></p>
    </div>

Les Views de Plugin
-------------------

Si c'est la view du plugin Recipes, elle sera trouvée dans
`/app/Plugin/Recipes/View/view.ctp`.
