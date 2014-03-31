---
layout: default
title: Documentation
permalink: /docs/home/
categories: home
tags: [one two three, four]
featured: true
---

<ul>
{% for node in site.pages %}
  {% if page.categories != null and node.categories == "docs" %}
    {% if page.url == node.url %}
      <li class="active"><a href="{{ node.url }}">{{ node.title }}</a></li>
    {% else %}
      <li><a href="{{ node.url }}">{{ node.title }}</a></li>
    {% endif %}
  {% endif %}
{% endfor %}
</ul>
