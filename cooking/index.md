---
title: Cooking
---

## Cooking Recipes

{% for category in site.categories %}
  {% if category[0] == 'recipe' %}
  <ul>
    {% for post in category[1] %}
      <li><a href="{{ post.url }}">{{ post.title }}</a><br /><em>{{ post.tags | join: ", " }}</em></li>
    {% endfor %}
  </ul>
  {% endif %}
{% endfor %}