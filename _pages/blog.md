---
title: "Blog"
layout: page
sitemap: false
permalink: /blog/
---

{% for post in site.posts %}
 {% unless post.draft %}
   * <span class="blog-list">__{{ post.date | date: "%Y-%m-%d" }}__</span> &raquo; [ {{ post.title }} ]({{ post.url }})
 {% endunless %}
{% endfor %}

<br>
