---
title: briefs
permalink: /briefs/
layout: page
published: false
---

{% for post in site.tags['brief'] %}
  {% capture first_tag %}{{ post.tags | first }}{% endcapture %}
  <h3>{{ "week " | append: post.week | append: ", " }}{{ first_tag }}{{ " " | append: post.number }}: <a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a></h3>
{% endfor %}
