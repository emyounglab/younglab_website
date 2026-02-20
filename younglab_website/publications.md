---

layout: page

title: Publications

permalink: /publications/

---



{% assign pubs = site.data.publications | sort: "year" | reverse %}



\## Journal articles

{% assign journals = "" | split: "" %}

{% for p in pubs %}

&nbsp; {% if p.type == "journal" %}

&nbsp;   {% assign journals = journals | push: p %}

&nbsp; {% endif %}

{% endfor %}



{% if journals.size > 0 %}

&nbsp; {% assign years = "" | split: "" %}

&nbsp; {% for p in journals %}

&nbsp;   {% unless years contains p.year %}

&nbsp;     {% assign years = years | push: p.year %}

&nbsp;   {% endunless %}

&nbsp; {% endfor %}



&nbsp; {% for y in years %}

&nbsp; ### {{ y }}

&nbsp;   {% for pub in journals %}

&nbsp;     {% if pub.year == y %}

&nbsp;       {% include pub-item.html pub=pub %}

&nbsp;     {% endif %}

&nbsp;   {% endfor %}

&nbsp; {% endfor %}

{% else %}

&nbsp; <p class="muted">No journal articles yet. Add items with <code>type: journal</code> in <code>\_data/publications.yml</code>.</p>

{% endif %}



<hr/>



\## Preprints

{% assign preprints = "" | split: "" %}

{% for p in pubs %}

&nbsp; {% if p.type == "preprint" %}

&nbsp;   {% assign preprints = preprints | push: p %}

&nbsp; {% endif %}

{% endfor %}



{% if preprints.size > 0 %}

&nbsp; {% assign years2 = "" | split: "" %}

&nbsp; {% for p in preprints %}

&nbsp;   {% unless years2 contains p.year %}

&nbsp;     {% assign years2 = years2 | push: p.year %}

&nbsp;   {% endunless %}

&nbsp; {% endfor %}



&nbsp; {% for y in years2 %}

&nbsp; ### {{ y }}

&nbsp;   {% for pub in preprints %}

&nbsp;     {% if pub.year == y %}

&nbsp;       {% include pub-item.html pub=pub %}

&nbsp;     {% endif %}

&nbsp;   {% endfor %}

&nbsp; {% endfor %}

{% else %}

&nbsp; <p class="muted">No preprints yet. Add items with <code>type: preprint</code> in <code>\_data/publications.yml</code>.</p>

{% endif %}



{% assign other = "" | split: "" %}

{% for p in pubs %}

&nbsp; {% if p.type != "journal" and p.type != "preprint" %}

&nbsp;   {% assign other = other | push: p %}

&nbsp; {% endif %}

{% endfor %}



{% if other.size > 0 %}

<hr/>



\## Other

{% for pub in other %}

&nbsp; {% include pub-item.html pub=pub %}

{% endfor %}

{% endif %}



