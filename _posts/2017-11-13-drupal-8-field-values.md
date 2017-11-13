---
title: Accessing Drupal 8 field values
date: '2017-11-13 12:36:33 -0700'
tags: drupal
---

Getting field values can be a pain sometimes.

## Entity (node, taxonomy term, etc) objects

```php
<?php
$node->get('field_name')->value;
```
