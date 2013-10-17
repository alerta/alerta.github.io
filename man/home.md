---
layout: docs
title: Man Pages
permalink: /home/
categories: introduction
tags: [manpage]
featured: true
---

<ul>
{% for node in site.pages %}
  {% if page.categories != null and node.categories == "manpage" %}
    {% if page.url == node.url %}
      <li class="active"><a href="{{ node.url }}">{{ node.title }}</a></li>
    {% else %}
      <li><a href="{{ node.url }}">{{ node.title }}</a></li>
    {% endif %}
  {% endif %}
{% endfor %}
</ul>
