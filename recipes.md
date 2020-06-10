---
title: recipes
permalink: /recipes/
layout: page
---


{% assign sorted-posts = site.posts | where: "tags","recipes" %}
{% for post in sorted-posts limit: 5 %}
  <li>{{post.title}}</li>
{% endfor %}

<!--
{% for post in site.tags['recipes'] %}

  {% capture first_tag %}{{ post.tags | first }}{% endcapture %}
  <h3>{{ "week " | append: post.week | append: ", " }}{{ first_tag }}{{ " " | append: post.number }}: <a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a></h3>
{% endfor %} -->
