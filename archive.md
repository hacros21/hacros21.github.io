---
layout: page
title: archive
permalink: /archive/
---

<article>

{% for post in site.posts %}
{% capture month %}{{ post.date | date: '%m%Y' }}{% endcapture %}
{% capture nmonth %}{{ post.next.date | date: '%m%Y' }}{% endcapture %}
{% if month != nmonth %}
{% if forloop.index != 1 %}</ul>{% endif %}
<h2>{{ post.date | date: '%Y년 %m월' }}</h2><ul>
{% endif %}
<li> <a href="{{ post.url }}">{{ post.title }}</a>  <span class="date">{{ post.date | date: "%y%m%d" }}</span></li>

{% endfor %}

</article>
