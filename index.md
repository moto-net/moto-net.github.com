---
layout: page
title: Hello World!
tagline: Welcome to Internet Club.
---
{% include JB/setup %}

##Project一覧
- [インターネット部Webサイト2011](http://moto-net.github.com/internet2011) 
- [インターネット部Webサイト2012](http://moto-net.github.com/internet2012)
- [インターネット部Webサイト2013 (準備中)](http://moto-net.github.com/internet2013)


## 最近の投稿
<ul>
  {% for post in site.posts %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>
