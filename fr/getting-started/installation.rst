Installation
############

Installeur par le Web
=====================

- Extrayez l'archive. Uploadez le contenu vers votre serveur.
- Créez une nouvelle base de données MySQL (utf8_unicode_ci collation)
- Visitez http://your-site.com/ de votre navigateur et suivez les instructions.

Manuel d'installation
=====================

- Extrayez l'archive. Uploadez le contenu vers votre serveur.
- Créez une nouvelle base de données MySQL (utf8_unicode_ci collation), et
  utilisez ces deux fichiers dump SQL dans l'ordre donné:
  - app/Config/Schema/sql/croogo.sql
  - app/Config/Schema/sql/croogo_data.sql
- Renommez:
  - app/Config/database.php.install en database.php, et éditez les détails.
  - app/Config/croogo.php.install en croogo.php, et éditez les détails.
  - app/Config/settings.yml.install en settings.yml
- Vous pouvez accéder à votre panneau d'admin à http://your-site.com/admin.
  L'installeur devrait afficher une page pour vous pour créer un utilisateur
  admin.

Il est recommandé que vous installiez Croogo en utilisant l'installeur par le
Web pour des raisons de sécurité.
