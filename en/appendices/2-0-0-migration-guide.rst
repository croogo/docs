2.0.0 Migration Guide
#####################

Schema Changes
==============

- Enlarge ``users.timezone`` column
- Add Trackable fields, ``created_by`` and ``updated_by``
- Add Publishable fields, ``publish_start`` and ``publish_end``
- ``nodes_taxonomies`` renamed to ``model_taxonomies``
- ``comments.node_id`` renamed to ``comments.foreign_key``

Settings
========

New settings have been added:

- Site.asset_timestamp
- Site.home_url

Settings have been made editable:

- Site.locale
- Site.admin_theme

Migrating from 1.5.x
====================

Ensure that you have a full backup of your existing installation and database.

Since the application layout has changed a lot, it is not straightforward to
migrate from a 1.5.x installation. Further, it is advised to upgrade to the
latest available 1.5.x version first before attempting to migrate to 2.x.

Once you have updated to latest 1.5.x, the safest way to do this is to install
2.x to a separate directory and database.

Assumptions
-----------

- Croogo is installed in ``~/sites/croogo``
- CakePHP is installed in ``~/sites/lib/Cake``
- DocumentRoot is ``~/sites/croogo/webroot``
- Old Croogo database is: ``croogo15_db``
- New Croogo database is: ``croogo20_db``

Migration Steps
---------------

- Backup ``Config/croogo.php``, ``Config/settings.json``, ``Config/database.php``::

    $ mkdir ~/sites/backup
    $ ( cd ~/sites/croogo/Config && cp croogo.php settings.json database.php ~/sites/backup )

- Backup mysql database::

    $ mysqldump -u<user> -p<pass> croogo15_db > croogo15.sql

- Create a new database::

    $ mysql -u<user> -p<pass> -e 'create database croogo20_db'
    $ mysql -u<user> -p<pass> croogo20_db < croogo15.sql

- Setup a new croogo instance in a different directory using ``composer``::

    $ COMPOSER_PROCESS_TIMEOUT=1200 composer create-project --no-dev -v croogo/app ~/sites/croogo-app

- Restore your backup ``Config/croogo.php``, ``Config/settings.json``, ``Config/database.php``::

    $ ( cd ~/sites/backup && cp croogo.php settings.json database.php ~/sites/croogo-app/Config )

- Rename the database in ``database.php``::

    $ ( cd ~/sites/croogo-app && sed -i 's/croogo15_db/croogo20_db/' Config/database.php' )

- Copy your own plugins from the old application directory.  Be sure not to
  copy the old Croogo plugins from 1.5.x

- Run the migrations command to update database schema::

    $ cd ~/sites/croogo-app && Console/cake croogo upgrade migrations

- Update the DocumentRoot to the new croogo instance ``~/sites/croogo-app/webroot``

By this point, hopefully Croogo has been successfully migrated.

Final migrated application
--------------------------

The final migration will have the following directory layout:

    ``~/sites/croogo-app`` Contains the barebone application skeleton

    ``~/sites/croogo-app/Plugin/Search`` Contains the Search plugin

    ``~/sites/croogo-app/Plugin/Migrations`` Contains the Migrations plugin

    ``~/sites/croogo-app/Plugin/Ckeditor`` Contains the Ckeditor plugin

    ``~/sites/croogo-app/Vendor/cakephp/cakephp`` Contains the CakePHP framework

    ``~/sites/croogo-app/Vendor/croogo/croogo`` Contains the core of Croogo CMS
