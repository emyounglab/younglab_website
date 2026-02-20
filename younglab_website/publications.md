---
layout: page
title: Publications
permalink: /publications/
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
  {% assign years = "" | split: "" %}
  {% for p in journals %}
    {% unless years contains p.year %}
      {% assign years = years | push: p.year %}
    {% endunless %}
  {% endfor %}

  {% for y in years %}
  ### {{ y }}
    {% for pub in journals %}
      {% if pub.year == y %}
        {% include pub-item.html pub=pub %}
      {% endif %}
    {% endfor %}
  {% endfor %}
{% else %}
  <p class="muted">No journal articles yet. Add items with <code>type: journal</code> in <code>_data/publications.yml</code>.</p>
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
  {% assign years2 = "" | split: "" %}
  {% for p in preprints %}
    {% unless years2 contains p.year %}
      {% assign years2 = years2 | push: p.year %}
    {% endunless %}
  {% endfor %}

  {% for y in years2 %}
  ### {{ y }}
    {% for pub in preprints %}
      {% if pub.year == y %}
        {% include pub-item.html pub=pub %}
      {% endif %}
    {% endfor %}
  {% endfor %}
{% else %}
  <p class="muted">No preprints yet. Add items with <code>type: preprint</code> in <code>_data/publications.yml</code>.</p>
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
{% for pub in other %}
  {% include pub-item.html pub=pub %}
{% endfor %}
{% endif %}