---
layout: page
title: News
permalink: /news/
---

{% assign items = site.data.news | sort: "date" | reverse %}
<ul class="clean-list">
{% for n in items %}
  <li class="news-item">
    <span class="muted">{{ n.date | date: "%B %-d, %Y" }}</span><br/>
    <strong>{{ n.title }}</strong><br/>
    {{ n.text }}
  </li>
{% endfor %}
</ul>