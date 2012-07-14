Roadmap
#######

- Plugin download/finder via shell (the CPM - package management idea)
- Default theme: use Twitter Bootstrap
- Admin theme: use Twitter Bootstrap here too?
- Node Preview indicator, display published nodes that has preview flag set for admins.
- Defaults to InnoDb storage engine for mysql
- Plugin Activation ordering and presentation in plugin list
- Migration plugin (cakedc) can be use for installation, and plugins. create and update tables between versions, setup default/baseline data [http://croogo.lighthouseapp.com/projects/32818/tickets/258]
- Helpers to create UI components markups, eg: tabs, accordion, panels. Mostly for /admin
- Pluginify the File Manager, add better folder security
- Pluginify Blocks
- Pluginify Taxonomy
- Replace Email Component with CakeEmail and move to models
- Move functionality in NodesController to the model
- Move CommentsController::add() functionality to model
- Move AttachmentsController::admin_add functionality to model
- Move non-controller CroogoComponent functionality to a Lib
- Pluginify User management (extract as plugin), allow integration of third party auth, eg: twitter oauth, facebook, ldap,
- Replace Config/settings.yml to Config/settings.json, remove spyc from Vendor
