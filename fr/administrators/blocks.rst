Blocks
######

Les Blocks sont ce que vous voyez dans la sidebar (region ‘right’ dans le theme
default) en boites. Ils appartiennent à une region particulière.

Elements
========

Tous les blocks sont rendus via l'element block.ctp (trouvé dans
app/Plugin/Blocks/View/Elements/block.ctp). Vous pouvez aussi utiliser votre
propre element pour vos blocks en modifiant le champ 'element' lors de l'ajout
d'un block.

Tip: Si c'est un element de plugin, entrez 'PluginName.element_name'.

Comment afficher un THIS et THAT dans un block?
===============================================

Vous êtes capable de montrer un element, menu, vocabulary (une liste imbriquée
de termes), ou une liste de noeuds en entrant un texte spécialement formaté
dans le corps de votre block.

Element
-------

Pour un element avec un nom de fichier my_element.ctp:

    [element:my_element] OR [e:my_element]

Passer des variables à votre element:

    [element:my_element myVar="value here" anotherVar="value here"]

Pour les elements de plugin:

    [element:my_element plugin="my_plugin"]

Menu
----

	Pour un Menu avec l'alias main:

    [menu:main] OR [m:main]

Avancé

``Ces options peuvent changer drastiquement la façon dont votre site web
fonctionne, à manier avec précaution``

Variables supportées:

* tag="htmlTag" : tag to wrap content output
* tagAttributes="className" : class name for wrapping tag
* selected="selected" : class for the selected element
* dropdown="false" : Dropdown menu
* dropdownClass="sf-menu" : Class for dropdown menus
* element="Menus.menu" : Element to use as template

Vocabulary
----------

Pour un Vocabulary avec l'alias categories:

    [vocabulary:categories] OR [v:categories]

Avancé

``Ces options peuvent changer drastiquement la façon dont votre site web
fonctionne, à manier avec précaution``

Variables supportées :

* link="true" : si à true, cela crée un lien pour chaque vocabulary trouvé, il
  va créer le lien en utilisant les arguments fournis pour le plugin,
  controller, action et le type.
* plugin="nameOfPlugin" : nom du plugin fourni pour créer un lien
* controller="controller" : nom du controller fourni pour créer un lien
* action="action" : nom de l'action fourni pour créer un lien
* type="type" : type de node fourni pour créer un lien
* tag="htmlTag" : tag to wrap content output
* tagAttributes="className" : className for wrapping tag
* element="Taxonomy.vocabulary" : Element à utiliser comme template

Nodes
-----

Par exemple, vous voulez montrer une liste des 5 posts les plus récents dans un
block:

    [node:recent_posts conditions="Node.type:blog;Node.status:1" order="Node.id DESC" limit="5"]

Avancé

``Ces options peuvent changer drastiquement la façon dont votre site web
fonctionne, à manier avec précaution``

Variables supportées :

* link="true" : si à true, cela crée un lien pour chaque vocabulary trouvé, il
  va créer le lien en utilisant les arguments fournis pour le plugin,
  controller, action et le type.
* plugin="nodes" : nom du plugin fourni pour créer un lien
* controller="nodes" : nom du controller fourni pour créer un lien
* action="view" : nom de l'action fourni pour créer un lien
* element="Nodes.node_list" : Element à utiliser comme template
