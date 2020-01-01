---
bg: "climbing.jpg"
layout: page
permalink: /tech
title: "技术拯救世界"
crawlertitle: "技术"
summary: "mark down some technical detail"
active: archive
---

{% for tag in site.tags %}
  {% assign t = tag | first %}
  {% assign posts = tag | last %}
  {% assign category = t | truncate: 4, '' %}
  {% if category=="tech" %}
  {% assign cate-tag = t | replace:'tech-','' %}
  <h2 class="category-key" id="{{ cate-tag | downcase }}">{{ cate-tag | capitalize }}</h2>
  
  <ul class="year">
    {% for post in posts %}
      {% if post.tags contains t %}
        <li>
          {% if post.lastmod %}
            <a href="{{ post.url | relative_url}}">{{ post.title }}</a>
            <span class="date">{{ post.lastmod | date: "%Y-%m-%d"  }}</span>
          {% else %}
            <a href="{{ post.url | relative_url}}">{{ post.title }}</a>
            <span class="date">{{ post.date | date: "%Y-%m-%d"  }}</span>
          {% endif %}
        </li>
      {% endif %}
    {% endfor %}
  </ul>
  {% endif %}
{% endfor %}
