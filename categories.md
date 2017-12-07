---
title: Categories
layout: page
permalink: /categories/
---
<div id='cat_cloud'>
{% for cat in site.categories %}
<a href="#{{ cat[0] }}" title="{{ cat[0] }}" rel="{{ cat[1].size }}">{{ cat[0] }} ({{ cat[1].size }})</a>
{% endfor %}
</div>

<ul class="fa-ul">
{% for cat in site.categories %}
  <li class="listing-seperator" id="{{ cat[0] }}"><i class="fa-li fa fa-square"></i>{{ cat[0] }}</li>
  <ul class="fa-ul">
{% for post in cat[1] %}
  <li class="listing-item">
  <i class="fa-li fa fa-check-square"></i>
  <a href="{{ site.url }}{{ post.url }}" title="{{ post.title }}"><time datetime="{{ post.date | date:"%Y-%m-%d" }}">{{ post.date | date:"%Y-%m-%d" }}</time> {{ post.title }}</a>
  </li>
{% endfor %}
</ul>
{% endfor %}
</ul>