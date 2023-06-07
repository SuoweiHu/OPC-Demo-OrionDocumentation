---

sidebar_position: 2
title: "Package Manager"
---

## What composer handles?

When installing the given `composer.json` some tasks are taken care of:

* Drupal will be installed in the `web`-directory.
* Autoloader is implemented to use the generated composer autoloader in `vendor/autoload.php`,
  instead of the one provided by Drupal (`web/vendor/autoload.php`).
* Modules (packages of type `drupal-module`) will be placed in `web/modules/contrib/`
* Themes (packages of type `drupal-theme`) will be placed in `web/themes/contrib/`
* Profiles (packages of type `drupal-profile`) will be placed in `web/profiles/contrib/`
* Creates the `web/sites/default/files`-directory.
* Latest version of [Drush](https://www.drush.org/latest/) is installed locally for use at `vendor/bin/drush`.
* Latest version of [Drupal Console](http://www.drupalconsole.com) is installed locally for use at `vendor/bin/drupal`.
* The correct scaffolding for your Drupal core version is installed, along with Lagoon-specific scaffolding from [amazeeio/drupal-integrations](https://github.com/amazeeio/drupal-integrations) project and the `assets/` directory in this repo.  For more information see [drupal/core-composer-scaffold](https://github.com/drupal/core-composer-scaffold)