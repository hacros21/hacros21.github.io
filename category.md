---
layout: default
title: categories
permalink: /categories/
---



{% capture site_cate %}{% for category in site.categories %}{{ category | first }}{% unless forloop.last %},{% endunless %}{% endfor %}{% endcapture %}
<!-- site_tags: {{ site_tags }} -->

{% assign cate_words = site_cate | split:',' | sort %}
<!-- tag_words: {{ tag_words }} -->

<div id="tags">
  <!--<h1>Tags</h1>-->
  <ul class="tag-box inline">
  {% for item in (0..site.categories.size) %}{% unless forloop.last %}
    {% capture this_word %}{{ cate_words[item] | strip_newlines }}{% endcapture %}

    <li><a href="#{{ this_word | cgi_escape }}">{{ this_word }}
    <span>{{ site.categories.[this_word].size }}</span></a></li>
  {% endunless %}{% endfor %}
  </ul>
  <hr>

  {% for item in (0..site.categories.size) %}{% unless forloop.last %}
    {% capture this_word %}{{ cate_words[item] | strip_newlines }}{% endcapture %}
  <h2 id="{{ this_word | cgi_escape }}">{{ this_word }}</h2>
  <ul class="posts">
    {% for post in site.categories[this_word] %}{% if post.title != null %}
    <li><a href="{{ post.url }}">{{ post.title }}</a> <span class="date">{{ post.date | date: "%y%m%d" }}</span> </li>
    {% endif %}{% endfor %}
  </ul>
  {% endunless %}{% endfor %}

</div>
