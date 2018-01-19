---
bg: "tag.jpg"
layout: page
permalink: /tech
title: "技术拯救世界"
crawlertitle: "technology articles"
summary: "mark down some technical detail"
active: archive
---

{% for tag in site.tags %}
  {% assign t = tag | first %}
  {% assign posts = tag | last %}
  {% assign category = t | truncate: 4, '' %}
  <h4>{{ category }}</h4>
  {% if category=="tech" %}
	  <h2 class="category-key" id="{{ t[1] | downcase }}">{{ t[1] | capitalize }}</h2>
	  
	  <ul class="year">
	    {% for post in posts %}
	      {% if post.tags contains t[1] %}
	        <li>
	          {% if post.lastmod %}
	            <a href="{{ post.url | relative_url}}">{{ post.title }}</a>
	            <span class="date">{{ post.lastmod | date: "%d-%m-%Y"  }}</span>
	          {% else %}
	            <a href="{{ post.url | relative_url}}">{{ post.title }}</a>
	            <span class="date">{{ post.date | date: "%d-%m-%Y"  }}</span>
	          {% endif %}
	        </li>
	      {% endif %}
	    {% endfor %}
	  </ul>
  {% endif %}
{% endfor %}
