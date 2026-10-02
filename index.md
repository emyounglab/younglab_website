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

<h2 class="home-title">Latest Articles</h2>

{% comment %}publications.yml is kept newest-first; take the first 3 journal articles or preprints in file order{% endcomment %}
<div class="home-cards">
{% assign n = 0 %}
{% for pub in site.data.publications %}
{% if n < 3 %}{% if pub.type == "journal" or pub.type == "preprint" %}
<a class="home-card" href="{{ pub.url }}" target="_blank" rel="noreferrer">
<span class="home-card-meta">{{ pub.year }} &middot; {{ pub.venue }}</span>
<span class="home-card-title">{{ pub.title }}</span>
<span class="home-card-authors">{{ pub.authors | replace: "E.M. Young", "<strong>E.M. Young</strong>" }}</span>
</a>
{% assign n = n | plus: 1 %}
{% endif %}{% endif %}
{% endfor %}
</div>

<p class="home-more"><a href="{{ '/publications/' | relative_url }}">All publications →</a></p>

<hr class="palette-rule"/>

<div class="home-parts">
<h2 class="home-parts-title">Get Our Parts and Tools</h2>
<div class="rmap-row">
<a class="rmap-link" href="https://www.addgene.org/kits/young-opencidar/">OpenCidar kit</a>
<a class="rmap-link" href="https://www.addgene.org/browse/article/28252864/">Xd MoClo kit</a>
<a class="rmap-link" href="https://www.addgene.org/browse/article/28275214/">Dh MoClo kit</a>
<a class="rmap-link" href="https://github.com/emyounglab/prymetime">PRYMETIME</a>
<a class="rmap-link" href="https://www.addgene.org/Eric_Young/">All lab plasmids on Addgene →</a>
</div>
</div>