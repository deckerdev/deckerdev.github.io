---
title: Drupal and Twig
date: '2017-10-25 16:00:00 -0700'
tags: drupal
---

A collection of resources for Drupal 8 and Twig.

## General Twig

* [Official reference](https://twig.symfony.com/doc/2.x/#reference): tags, filters, functions, etc

## Drupal Twig

* [Starting point on Drupal.org](https://www.drupal.org/docs/8/theming/twig)
* [Drupal specific filters](https://www.drupal.org/docs/8/theming/twig/filters-modifying-variables-in-twig-templates)
* [Drupal specific functions](https://www.drupal.org/docs/8/theming/twig/functions-in-twig-templates)
* [Twig overview](https://sqndr.github.io/d8-theming-guide/twig/twig-basics.html) from _The Drupal 8 Theming guide_

## Drupal Modules that extend Twig

* [Twig tweak](https://www.drupal.org/project/twig_tweak)
  * [Cheatsheet](https://www.drupal.org/docs/8/modules/twig-tweak/cheat-sheet-8x-2x)
* [Twig field value](https://www.drupal.org/project/twig_field_value)
* [Twig extensions](https://www.drupal.org/project/twig_extensions)
* [Twig extender](https://www.drupal.org/project/twig_extender)
* [Themable forms](https://www.drupal.org/project/themable_forms)

## Snippets

Get the value from a `List (text)` field:
{% raw %}
```twig
{{ content.field_text_list['#items'].getString() }}
```
{% endraw %}

Traverse a multi-valued field:
{% raw %}
```twig
{# yes, the following syntax sucks! see https://www.drupal.org/node/2776307 #}
{% set links = [] %}
{% for key, link in content.field_links if key|first != '#' %}
  {% set links = links|merge([ link ]) %}
{% endfor %}
```
{% endraw %}

Get the value from a `text` field:
{% raw %}
```twig
{{ node.field_text.value }}
{{ node.field_text.value|striptags }}
```
{% endraw %}
