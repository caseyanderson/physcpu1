---
title: recipes
permalink: /recipes/
layout: page
---

<div class="posts">
{% assign sorted-posts = site.posts | where: "tags","recipes" %}
{% for post in sorted-posts %}
  <h3><a href="{{ post.url }}">{{ post.title }}</a></h3>
{% endfor %}
</div>
