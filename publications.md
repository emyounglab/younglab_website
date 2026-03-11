---
layout: page
title: Publications
permalink: /publications/
description: "Peer-reviewed publications, preprints, and book chapters from the Young Lab at Worcester Polytechnic Institute."
---

{% assign pubs = site.data.publications | sort: "year" | reverse %}

## Journal articles

{% assign journals = "" | split: "" %}
{% for p in pubs %}
{% if p.type == "journal" %}
{% assign journals = journals | push: p %}
{% endif %}
{% endfor %}

{% if journals.size > 0 %}
{% assign total_j = journals.size %}
{% assign years = "" | split: "" %}
{% for p in journals %}
{% unless years contains p.year %}
{% assign years = years | push: p.year %}
{% endunless %}
{% endfor %}
{% for y in years %}
{% assign count_before = 0 %}
{% for p in journals %}
{% if p.year > y %}{% assign count_before = count_before | plus: 1 %}{% endif %}
{% endfor %}
<h3 class="year-stamp">{{ y }}</h3>
{% assign year_pubs = journals | where: "year", y %}
{% for pub in year_pubs %}
{% assign pub_num = total_j | minus: count_before | minus: forloop.index0 %}
{% include pub-item.html pub=pub num=pub_num %}
{% endfor %}
{% endfor %}
{% else %}
<p class="muted">No journal articles yet.</p>
{% endif %}

<hr/>

## Preprints

{% assign preprints = "" | split: "" %}
{% for p in pubs %}
{% if p.type == "preprint" %}
{% assign preprints = preprints | push: p %}
{% endif %}
{% endfor %}

{% if preprints.size > 0 %}
{% assign total_pre = preprints.size %}
{% assign years2 = "" | split: "" %}
{% for p in preprints %}
{% unless years2 contains p.year %}
{% assign years2 = years2 | push: p.year %}
{% endunless %}
{% endfor %}
{% for y in years2 %}
{% assign count_before2 = 0 %}
{% for p in preprints %}
{% if p.year > y %}{% assign count_before2 = count_before2 | plus: 1 %}{% endif %}
{% endfor %}
<h3 class="year-stamp">{{ y }}</h3>
{% assign year_pubs2 = preprints | where: "year", y %}
{% for pub in year_pubs2 %}
{% assign pub_num = total_pre | minus: count_before2 | minus: forloop.index0 %}
{% include pub-item.html pub=pub num=pub_num %}
{% endfor %}
{% endfor %}
{% else %}
<p class="muted">No preprints yet.</p>
{% endif %}

{% assign other = "" | split: "" %}
{% for p in pubs %}
{% if p.type != "journal" and p.type != "preprint" %}
{% assign other = other | push: p %}
{% endif %}
{% endfor %}

{% if other.size > 0 %}
<hr/>

## Other

{% assign total_other = other.size %}
{% for pub in other %}
{% assign pub_num = total_other | minus: forloop.index0 %}
{% include pub-item.html pub=pub num=pub_num %}
{% endfor %}
{% endif %}
