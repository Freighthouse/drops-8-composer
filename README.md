# Packaged with KSS Node for Zurb Foundation

https://github.com/kalamuna/kss-foundation

https://github.com/kss-node/kss-node/wiki/Quick-Start-Guide

# Example Drops 8 Composer

This repository can be used to set up a Composer-Managed Drupal 8 site on [Pantheon](https://pantheon.io).

[![CircleCI](https://circleci.com/gh/pantheon-systems/example-drops-8-composer.svg?style=svg)](https://circleci.com/gh/pantheon-systems/example-drops-8-composer)

## Installation

This project can either be used as an upstream repository, or it can be set up manually.

### As an Upstream

Create a custom upstream for this project following the instructions in the [Pantheon Custom Upstream documentation](https://pantheon.io/docs/custom-upstream/). When you do this, Pantheon will automatically run composer install to populate the web and vendor directories each time you create a site.

### Manual Setup

Start off by creating a new Drupal 8 site; then, before installing Drupal, set your site to git mode and do the following from your local machine:
```
$ git clone git@github.com:pantheon-systems/example-drops-8-composer.git my-site
$ cd my-site
$ composer prepare-for-pantheon
$ composer install
$ composer drupal-scaffold
$ git add -A .
$ git commit -m "web and vendor directory from composer install"
$ git remote set-url origin ssh://ID@ID.drush.in:2222/~/repository.git
$ git push --force origin master
```
Replace my-site with the name that you gave your Pantheon site, and replace ssh://ID@ID.drush.in:2222/~/repository.git with the URL from the middle of the SSH clone URL from the Connection Info popup dialog on your dashboard.

### Installing Drupal

Note that this example repository sets the installation profile to 'standard' in settings.php, so that the installer will not need to modify the settings file. If you would like to install a different profile, modify settings.php appropriately before installing your site.

## Updating Your Site

When using this repository to manage your Drupal 8 site, you will no longer use the Pantheon dashboard to update your Drupal version. Instead, you will manage your updates using Composer. Updates can be applied either directly on Pantheon, by using Terminus, or on your local machine.

### Update with Terminus

Install [Terminus 0.13.4](https://github.com/pantheon-systems/terminus/releases/tag/0.13.4) and the [Terminus Composer plugin](https://github.com/rvtraveller/terminus-composer).  Then, to update your site, ensure it is in SFTP mode, and then run:
```
terminus composer update --site=sitename --env=dev
```
Other commands will work as well; for example, you may install new modules using `terminus composer require`.

### Update on your local machine

You may also place your site in Git mode, clone it locally, and then run composer commands from there.  Commit and push your files back up to Pantheon as usual.
