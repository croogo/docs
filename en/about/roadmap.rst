.. role:: strike
   :class: strike

Roadmap
#######

The task lists described in this page is outdated.
All tasks, bugs, scheduled releases are now tracked in github:

    https://github.com/croogo/croogo/milestones

2.0.x
-----

- :strike:`Fully Pluginize: Croogo can become a set of plugins and a minimalist app that simply installs the default plugin set for easy installation.` **(shama, real34, rchavik)**
- Add namespaces
- PSR-0 and PSR-1 Compat
- Use composer.json instead of Config/plugin.json for extensions
- Offer RESTful API by core, to allow easy integration with third-party apps (could be an iPhone app too)
- Allow admins to update Croogo from admin panel (HTTP download, or backed by Git?)
- :strike:`Granular ACL` **(rchavik)**
- [Plugin] Contents: Nodes going out, forming a Contents plugin.

1.5.2
-----
- Going stable
- Doc updates

1.5.1
-----
- :strike:`Plugin Activation ordering and presentation in plugin list`
- :strike:`Helpers to create UI components markups, eg: tabs, accordion, panels.  Mostly for /admin` **(aymeric and real34 - occitech)**
- :strike:`Replace Email Component with CakeEmail and move to models`
- :strike:`Move functionality in NodesController to the model`

1.5.0
-----

- Plugin download/finder via shell (the CPM - package management idea)
- :strike:`Default theme: use Twitter Bootstrap` (default theme will not be changed)
- :strike:`Admin theme: use Twitter Bootstrap here too?` **(aymeric and real34 - occitech)**
- Node Preview indicator, display published nodes that has preview flag set for admins.
- :strike:`Defaults to InnoDb storage engine for mysql`
- :strike:`Migration plugin (cakedc) can be use for installation, and plugins. create and update tables between versions, setup default/baseline data [http://croogo.lighthouseapp.com/projects/32818/tickets/258]` **(aymeric and real34 - occitech)**
- :strike:`Pluginify the File Manager, add better folder security` **(shama)**
- :strike:`Pluginify Blocks` **(shama)**
- :strike:`Pluginify Taxonomy` **(shama)**
- :strike:`Move CommentsController::add() functionality to model`
- :strike:`Move AttachmentsController::admin_add functionality to model`
- :strike:`Move non-controller CroogoComponent functionality to a Lib`
- :strike:`Pluginify User management (extract as plugin)` **(rchavik)**
- Allow integration of third party auth, eg: twitter oauth, facebook, ldap,
- :strike:`Replace Config/settings.yml to Config/settings.json, remove spyc from Vendor` **(rchavik)**
