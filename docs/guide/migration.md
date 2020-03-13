---
title: Migrating from &lt; 4.x
---

There is no fully automatic approach to migrate a
 project to _Croogo 4.x_ at the moment, but this must be done
 manually using one of these main approaches:
1) Migrate an existing installation by changing the source files
and bumping version in the `composer.json` file.
2) Create a new project from scratch and start migrating the
database contents and any custom code to the newly installed project.

Both approaches will have their pros and cons and it will depend a lot on
each single case, which of them suit your purpose better.

If migrating from Croogo 2.x to 4.x there are so many differences
in name conventions, database schema, etc. that the second approach
seems the more robust path to follow, given that you can start from a working
environment and continue step-by-step through the migration.


So for now we'll be exclusively handling the second approach and install
a new project from scratch and start from there.

TODO: add some links to how to manage the first approach.

# Installation
This step assumes you already have `composer` and necessary `php`-extensions
in your system.

First create a new database for your new application.

*TODO: add some steps to install mysql db? or just a link to
official docs?*

Now create a new project under `my-app` directory with composer and
run the development server and follow the steps to initialize the
database and admin user:

```shell
$ composer create-project croogo/app my-app
$ bin/cake server
```
Now open the page on your localhost or use a vhost if you're doing
this from a development server and follow the instructions.

If everything went right, you now have a running installation of _Croogo_!

# Schema Migration

# Data Migration

## Content

## Users
