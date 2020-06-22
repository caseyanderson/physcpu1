---
title: recipes
permalink: /recipes/
layout: page
---

{% assign sorted-posts = site.posts | where: "tags","recipes" %}
{% for post in sorted-posts %}
  <h3><a href="{{ post.url }}">{{ post.title }}</a></h3>
{% endfor %}

