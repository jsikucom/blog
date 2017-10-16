---
layout: page
title: Gallery
date: '2017-10-17 06:04:00 +0900'
tags: gallery
permalink: /gallery/
author: siku
---
    <div class="row pack">

        {% for post in paginator.posts %}   
            <div class="col-md-4 card">
                 
                <div class="panel panel-default">
                  <div class="panel-body">
                    <h3 class="panel-title pull-left">{{ post.title | truncate: 25 }}</h3><span class="post-meta pull-right"><small>{{ post.date | date: "%F" }}</small></span>
                  </div>
                  {% if post.img %}
                  <img width="100%" src="{{post.img}}" alt="{{post.title}}" href="{{ post.url | prepend: site.baseurl }}">
                  {% endif %}
                </div>
            </div>
        
          {% endfor %}

    </div> 
    
<div class="row">
    <div class="col-md-4">  </div>
    <div class="col-md-4">
        {% if paginator.total_pages > 1 %}
        <ul class="pagination">
          {% if paginator.previous_page %}
            <li><a href="{{ paginator.previous_page_path | prepend: site.baseurl | replace: '//', '/' }}">&laquo; Prev</a></li>
          {% else %}
            <li><span>&laquo; Prev</span></li>
          {% endif %}

          {% for page in (1..paginator.total_pages) %}
            {% if page == paginator.page %}
              <li class="active"><span><em>{{ page }}</em></span></li>
            {% elsif page == 1 %}
            <li><a href="{{ paginator.previous_page_path | prepend: site.baseurl | replace: '//', '/' }}">{{ page }}</a></li>
            {% else %}
            <li><a href="{{ site.paginate_path | prepend: site.baseurl | replace: '//', '/' | replace: ':num', page }}">{{ page }}</a></li>
            {% endif %}
          {% endfor %}

          {% if paginator.next_page %}
            <li><a href="{{ paginator.next_page_path | prepend: site.baseurl | replace: '//', '/' }}">Next &raquo;</a></li>
          {% else %}
            <li><span >Next &raquo;</span></li>
          {% endif %}
          </ul>
        {% endif %}

    </div>
    <div class="col-md-4">  </div>
</div>

