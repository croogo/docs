Système de secours
##################s

C'est absolument ok si vous ne voulez pas créer chacun des fichiers de vue pour
votre thème. Par exemple, si `app/View/Themed/MyTheme/Users/add.ctp` n'est pas
trouvé, CakePHP va essayer de localiser `app/View/Users/add.ctp`.

Solutions de secours supplémentaires pour les nœuds
===================================================

Pour les thèmes, Croogo supporte quelques solutions de secours supplémentaires
pour les nœuds, et quel fichier de vue trouvé le premier est rendu. Ci-dessous,
les listes de quatre actions de NodesController supportant les systèmes de vue
suppléementaires:

index
-----

- `app/View/Themed/MyTheme/Nodes/index_{type}.ctp`: où {type} est l'alias de votre type de contenu, par ex 'blog'
- `app/View/Themed/MyTheme/Nodes/index.ctp`
- `app/View/Nodes/index.ctp`

search
------

- `app/View/Themed/MyTheme/Nodes/search_{type}.ctp`
- `app/View/Themed/MyTheme/Nodes/search.ctp`
- `app/View/Nodes/search.ctp`

term
----

- `app/View/Themed/MyTheme/Nodes/term_{id}.ctp`: où {id} est l'ID de Term
- `app/View/Themed/MyTheme/Nodes/term_{type}.ctp`
- `app/View/Themed/MyTheme/Nodes/term.ctp`
- `app/View/Nodes/term.ctp`

view
----

- `app/View/Themed/MyTheme/Nodes/view_{id}.ctp`: où {id} est l'ID du Noeud
- `app/View/Themed/MyTheme/Nodes/view_{type}.ctp`
- `app/View/Themed/MyTheme/Nodes/view.ctp`
- `app/View/Nodes/view.ctp`
