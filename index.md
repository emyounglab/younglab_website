---
layout: page
permalink: /
---

<div class="palette-stripe">
  <span class="ps-red"></span>
  <span class="ps-orange"></span>
  <span class="ps-green"></span>
  <span class="ps-navy"></span>
  <span class="ps-blue"></span>
</div>

<p class="lead">The Young Lab uses genomics, synthetic biology, and metabolic engineering to engineer organisms. We are designing the next generation of biosensors and cell factories for a sustainable future. We are developing biofoundry-based workflows to enable engineering across the tree of life.</p>

<div class="focus-badges">
  <a href="{{ '/research/#cell-factories' | relative_url }}" class="focus-badge badge-orange">Cell Factories</a>
  <a href="{{ '/research/#biosensors' | relative_url }}" class="focus-badge badge-blue">Biosensors</a>
  <a href="{{ '/research/#nonconventional-yeasts' | relative_url }}" class="focus-badge badge-green">Nonconventional Yeasts</a>
  <a href="{{ '/research/#microbial-communities' | relative_url }}" class="focus-badge badge-navy">Microbial Communities</a>
</div>

<hr class="palette-rule"/>

## Selected publications

{% assign pubs = site.data.publications | sort: "year" | reverse | slice: 0, 3 %}
{% for pub in pubs %}
  {% include pub-item.html pub=pub %}
{% endfor %}

<p><a href="{{ '/publications/' | relative_url }}">All publications →</a></p>

<hr class="palette-rule"/>