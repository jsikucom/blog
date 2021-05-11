---
layout: page
title: Gallery
date: '2017-10-17 06:04:00 +0900'
tags: gallery
permalink: /gallery/
author: siku
---
{% for post in site.posts %}
{% if post.layout contains "gallery" %}
<div class="project">
<div class="thumbnail">
<a href="{{ site.baseurl }}{{ post.url }}">
{% if post.img %}
<img class="thumbnail" src="{{ post.img }}"/>
{% else %}
<div class="thumbnail blankbox"></div>
{% endif %}
<span>
<h5>{{ post.title }}</h5>
<br/>
<p>{{ post.author }} {{ post.date | date: '%F' }}</p>
</span>
</a>
</div>
</div>
{% endif %}
{% endfor %}
