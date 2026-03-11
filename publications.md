---
layout: page
title: Publications
permalink: /publications/
description: "Peer-reviewed publications, preprints, and book chapters from the Young Lab at Worcester Polytechnic Institute."
---

{% assign pubs = site.data.publications | sort: "year" | reverse %}

<nav class="pub-nav">
  <a href="#preprints">Preprints</a>
  <a href="#peer-reviewed-journal-articles">Papers</a>
  <a href="#reviews">Reviews</a>
  <a href="#book-chapters">Book Chapters</a>
  <a href="#patents">Patents</a>
</nav>

{% assign journals = "" | split: "" %}
{% assign preprints = "" | split: "" %}
{% assign reviews = "" | split: "" %}
{% assign chapters = "" | split: "" %}
{% assign patents = "" | split: "" %}
{% for p in pubs %}
{% if p.type == "journal" %}{% assign journals = journals | push: p %}
{% elsif p.type == "preprint" %}{% assign preprints = preprints | push: p %}
{% elsif p.type == "review" %}{% assign reviews = reviews | push: p %}
{% elsif p.type == "book-chapter" %}{% assign chapters = chapters | push: p %}
{% elsif p.type == "patent" %}{% assign patents = patents | push: p %}
{% endif %}
{% endfor %}

{% assign total_numbered = journals.size | plus: preprints.size | plus: reviews.size | plus: chapters.size %}
{% assign offset_pre = journals.size %}
{% assign offset_rev = journals.size | plus: preprints.size %}
{% assign offset_ch = journals.size | plus: preprints.size | plus: reviews.size %}

<div class="pub-section">
<h2 id="peer-reviewed-journal-articles">Peer-Reviewed Journal Articles</h2>
{% if journals.size > 0 %}
{% assign years = "" | split: "" %}
{% for p in journals %}
{% unless years contains p.year %}{% assign years = years | push: p.year %}{% endunless %}
{% endfor %}
{% for y in years %}
{% assign count_before = 0 %}
{% for p in journals %}
{% if p.year > y %}{% assign count_before = count_before | plus: 1 %}{% endif %}
{% endfor %}
<h3 class="year-stamp">{{ y }}</h3>
{% assign year_pubs = journals | where: "year", y %}
{% for pub in year_pubs %}
{% assign pub_num = total_numbered | minus: count_before | minus: forloop.index0 %}
{% include pub-item.html pub=pub num=pub_num %}
{% endfor %}
{% endfor %}
{% else %}
<p class="muted">No journal articles yet.</p>
{% endif %}
</div>

<div class="pub-section">
<div class="pub-section-title">
<h2 id="preprints">Preprints</h2>
<a href="#" class="back-to-top">↑ top</a>
</div>
{% if preprints.size > 0 %}
{% assign years2 = "" | split: "" %}
{% for p in preprints %}
{% unless years2 contains p.year %}{% assign years2 = years2 | push: p.year %}{% endunless %}
{% endfor %}
{% for y in years2 %}
{% assign count_before2 = 0 %}
{% for p in preprints %}
{% if p.year > y %}{% assign count_before2 = count_before2 | plus: 1 %}{% endif %}
{% endfor %}
<h3 class="year-stamp">{{ y }}</h3>
{% assign year_pubs2 = preprints | where: "year", y %}
{% for pub in year_pubs2 %}
{% assign pub_num = total_numbered | minus: offset_pre | minus: count_before2 | minus: forloop.index0 %}
{% include pub-item.html pub=pub num=pub_num %}
{% endfor %}
{% endfor %}
{% else %}
<p class="muted">No preprints yet.</p>
{% endif %}
</div>

<div class="pub-section">
<div class="pub-section-title">
<h2 id="reviews">Reviews</h2>
<a href="#" class="back-to-top">↑ top</a>
</div>
{% if reviews.size > 0 %}
{% for pub in reviews %}
{% assign pub_num = total_numbered | minus: offset_rev | minus: forloop.index0 %}
{% include pub-item.html pub=pub num=pub_num %}
{% endfor %}
{% else %}
<p class="muted">No reviews yet.</p>
{% endif %}
</div>

<div class="pub-section">
<div class="pub-section-title">
<h2 id="book-chapters">Book Chapters</h2>
<a href="#" class="back-to-top">↑ top</a>
</div>
{% if chapters.size > 0 %}
{% for pub in chapters %}
{% assign pub_num = total_numbered | minus: offset_ch | minus: forloop.index0 %}
{% include pub-item.html pub=pub num=pub_num %}
{% endfor %}
{% else %}
<p class="muted">No book chapters yet.</p>
{% endif %}
</div>

<div class="pub-section">
<div class="pub-section-title">
<h2 id="patents">Patents</h2>
<a href="#" class="back-to-top">↑ top</a>
</div>
{% if patents.size > 0 %}
{% assign total_patents = patents.size %}
{% for pub in patents %}
{% assign pub_num = total_patents | minus: forloop.index0 %}
{% include pub-item.html pub=pub num=pub_num %}
{% endfor %}
{% else %}
<p class="muted">No patents yet.</p>
{% endif %}
</div>
