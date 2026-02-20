---
layout: page
title: News
permalink: /news/
---

{% assign items = site.data.news | sort: "date" | reverse %}
<ul class="clean-list">
{% for n in items %}
  {% include news-item.html item=n %}
{% endfor %}
</ul>
