---
title: Composer and Drupal 8
date: '2018-01-24 09:36:18 -0700'
tags: drupal, composer
---

Composer + Drupal 8 = Awesome

## Useful links

* [Using Composer to manage Drupal site dependencies](https://www.drupal.org/docs/develop/using-composer/using-composer-to-manage-drupal-site-dependencies)
* [Tips from Lullabot](https://www.lullabot.com/articles/drupal-8-composer-best-practices)
* [Tips for Managing Drupal 8 projects with Composer](https://www.jeffgeerling.com/blog/2017/tips-managing-drupal-8-projects-composer)
* [Updating drupal/core with Composer - but Drupal core doesn't update](https://www.jeffgeerling.com/blog/2018/updating-drupalcore-composer-drupal-core-doesnt-update)

## Common commands

Check for outdated:
```bash
composer outdated
```

Update Drupal core:
```bash
composer update drupal/core --with-dependencies
```

Update single module:
```bash
composer update drupal/MODULE_NAME --with-dependencies
```
