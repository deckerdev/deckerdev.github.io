---
title: Javascript Behavior Templates for Drupal
date: '2017-10-19 16:15:00 -0700'
tags: drupal, javascript
---

Templates for quickly starting javascript behaviors (for Drupal)

Drupal 7:
```javascript
(function($, Drupal) {

  'use strict';

  // Description
  Drupal.behaviors.nameOfBehavior = {
    attach: function (context, settings) {

      // Code here.

    }
  };

})(jQuery, Drupal);
```

Drupal 8 (ES6):
```javascript
'use strict';

(function ($, Drupal) {

  // Description
  Drupal.behaviors.nameOfBehavior = {
    attach: (context, settings) => {

      // Code here.

    }
  };

})(jQuery, Drupal);
```
