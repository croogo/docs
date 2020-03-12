---
title: Create a plugin
---

# Creating a plugin

## Bake

In this example, we will use the `bake` command to create a plugin that
manages Authors and Books.  The following detail how to generate an example
plugin that works with Croogo4.

From command line, bake the initial plugin using the following commands:

**_Make sure you select no 'n' to not overwrite the existing composer.json file When execuring the commands below._**

```sh
bin/cake bake plugin Books
bin/cake migrations create --plugin Books InitialMigration
```

Edit the migration file generated in `plugins/Books/config/Migrations/` and replace the change() method with:

```php
    public function change()
    {
        $this->table('authors')
            ->addColumn('name', 'string')
            ->create();

        $this->table('books')
            ->addColumn('title', 'string')
            ->addColumn('author_id', 'integer')
            ->addForeignKey('author_id', 'authors', ['id'], [
                'constraint' => 'fk_books2authors',
                'delete' => 'RESTRICT',
            ])
            ->create();
    }
```

Proceed with the bake commands as follows:

```sh
bin/cake migrations migrate --plugin Books

bin/cake bake model --plugin Books Authors
bin/cake bake model --plugin Books Books

bin/cake bake controller --plugin Books Authors
bin/cake bake controller --plugin Books Books

bin/cake bake template --plugin Books Authors
bin/cake bake template --plugin Books Books
```

## Configure for use in Croogo

Configure the plugin so Croogo can recognize it:

- Prepare a plugin.json file so that Extension plugin can recognize it Edit `plugin/Books/config/plugin.json`, and put the following:

```json
{
  "name" : "Books",
  "description" : "Croogo Books Example Plugin."
}
```

- Edit `src/Application.php`, in bootstrap() method and remove `$this->addPlugin('Books');`
- Browse to /admin panel, Extensions -> Plugins -> Activate Books plugin
- Browse to **/books/books** and **/books/authors** and see it uses CakePHP default app theme
- you may need to use the command `bin/cake cache clear_all` to clear the cache
- To make the plugin use Croogo current theme, edit the plugins AppController file, eg: `plugins/Books/src/Controller/AppController.php`

Change the parent class from:

`use App\Controller\AppController as BaseController;`

to:

`use Croogo\Core\Controller\AppController as BaseController;`

- In order to view the authors when adding or editing a book, you will need to add the following to the add and edit fucntions in the Books controller:

`plugins/Books/src/Controller/BooksController.php`

Update the add function

```php
public function add()
    {
        $book = $this->Books->newEntity();
        $authors = $this->Books->Authors->find('list'); // Add this line
        if ($this->request->is('post')) {
            $book = $this->Books->patchEntity($book, $this->request->getData());
            if ($this->Books->save($book)) {
                $this->Flash->success(__('The book has been saved.'));

                return $this->redirect(['action' => 'index']);
            }
            $this->Flash->error(__('The book could not be saved. Please, try again.'));
        }
        $this->set(compact('book', 'authors')); // and add this
    }
```
Update the edit function

```php
public function edit($id = null)
    {
        $book = $this->Books->get($id, [
            'contain' => []
        ]);
        $authors = $this->Books->Authors->find('list'); // Add this line
        if ($this->request->is(['patch', 'post', 'put'])) {
            $book = $this->Books->patchEntity($book, $this->request->getData());
            if ($this->Books->save($book)) {
                $this->Flash->success(__('The book has been saved.'));

                return $this->redirect(['action' => 'index']);
            }
            $this->Flash->error(__('The book could not be saved. Please, try again.'));
        }
        $this->set(compact('book', 'authors')); // and add this
    }
```

## Admin Integration

To prepare the plugin for use in Croogo Admin follow the next steps:

- Use the following AppController.php below as template and put it in:

`plugin/Books/src/Controller/Admin/AppController.php`

```php
<?php

namespace Books\Controller\Admin;

use Croogo\Core\Controller\Admin\AppController as BaseController;

class AppController extends BaseController
{

}
```

- Next you will probably need to patch the following file

`vendor/croogo/croogo/Core/src/Template/Bake/Controller/controller.ctp`

With the following

```php
<?php

namespace <%= $namespace %>\Controller<%= $prefix %>;

<% if (class_exists("$namespace\Controller\$prefix\AppController")): %>
use <%= $namespace %>\Controller<%= $prefix %>AppController as CroogoController;
<% else: %>
use Croogo\Core\Controller<%= $prefix %>\AppController as CroogoController;
<% endif; %>

/**
 * <%= $name %> Controller
 *
 * @property \<%= $namespace %>\Model\Table\<%= $defaultModel %>Table $<%= $defaultModel %>
<%
foreach ($components as $component):
    $classInfo = $this->Bake->classInfo($component, 'Controller/Component', 'Component');
%>
 * @property <%= $classInfo['fqn'] %> $<%= $classInfo['name'] %>
<% endforeach; %>
 */
class <%= $name %>Controller extends CroogoController
{
<%
echo $this->Bake->arrayProperty('helpers', $helpers, ['indent' => false]);
echo $this->Bake->arrayProperty('components', $components, ['indent' => false]);
foreach($actions as $action) {
    echo $this->element('Controller/' . $action);
}
%>

}
```

- Once that's done execute the following commands:

```sh

bin/cake bake controller --plugin Books --prefix Admin --theme Croogo/Core Authors
bin/cake bake controller --plugin Books --prefix Admin --theme Croogo/Core Books
bin/cake bake template --plugin Books --prefix Admin --theme Croogo/Core Authors
bin/cake bake template --plugin Books --prefix Admin --theme Croogo/Core Books

```

- To utilise admin routes, you will need to **ADD** the following code to the file:

`plugins/Books/config/routes.php`

```php
Router::plugin('Books', ['path' => '/'], function (RouteBuilder $route) {
    $route->prefix('admin', function (RouteBuilder $route) {
        $route->scope('/books', [], function (RouteBuilder $route) {
            $route->fallbacks();
        });
    });
});
```
- Add the next bit of code to the following files:

`$this->addBehavior('Search.Search');`

`plugins/Books/src/Model/Table/AuthorsTable.php`

```php
public function initialize(array $config)
    {
        parent::initialize($config);

        $this->addBehavior('Search.Search');  // this line
        $this->setTable('authors');
        $this->setDisplayField('name');
        $this->setPrimaryKey('id');

        $this->hasMany('Books', [
            'foreignKey' => 'author_id',
            'className' => 'Books.Books'
        ]);
    }
```
And this

 `plugins/Books/src/Model/Table/BooksTable.php`

```php
public function initialize(array $config)
    {
        parent::initialize($config);

        $this->addBehavior('Search.Search');  // this line
        $this->setTable('books');
        $this->setDisplayField('title');
        $this->setPrimaryKey('id');

        $this->belongsTo('Authors', [
            'foreignKey' => 'author_id',
            'joinType' => 'INNER',
            'className' => 'Books.Authors'
        ]);
    }
```
To access the admin URLs use
`/admin/books/books` and `/admin/books/authors`

## Sidebar

To add the admin URLs to the sidebar navigation in Croogo4 Admin
- Create the following file:
`plugins/Books/config/admin_menu.php`

and add the following code:

```php
<?php

namespace Croogo\Nodes\Config;

use Croogo\Core\Nav;

Nav::add('sidebar', 'books', [
    'icon' => 'edit',
    'title' => __d('croogo', 'Books'),
    'url' => [
        'prefix' => 'admin',
        'plugin' => 'Books',
        'controller' => 'Books',
        'action' => 'index',
    ],
    'weight' => 10,
    'children' => [
        'list' => [
            'title' => __d('croogo', 'Books'),
            'url' => [
                'prefix' => 'admin',
                'plugin' => 'Books',
                'controller' => 'Books',
                'action' => 'index',
            ],
            'weight' => 10,
        ],
        'create' => [
            'title' => __d('croogo', 'Authors'),
            'url' => [
                'prefix' => 'admin',
                'plugin' => 'Books',
                'controller' => 'Authors',
                'action' => 'index',
            ],
            'weight' => 20,
        ],
    ]
]);

```

Again, you will need to clear the cache either via the admin area of using the following command: `bin/cake cache clear_all`

**Your plugin should now be working in both public/frontend and in admin/backend.**