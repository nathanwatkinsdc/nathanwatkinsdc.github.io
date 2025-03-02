---
layout: blog
title: Blog
permalink: /blog/
---
<h1 class="text-center">✍🏻 My Blog </h1>

<!-- horizontal line -->
<hr />

{% for post in site.posts %}
- [{{ post.title }}]({{ post.url }}) - {{ post.date | date: "%B %d, %Y" }}
{% endfor %}
