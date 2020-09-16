---
title: labs
permalink: /labs.html
layout: page
---

<div class="posts">
    {% assign sorted-posts = site.posts | where: "categories","labs" %}
    {% for post in sorted-posts %}

        <h3>{{ "Week " | append: post.week}}.{{ post.number }} <a href="{{ post.url }}">{{ post.title }}</a></h3>

{% endfor %}
</div>

