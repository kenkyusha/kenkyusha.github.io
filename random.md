---
layout: page
# permalink: /random/
permalink: tag/random
title: Random #Portfolio
# subtitle: Things I've worked on.
---

<!-- blalbvla -->

{% for post in site.tags.random %}
<!-- <h2>{{ post.title }}</h2> -->
<li><a href="{{ site.url }}{{ post.url }}" title="{{ post.title }}" >{{ post.date | date: '%d/%m/%Y' }} ---- {{ post.title }}</a></li>
<!-- <a href="{{ post.url | prepend: site.baseurl }}"> -->
<!-- <time>{{ post.date }}</time> -->
{% endfor %}

