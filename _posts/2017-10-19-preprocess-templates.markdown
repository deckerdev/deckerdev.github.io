---
title: Preprocessing Drupal Templates
date: '2017-10-19 16:15:00 -0700'
tags: drupal
---

Snippets relating to Drupal preprocess functions.

## Preprocess nodes:

Drupal 7:
```php
<?php
function THEME_preprocess_node(&$vars) {
  $type = $vars['type'];
  $mode = $vars['view_mode'];
  $node = $vars['node'];

  // Bundle-specific preprocess functions, like
  // THEME_preprocess_node__page() or THEME_preprocess_node__story().
  $function = __FUNCTION__ . '__' . $node->type;
  if (function_exists($function)) {
    $function($vars);
  }
}
```

Drupal 8:
```php
<?php
function military_preprocess_node(&$variables) {
  /** @var \Drupal\node\NodeInterface $node */
  $node = $variables['node'];

  // Bundle-specific preprocess functions.
  $function = __FUNCTION__ . '__' . $node->bundle();
  if (function_exists($function)) {
    $function($variables);
  }
}
```
