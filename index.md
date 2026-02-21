---
layout: page
permalink: /
---

<p class="lead">The Young Lab uses genomics, synthetic biology, and metabolic engineering to engineer organisms. We are designing the next generation of biosensors and cell factories for a sustainable future. We are developing biofoundry-based workflows to enable engineering across the tree of life.</p>

<hr/>

## Selected publications

{% assign pubs = site.data.publications | sort: "year" | reverse | slice: 0, 3 %}
{% for pub in pubs %}
  {% include pub-item.html pub=pub %}
{% endfor %}

<p><a href="{{ '/publications/' | relative_url }}">All publications →</a></p>

<hr/>