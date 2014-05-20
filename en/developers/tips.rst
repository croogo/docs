Tips
####

Make it faster
==============

Debug Setting
-------------

Croogo is shipped with debug level 1 enabled. You can disable it in `/app/Config/croogo.php` to make it faster. Replace line 37 with this::

    Configure::write('debug', 0);

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

Debugging
=========

DebugKit
--------

Install DebugKit into `Plugin/DebugKit`::

    git clone http://github.com/cakephp/debug_kit Plugin/DebugKit

Activate DebugKit plugin::

    Console/cake ext activate plugin -f DebugKit

Hook the ToolbarComponent to all controllers::

    // Config/bootstrap.php
    Croogo::hookComponent('*', 'DebugKit.Toolbar');

Blackholed Request
------------------

Debugging blackholed requests can be tricky. The first thing that you should
do if you get blackholed requests is to check your ``tmp/logs/error.log`` file.
A simple syntax error or a ``PDOException`` may have triggered the blackhole
callback.

In some cases, the request may cause an infinite loop.  If you get this
problem, clear out your ``error.log`` and re-do the request.  If the problem is
logged, it would be in the first few lines of this file.

Secondly, verify that:

    * Your input fields are created using the FormHelper
    * Your forms are closed using FormHelper::end()
    * Your form is created with `type` => 'file' if you're working with file uploads
    * You are not using nested forms