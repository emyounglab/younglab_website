---
layout: default
title: Publications
permalink: /publications/
key: navy
wrap: wide
toc:
  - { title: Publications, id: lab-work, years: true }
  - { title: Prior work, id: prior-work }
description: "Peer-reviewed publications, preprints, reviews, book chapters, and patents from the Young Lab at Worcester Polytechnic Institute."
---

{% comment %}Split once: training papers go to Prior work, everything else is lab work.
Numbers count down across both lists, newest first.{% endcomment %}
{% assign pubs = "" | split: "" %}
{% assign prior = "" | split: "" %}
{% for p in site.data.publications %}
{% if p.context contains "training" %}{% assign prior = prior | push: p %}
{% else %}{% assign pubs = pubs | push: p %}{% endif %}
{% endfor %}
{% assign grand = pubs.size | plus: prior.size %}

{% assign years = "" | split: "" %}
{% for p in pubs %}
{% unless years contains p.year %}{% assign years = years | push: p.year %}{% endunless %}
{% endfor %}
{% assign years = years | sort | reverse %}

<div class="with-toc">

{% include toc.html years=years %}

<div class="toc-main toc-main-compact">

<section class="section" id="lab-work">
<h1>Publications</h1>
</section>

{% assign pub_num = grand %}
{% for y in years %}
<section class="section" id="year-{{ y }}">
<h2>{{ y }}</h2>
<div class="pub-list">
{% assign year_pubs = pubs | where: "year", y %}
{% for pub in year_pubs %}
{% include pub-item.html pub=pub num=pub_num %}
{% assign pub_num = pub_num | minus: 1 %}
{% endfor %}
</div>
</section>
{% endfor %}

{% if prior.size > 0 %}
<section class="section" id="prior-work">
<h2>Prior work</h2>
<p class="muted">Published before the Young Lab was established.</p>
<div class="pub-list">
{% for pub in prior %}
{% assign pub_num = prior.size | minus: forloop.index0 %}
{% include pub-item.html pub=pub num=pub_num %}
{% endfor %}
</div>
</section>
{% endif %}

</div>
</div>
