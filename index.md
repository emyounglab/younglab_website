---
layout: page
permalink: /
---

<div class="lead">
  We use genomics, synthetic biology, and metabolic engineering<br>
  to design and build biosensors and cell factories.
  <div class="lead-chips">
<a class="lead-chip" href="{{ '/research/#onboarding' | relative_url }}">Organism Onboarding</a>
<a class="lead-chip" href="{{ '/research/#metabolic-engineering' | relative_url }}">Metabolic Engineering</a>
<a class="lead-chip" href="{{ '/research/#circuits' | relative_url }}">Genetic Circuits</a>
<a class="lead-chip" href="{{ '/research/#biofoundries' | relative_url }}">Biofoundries</a>
  </div>
</div>

<hr class="palette-rule"/>

## Latest Articles

{% comment %}publications.yml is kept newest-first; take the first 3 journal articles or preprints in file order{% endcomment %}
{% assign n = 0 %}
{% for pub in site.data.publications %}
{% if n < 3 %}{% if pub.type == "journal" or pub.type == "preprint" %}
{% include pub-item.html pub=pub %}
{% assign n = n | plus: 1 %}
{% endif %}{% endif %}
{% endfor %}

<p><a href="{{ '/publications/' | relative_url }}">All publications →</a></p>

<hr class="palette-rule"/>

<div class="home-parts">
<span class="rmap-axis">Get Our Parts and Tools</span>
<div class="rmap-row">
<a class="rmap-link" href="https://www.addgene.org/kits/young-opencidar/">OpenCidar kit</a>
<a class="rmap-link" href="https://www.addgene.org/browse/article/28252864/">Xd MoClo kit</a>
<a class="rmap-link" href="https://www.addgene.org/browse/article/28275214/">Dh MoClo kit</a>
<a class="rmap-link" href="https://github.com/emyounglab/prymetime">PRYMETIME</a>
<a class="rmap-link" href="https://www.addgene.org/Eric_Young/">All lab plasmids on Addgene →</a>
</div>
</div>