Events
######

Croogo dispatches several custom events. These events are useful to
customize the default behaviors.

Available events
================

Bootstrap
---------

- **Croogo.beforeSetupAdminData**

  Triggered at the end of ``Controller::beforeFilter()`` when the current
request is an administrator session

- **Croogo.bootstrapComplete**

  Triggered at the end of bootstrap cycle.  All plugins have been loaded, but
  before routes is loaded.

- **Croogo.setupAdminData**

  Triggered at ``Helper::beforeRender()`` when the current request is an
  administrator session. Complementary to Croogo.beforeSetupAdminData

Model
-----

- **Model.Node.afterSaveNode**

  Trigger before a Node is saved

- **Model.Node.beforeSaveNode**

  Trigger after a Node is saved

View
----

- **Helper.Layout.afterFilter**

  Triggered before a block is rendered (via call to ``LayoutHelper::filter()``
  in element ``Blocks/View/Elements/block.ctp``, and calls to
  ``LayoutHelper::snippet()``)

- **Helper.Layout.beforeFilter**

  Triggered before a block is rendered (via call to ``LayoutHelper::filter()``
  in element ``Blocks/View/Elements/block.ctp``, and calls to
  ``LayoutHelper::snippet()``)

- **Helper.Nodes.afterSetNode**

  Triggered at the start of ``NodesHelper::set()``

- **Helper.Nodes.beforeSetNode**

  Triggered at the end of ``NodesHelper::set()``

- **Helper.Regions.afterSetBlock**

  Triggered before rendering of block in ``RegionsHelper::blocks()``

- **Helper.Regions.beforeSetBlock**

  Triggered after rendering of block in ``RegionsHelper::blocks()``

Controller
----------

- **Controller.Links.setupLinkChooser**

- **Controller.Nodes.afterAdd**

- **Controller.Nodes.afterEdit**

- **Controller.Users.activationFailure**

- **Controller.Users.activationSuccessful**

- **Controller.Users.adminLoginFailure**

- **Controller.Users.adminLoginSuccessful**

- **Controller.Users.adminLogoutSuccessful**

- **Controller.Users.afterLogout**

- **Controller.Users.beforeAdminLogin**

- **Controller.Users.beforeLogin**

- **Controller.Users.beforeLogout**

- **Controller.Users.loginFailure**

- **Controller.Users.loginSuccessful**

- **Controller.Users.registrationFailure**

- **Controller.Users.registrationSuccessful**

Miscellaneous
-------------

- **Croogo.Status.setup**

- **Croogo.Status.status**
