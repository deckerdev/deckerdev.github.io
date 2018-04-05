---
layout: default
---

## Posts:
<ul>
  {% for post in site.posts %}
    <li class="teaser">
      <a href="{{ post.url | absolute_url }}">
        {{ post.title }}
      </a>
      <div>
        {{ post.excerpt | strip_html }}
      </div>
    </li>
  {% endfor %}
</ul>
