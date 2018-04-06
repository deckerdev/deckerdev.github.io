---
title: Drupal 8 and BrowserSync
date: '2017-11-13 12:42:21 -0700'
tags: drupal
---

Getting BrowserSync to properly reload in Drupal 8.



## In THEME_NAME.theme

```php
<?php
use Drupal\Core\Site\Settings;

/**
 * Implements hook_css_alter().
 */
function THEME_NAME_css_alter(&$css) {
  // Enable the ability to toggle <link> as opposed to <style> @import during
  // development via settings.local.php variable. This will allow tools like
  // BrowserSync and LiveReload to work properly.
  $dev_enabled = Settings::get('use_dev_css');
  if (isset($dev_enabled) && $dev_enabled === TRUE) {
    foreach ($css as $key => $value) {
      $css[$key]['preprocess'] = FALSE;
    }
  }
}
```

## In settings.local.php

```php
<?php
$settings['use_dev_css'] = TRUE;
```
