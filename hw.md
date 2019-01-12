---
title: hw
permalink: /hw/
layout: page
---

{% for post in site.tags['hw'] %}
  {% capture first_tag %}{{ post.tags | first }}{% endcapture %}
  <h3>{{ "week " | append: post.week | append: ", " }}{{ first_tag }}{{ " " | append: post.number }}: <a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a></h3>
{% endfor %}
