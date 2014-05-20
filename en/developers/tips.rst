Tips
####

Make it faster
==============

Debug Setting
-------------

Croogo is shipped with debug level 1 enabled. You can disable it in `/app/Config/croogo.php` to make it faster. Replace line 37 with this::

    Configure::write('debug', 0);

DebugKit
--------

Install DebugKit into `Plugin/DebugKit`::

    git clone http://github.com/cakephp/debug_kit Plugin/DebugKit

Activate DebugKit plugin::

    Console/cake ext activate plugin -f DebugKit

Hook the ToolbarComponent to all controllers::

    // Config/bootstrap.php
    Croogo::hookComponent('*', 'DebugKit.Toolbar');

Symlink plugin and theme assets
-------------------------------

By creating a symlink in the ``DocumentRoot``, we bypass Croogo and files
are served directly by the webserver.

Linking a theme asset directory::

    mkdir -p croogo-app/webroot/theme
    cd croogo-app/webroot/theme
    ln -s ../../View/Themed/MyTheme/webroot MyTheme

Linking a plugin asset directory::

    cd croogo-app/webroot/
    ln -s ../Plugin/Gallery/webroot Gallery