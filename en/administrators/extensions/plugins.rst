Plugins
#######

How to upload?
==============

If you have your plugin in a zip file, follow these instructions:

- Log in to your admin panel
- Go to Extensions > Plugins page
- Notice the Upload link on top. It will take you to a new page where you can upload the zip file.

Manual upload
-------------

Place your plugin under ``/app/plugins/your_plugin_name``

.. versionchanged:: 1.4
   The directory will be ``app/Plugin/YourPluginName`` following CakePHP 2.x
   convention.

How to activate/deactivate?
===========================

After uploading your plugin, you need to activate it.

- From your admin panel, go to Extensions > Plugins page
- Clicking on cross/tick icon will activate or deactivate your plugin

Migrations
==========

When you upload a new plugin, a "Migrate" link might appear to the left of
"Deactivate" link. This link allows to create or update the database for this
plugin.

In most cases this operation is automatically applied when activating the
plugin.  But in some cases, the plugin developer may require manual migrations
for better control, or additional steps are required before activating the
migration. In this case you need to read the plugin documentation before
clicking on the link "Migrate" to know the possibles consequences.
