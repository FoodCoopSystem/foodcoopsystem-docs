## Intro

To install FCS first you need to build it. This will be automatead in near future.

## Requirements

Before you start make sure you have

* `drush` (version 5.x+ [installation](http://docs.drush.org/en/master/install/))
* `git` ([installation](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git))

> You can test is on \*nix machine with `which` command. E.g.: `which git`. This should output full path to git command. If there is nothing your system doesn't have it.


## Installation

* Clone repository
    * `cd` to dir where you want to makie app directory
    * Run command in your terminal `git clone git@github.com:FoodCoopSystem/foodcoopsystem.git`
    * `cd foodcoopsystem/app`
* Setup
    1. Run drush make script: `drush make foodcoopsystem.make`
    1. Install default Drupal version (follow installer).
    1. Replace installed new Drupal version with the Database from /database folder.
    1. Run `drush updb`
    1. Run `drush vdel preprocess_css`
    1. Run `drush cc all`
    1. Set **admin** (UID 1) password to your desire one `drush upwd admin --password=secr3tPass`

## Installation (automated version)
 * Prepare your environement. You can use our [docker image](https://github.com/FoodCoopSystem/docker) for that task.
 * `cd` to dir with your codebase. 
 * Add file `app/sites/default/local.settings.php` file and add database details to that file. Example file:
```
<?php
$databases['default']['default'] = array(
  'driver' => 'mysql',
  'database' => 'foodcoop',
  'username' => 'root',
  'password' => 'root',
  'host' => 'db',
  'prefix' => '',
);
```
 * Execute build script: `./scripts/rebuild_directory_local.sh`.
