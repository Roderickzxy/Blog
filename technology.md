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
  <h4 id="t">{{t}}</h4>
  {% if t[0]=="tech" %}
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
