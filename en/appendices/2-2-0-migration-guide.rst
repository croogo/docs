2.2.0 Migration Guide
#####################

Dashboards plugin
=================

When updating your Croogo installation to version 2.2.0, the Dashboards plugin
will not be active. To activate this plugin::

    Console/cake ext activate plugin -f Dashboards
    Console/cake migrations.migration run -p Dashboards up

View Files
==========

The `LayoutHelper::cssClass()` method, `$themeSettings` and `$_icons`
view variables introduced in version 2.1.1 has been deprecated.

A new helper `ThemeHelper` class has been added to access theme configuration
values.

If your existing theme use any of these variable, you can use the following `find` and `sed` commands listed below to update your view files.

Replace usage of `->Layout->cssClass` to `->Theme->getCssClass`::

    find /path/to/theme \
        -type f \
        -name "*.ctp" \
        -exec sed -i 's/->Layout->cssClass/->Theme->getCssClass/g' {} \;

Change usage of `$_icons['home']` to `$this->Theme->getIcon('home')`::

    find path/to/theme \
        -type f \
        -name "*.ctp" \
        -exec sed -i "s/\$_icons\[\(.*\)\]/\$this->Theme->getIcon(\1)/" {} \;
