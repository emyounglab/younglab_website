---
layout: page
title: Publications
permalink: /publications/
description: "Peer-reviewed publications, preprints, reviews, book chapters, and patents from the Young Lab at Worcester Polytechnic Institute."
---

{% assign all_pubs = site.data.publications %}

{% assign pubs = "" | split: "" %}
{% assign prior = "" | split: "" %}
{% for p in all_pubs %}
{% if p.context contains "training" %}{% assign prior = prior | push: p %}
{% else %}{% assign pubs = pubs | push: p %}{% endif %}
{% endfor %}
{% assign total = pubs.size %}
{% assign grand = pubs.size | plus: prior.size %}

{% assign years = "" | split: "" %}
{% for p in pubs %}
{% unless years contains p.year %}{% assign years = years | push: p.year %}{% endunless %}
{% endfor %}
{% assign years = years | sort | reverse %}

<nav class="pub-nav">
{% for y in years %}<a href="#year-{{ y }}">{{ y }}</a>{% endfor %}
<a href="#prior-work">Prior work</a>
</nav>

<div class="pub-section">
{% for y in years %}
{% assign count_before = 0 %}
{% for p in pubs %}
{% if p.year > y %}{% assign count_before = count_before | plus: 1 %}{% endif %}
{% endfor %}
<h3 id="year-{{ y }}" class="year-stamp">{{ y }}</h3>
{% assign year_pubs = pubs | where: "year", y %}
{% for pub in year_pubs %}
{% assign pub_num = grand | minus: count_before | minus: forloop.index0 %}
{% include pub-item.html pub=pub num=pub_num %}
{% endfor %}
{% endfor %}
</div>

{% if prior.size > 0 %}
<div class="pub-section">
<h3 id="prior-work" class="year-stamp">Prior work</h3>
<p class="muted">Published before the Young Lab was established.</p>
{% for pub in prior %}
{% assign pub_num = prior.size | minus: forloop.index0 %}
{% include pub-item.html pub=pub num=pub_num %}
{% endfor %}
</div>
{% endif %}
