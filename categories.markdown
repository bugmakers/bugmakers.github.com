---
layout: page
title: Articles
header-img: "img/post-bg-01.jpg"
---

<div id="post-content">
<ul class="tag-box inline">
{% assign tags_list = site.categories %}  
  {% if tags_list.first[0] == null %}
    {% for tag in tags_list %} 
      <li><a href="{{ site.url }}/categories/#{{ tag }}">{{ tag | capitalize }} <sup>{{ site.tags[tag].size }}</sup></a></li>
    {% endfor %}
  {% else %}
    {% for tag in tags_list %} 
      <li><a href="{{ site.url }}/categories/#{{ tag[0] }}">{{ tag[0] | capitalize }} <sup>{{ tag[1].size }}</sup></a></li>
    {% endfor %}
  {% endif %}
{% assign tags_list = nil %}
</ul>

{% for tag in site.categories %} 
  <h2 id="{{ tag[0] }}">{{ tag[0] | capitalize }} <sup>({{ tag[1].size }})</sup></h2>
  <ul class="post-list">
    {% assign pages_list = tag[1] %}  
    {% for post in pages_list %}
      {% if post.title != null %}
      {% if group == null or group == post.group %}
      <li><a href="{{ site.url }}{{ post.url }}">{{ post.title }} <span class="entry-date"><time datetime="{{ post.date | date_to_xmlschema }}" itemprop="datePublished">{{ post.date | date: "%B %d, %Y" }}</time></a></li>
      {% endif %}
      {% endif %}
    {% endfor %}
    {% assign pages_list = nil %}
    {% assign group = nil %}
  </ul>
{% endfor %}
</div>
