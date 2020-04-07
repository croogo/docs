---
title: Create a plugin
---

# Creating a plugin

In this example, we use Bake to create a Croogo4 plugin that manages Books and Authors.

## Bake the Schema

We start by creating the plugin skeleton and the books and authors tables.

- First, we bake the plugin:
  ```sh
  bin/cake bake plugin --theme Croogo/Core Books
  ```
  **_Make sure to select no ['n'] when asked to overwrite the existing composer.json file._**

  Bake automatically activated our new plugin in the src/Application.php file, but this overrides Croogo's ability to enable and disable the plugin, so we'll need to reverse this by running the following command:
  ```sh
  bin/cake plugin unload Books
  ```
- Then, we activate it manually in Croogo's admin interface:
  - We load our app's `/admin` panel, and see the default Dashboard for our new plugin.
  - Then navigate to Extensions -> Plugins and find our new plugin in the list.
  - Activate the plugin by clicking on the lightning bolt.
- Next, we create a blank initial migration, and edit the change() method:
  ```sh
  bin/cake migrations create --plugin Books BooksInitialMigration
  ```
  `plugins/Books/config/Migrations/` 
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
- Then we load the database and generate our models, being sure to specify the Croogo theme:
  ```sh
  bin/cake migrations migrate --plugin Books
  bin/cake bake model --plugin Books --theme Croogo/Core Authors
  bin/cake bake model --plugin Books --theme Croogo/Core Books
  ```

## Configure the Croogo Admin Interface

We always need to perform full CRUD as an administrator, so to get testing in on all the features, it's best to start with the backend.

- By specifying the theme and the prefix, we bake the controllers and templates we need.

  ```sh
  bin/cake bake controller --plugin Books --prefix Admin --theme Croogo/Core Authors
  bin/cake bake controller --plugin Books --prefix Admin --theme Croogo/Core Books
  bin/cake bake template --plugin Books --prefix Admin --theme Croogo/Core Authors
  bin/cake bake template --plugin Books --prefix Admin --theme Croogo/Core Books
  ```
- Now, browse to `/admin/books/books` and `/admin/books/authors` and confirm the following:
  - it uses the Croogo/Core admin theme,
  - the index is displayed by default,
  - add, edit, view and delete operate as expected.

- In case the author's name does not appear in any or just some of the book views (index, view, add or edit), we need to check a couple of things:
  - If the model baking got confused about what the displayField should be, it will default to 'id'. So if we were seeing the author's id instead of their name when looking at a book record, we would need to ensure the displayField was set correctly in the Authors Table as shown below. A similar check should be made in the BooksTable.php file as well.

    `plugins/Books/src/Model/Table/AuthorsTable.php`
    ```php
    $this->setTable('authors');
    $this->setDisplayField('name');
    $this->setPrimaryKey('id');
    ```
  - Croogo uses the FriendsOfCake/Crud plugin to simplify much of the standard controller crud functions. Many of the actions are mapped to custom Croogo admin actions, however the view action is not, and the standard Crud View action is used. There, the query performs a find('all') method, but does not contain() any other tables by default. Therefore, the author record is not included. To correct this, we can listen to the beforeFind event from the Crud component and add the contain() as shown below:

    `plugins/Books/src/Controller/Admin/BooksController.php`
    ```php
    public function view($id = null)
    {
        $this->Crud->on('beforeFind', function(\Cake\Event\Event $event) {
            $event->getSubject()->query->contain(['Authors']);
        });
        return $this->Crud->execute();
    }
    ```
## Configure the Croogo Frontend

Now that we know the backend works, the frontend is easy.

- We bake again, this time leaving off the `--prefix` and `--theme` options. The standard Cake theme is used here to keep things simple.

  **_One significant difference between using the Cake theme and the Croogo theme is the Crud component. If you find your frontend needs the capabilities of Crud, then go for it, but that is beyond the scope of this guide._**
  ```sh
  bin/cake bake controller --plugin Books Authors
  bin/cake bake controller --plugin Books Books
  bin/cake bake template --plugin Books Authors
  bin/cake bake template --plugin Books Books
  ```
  Let's clear the cache
  ```sh
  bin/cake cache clear_all
  ```

- Browse to `/books/books` and `/books/authors` and see each uses the Croogo app theme.
  - Note that the styling and alignment of the buttons and data rows are not as desired, so we would need to account for that in our plugin's styling which is beyond the scope of this guide.
  - Also note that even though we didn't specify the Croogo/Core theme when baking the controllers, the Croogo view theme gets set in the Croogo controller extended by our plugin's AppController.

    `plugins/Books/src/Controller/AppController.php`
    ```php
    use Croogo\Core\Controller\AppController as CroogoController;

    class AppController extends CroogoController
    ```

- **_Your plugin should now be working in both public/frontend and in admin/backend._**

## Sidebar

Customize the sidebar navigation in the Croogo4 Admin UI to more easily get to our Book and Author indexes.

- We customize the menu in the generated config file by copying the default 'child' entry and modifying them for our Books and Authors controllers:

  `plugins/Books/config/admin_menu.php`
  ```php
  ...

  Nav::add('sidebar', 'books', [

  ...

      'children' => [
          'books' => [
              'title' => __d('croogo', 'Books'),
              'url' => [
                  'prefix' => 'admin',
                  'plugin' => 'Books',
                  'controller' => 'Books',
                  'action' => 'index',
              ],
              'weight' => 10,
          ],
          'authors' => [
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

- Again, we clear the cache:

  `bin/cake cache clear_all`

## Other Notes
- References to Croogo Models
  - If your plugin contains references to models outside of it's namespace (like the Croogo Users table for example), the standard baked Table files will need to be modified manually.
Here is an example of a Jobs plugin with Jobs that get claimed by Croogo Users. When baked, it looks like this:
    ```php
    $this->belongsTo('Users', [
        'foreignKey' => 'claimed_by_id',
        'className' => 'Jobs.Users',
    ]);
    ```
  - But the Jobs plugin does not contain a Users model. Instead, it should be changed to look like this:
    ```php
    $this->belongsTo('Users', [
        'foreignKey' => 'claimed_by_id',
        'className' => 'Croogo/Users.Users',
    ]);
    ```
- Croogo Dashboards
  - The Croogo plugin bake theme includes a simple Croogo dashboard ready for customization. They use Cake cells, so if you are familiar with those, dashboards will be simple.