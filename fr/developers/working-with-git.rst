Travailler avec Git
###################

Le dépôt git de Croogo est hébergé sur GitHub. Le dépôt contient le contenu
du dépôt de `app` seulement, ainsi vous avez besoin de télécharger CakePHP
avant de le dupliquer.

Une fois que vous avez téléchargé et extrait l'archive de CakePHP, naviguez
vers le dépôt `app` et effacez le. Maintenant lancez ce qui suit::

    $ cd app
    $ git init
    $ git remote add origin git://github.com/croogo/croogo.git
    $ git pull origin master
    $ git submodule update --init

Contribuer
==========

La meilleur façon de contribuer au code du coeur est de forker le dépôt sur
GitHub, de faire des changements, et ensuite d'envoyer une pull request. Pour
faire ceci:

- Créez-vous un compte GitHub
- Forkez Croogo.
- Ensuite vous aurez votre fork à l'adresse http://github.com/yourusername/croogo.
- Faites tout changement sur celui-ci, et envoyez une pull request.
