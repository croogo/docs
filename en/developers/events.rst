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

  Triggered by the Menus plugin before displaying the link chooser dialog

- **Controller.Nodes.afterAdd**

  Triggered by the NodesController after a node was successfully added

- **Controller.Nodes.afterEdit**

  Triggered by the NodesController after a node was successfully edited

- **Controller.Users.activationFailure**

  Triggerred when a user failed to be activated

- **Controller.Users.activationSuccessful**

  Triggerred when a user has been successfully activated

- **Controller.Users.adminLoginFailure**

  Triggerred when a administrator user has failed to login

- **Controller.Users.adminLoginSuccessful**

  Triggerred when a administrator user has login successfully

- **Controller.Users.adminLogoutSuccessful**

  Triggerred when a administrator user has logout successfully

- **Controller.Users.afterLogout**

  Triggerred when a user has logout successfully

- **Controller.Users.beforeAdminLogin**

  Triggerred before the admin login screen is rendered

- **Controller.Users.beforeLogin**

  Triggerred before the login screen is rendered

- **Controller.Users.beforeLogout**

  Triggerred before a user is logged out

- **Controller.Users.loginFailure**

  Triggerred when a user has failed to login

- **Controller.Users.loginSuccessful**

  Triggerred when a user has login successfully

- **Controller.Users.registrationFailure**

  Triggerred when a user has failed registration

- **Controller.Users.registrationSuccessful**

  Triggerred when a user has successfully registered

Miscellaneous
-------------

- **Croogo.Status.setup**

  Triggerred when the CroogoStatus is instantiated.

- **Croogo.Status.status**

  Triggerred before statuses are retrieved.
