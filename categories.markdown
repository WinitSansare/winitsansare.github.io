---
layout: page
title: Categories
---

<ul>
  {% for category in site.categories %}
    <li><a href="#{{ category[0] | slugify }}">{{ category[0] | capitalize }}</a></li>
  {% endfor %}
</ul>

{% for category in site.categories %}
  <h2 id="{{ category[0] | slugify }}">{{ category[0] | capitalize }}</h2>
  <ul>
    {% for post in category[1] %}
      <li><a href="{{ post.url | relative_url }}">{{ post.title }}</a></li>
    {% endfor %}
  </ul>
{% endfor %}
