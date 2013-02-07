---
layout: page
title: Hello World!
tagline: Welcome to Internet Club.
description: インターネット部Blog パソコンやイラスト、動画制作やプログラミングなどの役立つ知識が集まるブログ。
---
{% include JB/setup %}


## 最近の投稿
<ul>
  {% for post in site.posts %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>
