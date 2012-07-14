Installation
############

Web based installer
===================

- Extract the archive. Upload the content to your server.
- Create a new MySQL database (utf8_unicode_ci collation)
- Visit http://your-site.com/ from your browser and follow the instructions.

Manual installation
===================

- Extract the archive. Upload the content to your server.
- Create a new MySQL database (utf8_unicode_ci collation), and use these two SQL dump files in given order:
  - app/Config/Schema/sql/croogo.sql
  - app/Config/Schema/sql/croogo_data.sql
- Rename:
  - app/Config/database.php.install to database.php, and edit the details.
  - app/Config/croogo.php.install to croogo.php, and edit the details.
  - app/Config/settings.yml.install to settings.yml
- You can access your admin panel at http://your-site.com/admin. The installer should display a page for you to create the administrative user.

It is recommended that you install Croogo using the web based installer for security reasons.