Instalação
##########

Instalação pela interface Web
=============================

- Extraia o arquivo. Envie o conteúdo para o seu servidor.
- Crie um novo banco de dados MySQL (collation utf8_unicode_ci)
- Visite http://seu-site.com/ de seu navegador e siga as instruções.

Instalação Manual
=================

- Extraia o arquivo. Envie o conteúdo para o seu servidor.
- Crie um novo banco de dados MySQL (collation utf8_unicode_ci), e use esses dois arquivos de dump do SQL nesta orderm:

  - app/Config/Schema/sql/croogo.sql
  - app/Config/Schema/sql/croogo_data.sql

- Renomeie:

  - app/Config/database.php.install para database.php, e edite os detalhes.
  - app/Config/croogo.php.install para croogo.php, e edite os detalhes.
  - app/Config/settings.yml.install para settings.yml

- Você pode acessar o painel de administração no http://your-site.com/admin. O instalador deve exibir uma página para você criar o usuário administrativo.

É recomendado que você instale Croogo usando o instalador pela interface web por razões de segurança.