---
layout: page
title: Reflections
subtitle: Occasional notes on research, methods, books, and the places I think from.
permalink: /reflections/
---

<ul class="reflection-list">
  {% assign sorted = site.reflections | sort: 'date' | reverse %}
  {% for post in sorted %}
    <li>
      {% if post.category %}<p class="reflection-category">{{ post.category }}</p>{% endif %}
      <h2><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h2>
      <p class="reflection-date">{{ post.date | date: "%B %-d, %Y" }}</p>
      <p class="reflection-excerpt">{{ post.excerpt | strip_html | truncatewords: 32 }}</p>
    </li>
  {% endfor %}
</ul>
