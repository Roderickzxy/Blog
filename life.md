---
bg: "onbus.jpg"
layout: page
permalink: /life/
title: "一弦一柱思华年"
crawlertitle: "生活"
summary: "路灯下的感叹."
active: archive
---

{% for tag in site.tags %}
  {% assign t = tag | first %}
  {% assign posts = tag | last %}
  {% assign category = t | truncate: 4, '' %}
  {% if category=="life" %}
  {% assign cate-tag = t | replace:'life-','' %}
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
