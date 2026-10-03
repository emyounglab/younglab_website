---
layout: default
title: News
permalink: /news/
wrap: narrow
---

<section class="section">
<h1>News</h1>
{% assign items = site.data.news | sort: "date" | reverse %}
<div class="rows">
{% for n in items %}
{% include news-item.html item=n %}
{% endfor %}
</div>
</section>
