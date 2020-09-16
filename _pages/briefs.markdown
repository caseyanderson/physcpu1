---
title: briefs
permalink: /briefs.html
layout: page
---

<div class="posts">
{% assign sorted-posts = site.posts | where: "tags","brief" %}
{% for post in sorted-posts %}
{% assign date_format = post.week | append: "." | append: post.number %}

<h3>{{ date_format }} <a href="{{ post.url }}">{{ post.title }}</a></h3>

{% endfor %}
</div>
