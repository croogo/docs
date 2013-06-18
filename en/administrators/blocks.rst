Blocks
######

Blocks are what you see in the sidebar (‘right’ region in default theme) as boxes. They belong to a particular region.

Elements
========

All blocks are rendered via block.ctp element (found in app/Plugin/Blocks/View/Elements/block.ctp). You can use your own element too for your blocks by editing 'element' field when adding a block.

Tip: If it is a plugin element, enter 'PluginName.element_name'.

How to display a THIS and THAT in a block?
==========================================

You are able to show an element, menu, vocabulary (nested list of terms), or a list of nodes by entering specially formatted text in your block’s body.

Element
-------

For an element with file name my_element.ctp:

    [element:my_element] OR [e:my_element]

Passing variables to your element:

    [element:my_element myVar="value here" anotherVar="value here"]

For plugin elements:

    [element:my_element plugin="my_plugin"]

Menu
----

For a Menu with alias main:

    [menu:main] OR [m:main]

Advanced

``This options could drastically change the way your website works, handle with caution``

Variables supported:

* tag="htmlTag" : tag to wrap content output
* tagAttributes="className" : class name for wrapping tag
* selected="selected" : class for the selected element
* dropdown="false" : Dropdown menu
* dropdownClass="sf-menu" : Class for dropdown menus
* element="Menus.menu" : Element to use as template

Vocabulary
----------

For a Vocabulary with alias categories:

    [vocabulary:categories] OR [v:categories]

Advanced

``This options could drastically change the way your website works, handle with caution``

Variables supported :

* link="true" : if true, it creates a link for each vocabulary found, it will create the link using the supplied arguments for plugin, controller, action and type.
* plugin="nameOfPlugin" : plugin name supplied to create link
* controller="controller" : controller name supplied to create link
* action="action" : action name supplied to create link
* type="type" : type of node supplied to create link
* tag="htmlTag" : tag to wrap content output
* tagAttributes="className" : className for wrapping tag
* element="Taxonomy.vocabulary" : Element to use as template

Nodes
-----

For example, you want to show a list of 5 most recent blog posts as a block:

    [node:recent_posts conditions="Node.type:blog;Node.status:1" order="Node.id DESC" limit="5"]

Advanced

``This options could drastically change the way your website works, handle with caution``

Variables supported :

* link="true" : if true, it creates a link for each node found, it will create the link using the supplied arguments for plugin, controller, action and type.
* plugin="nodes" : plugin name supplied to create link
* controller="nodes" : controller name supplied to create link
* action="view" : action name supplied to create link
* element="Nodes.node_list" : Element to use as template
