Object Inheritance
##################

Croogo follows established standards for how to integrate custom functionality into a `CakePHP <http://cakephp.org/>`_ application. To those already familiar with the object inheritance of CakePHP, learning where the Croogo classes fit in should feel quite natural. And since Croogo is implemented almost entirely as a set of `CakePHP Plugins <http://book.cakephp.org/2.0/en/plugins.html>`_, it is important to include those in the explanation.

All requests to a Croogo app come in the form of /plugin/controller/action along with any additional parameters that might be necessary. This url gets parsed, the specific plugin and controller is located and its action is dispatched. For example, /menus/links/index will locate the Menus plugin, load the LinksController class found there and dispatch the index action. Each controller layer exists to contain increasing levels of custom functionality that carries out the activities once dispatched. The following inheritance list of the controllers in the Menus plugin display their ancestry.

    * `Controller` *(/myapp/Vendor/cakephp/cakephp/lib/Cake/Controller/)*
        * `CroogoAppController` *(/myapp/Vendor/croogo/croogo/Croogo/Controller/)*
            * `AppController` *(/myapp/Controller/)*
                * `MenusAppController` *(/myapp/Vendor/croogo/croogo/Menus/Controller/)*
                    * `LinksController` *(/myapp/Vendor/croogo/croogo/Menus/Controller/)*
                    * `MenusController` *(/myapp/Vendor/croogo/croogo/Menus/Controller/)*

Controller
""""""""""

At the root of the list is the CakePHP Controller which provides the base functionality of dispatching requests and interacting with Models, Views, Components and many other utility classes. *All* controllers within a Croogo application inherit this class. You will never modify this file unless your intention is to submit your changes back to the CakePHP repository (or you are simply changing things to better understand how Cake works). But you should certainly never release non-standard CakePHP code for production use.

CroogoAppController
"""""""""""""""""""

This controller extends CakePHP's Controller and performs much of the activity required to make Croogo what it is. This includes User auth, Theme setup, Settings load, custom Event callbacks, View fallbacks, and more. Similar to the CakePHP code, you will not modify this file unless your intention is to submit your changes back to the Croogo repository.

AppController
"""""""""""""

This controller extends the CroogoAppController and performs any actions that are applicable to *all* the controllers used in your entire application. This includes any controllers located in the /myapp/Controller/ directory, as well as any standard or custom plugins enabled in your app. This file can be modified without limits as needed for your application. As is typical in OOP, when subclassing, function overrides will usually contain a call to the parent function to include whatever activities are required at the higher level. This guideline can certainly be ignored when those activities are exactly what you are trying to change.

MenusAppController
""""""""""""""""""

Similar in function to the AppController, the MenusAppController is different only in its scope of applicability. Instead of being inherited by all controllers within the entire app, it is inherited by only the controllers within the Menus plugin.

.. NOTE:: Functionally, although not syntactically, code contained within a <plugin>AppController, and code contained within a <plugin>Component are equivalent. It is all used to keep your code `DRY <http://book.cakephp.org/2.0/en/appendices/glossary.html>`_. Typically, you should put your logical code within the Component, and only place code within the AppController when necessary to hook in at a specific point within the dispatching flow. This is especially true if the logic you write might be useful *outside* the plugin since it is very easy to include a Component from one plugin into another.

LinksController and MenusController
"""""""""""""""""""""""""""""""""""

Finally, the LinksController and MenusController both extend the MenusAppController and contain the functions specific to managing the hyperlinks and the menus within Croogo. Since Menus is a core Croogo plugin, its code should not be modified for production use, but understanding the structure will help immensely when creating your own custom :doc:`plugin<plugins>`.
