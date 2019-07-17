---
currentMenu: file
---

# File structure
The recommended file structure is set up like this:
```bash
.
├── config
│    ├── environments
│    │   ├── development.php
│    │   ├── production.php
│    │   └── staging.php
│    └── environment.php
├── lib
│    ├── Model
│    ├── Routes
│    └── Template
│        └── Helper
├── project
│    ├── templates
│    ├── translations
│    └── db
│        ├── blueprints
│        ├── controls
│        └── pages
└── public
     ├── .htaccess
     ├── index.php
     └── assets
         ├── images
         ├── scripts
         └── styles
```

##### Top level directories:
* [Config](#config)
* [Lib](#lib)
* [Project](#project)
* [Public](#public)

### Config
Environments configuration.
An environment variable is a dynamic-named value that can affect the way running processes will behave on a website. They are part of the environment in which a process runs.

___

### Lib
* [Model](#model)
* [Routes](#routes)
* [Template](#template) (helpers)

##### Model
<!-- @TODO -->
Manager configuration.
* Abstract model
* Spaces model
* Users model

##### Routes
<!-- @TODO -->
Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.

##### Template
<!-- @TODO -->
Directory of template helpers.
* CSRF
* Flash

___

### Project
Templates, translations and database data.
* [Templates](#templates)
* [Translation files](#translations)
* [Database imports](#database-imports)

##### Templates
Collection of all your template files; containers, layouts and macros.


##### Translations
Translation files. A separate file for every language you choose the support.

##### Database imports
Database imports are entirely optional, they are JSON files used to implement pre-written data directly into the Mongo database.
Blueprints, controls and pages.
___

### Public
The public folder generally contains the following content:

##### htaccess
htaccess is a configuration file for use on web servers running the Apache Web Server software. When a .htaccess file is placed in a directory which is in turn 'loaded via the Apache Web Server', then the .htaccess file is detected and executed by the Apache Web Server software. These .htaccess files can be used to alter the configuration of the Apache Web Server software to enable/disable additional functionality and features that the Apache Web Server software has to offer. These facilities include basic redirect functionality, for instance if a 404 file not found error occurs, or for more advanced functions such as content password protection or image hot link prevention.

##### Index file
The index page is the URL or local file that automatically loads when a web browser starts and when the browser's 'home' button is pressed. The term is also used to refer to the front page, web server directory index, or main web page of a website of a group, company, organization, or individual.
```php
defined('ROOT_PATH') || define('ROOT_PATH', dirname(__DIR__));

require '../vendor/autoload.php';

$platform = new \Frontender\Core\App();
$platform
    ->init()
    ->start();
```

##### Assets
All other files that are not related to the sections above. Some examples:
* Styles
* Scripts
* Fonts
* Images
* Other media (e.g. videos)
