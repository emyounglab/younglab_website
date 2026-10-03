---
layout: default
permalink: /
key: red
wrap: full
---

<section class="hero">
<div class="hero-text">
<h1>Microbes for biosensing and manufacturing</h1>
<p class="lede">We use genomics, synthetic biology, and metabolic engineering to design and build biosensors and cell factories.</p>
<div class="pills">
<a class="btn" href="{{ '/research/' | relative_url }}">Our research</a>
<a class="btn btn-outline" href="{{ '/publications/' | relative_url }}">Publications</a>
<a class="btn btn-outline" href="{{ '/join/' | relative_url }}">Join the lab</a>
</div>
</div>
<img class="hero-img" src="{{ '/assets/img/favicon/favicon.png' | relative_url }}" alt="Line drawings of yeast cells, fungal hyphae and natural-product structures in a red disc">
</section>

<section class="section">
<h2 class="center">Research Areas</h2>
<div class="grid">
<a class="card edge" href="{{ '/research/#metabolic-engineering' | relative_url }}"><span class="title">Metabolic Engineering</span><span>We engineer microbes, using modular parts libraries and combinatorial pathway engineering, to overproduce a target molecule.</span></a>
<a class="card edge" href="{{ '/research/#circuits' | relative_url }}"><span class="title">Genetic Circuits</span><span>We have developed a fungal-bacterial system that can send signals centimeters underground.</span></a>
<a class="card edge" href="{{ '/research/#onboarding' | relative_url }}"><span class="title">Organism Onboarding</span><span>We build the genomic foundation and modular parts that make a new host engineerable.</span></a>
<a class="card edge" href="{{ '/research/#biofoundries' | relative_url }}"><span class="title">Biofoundries</span><span>We integrate genome sequencing into strain development to verify the accuracy of genetic engineering.</span></a>
</div>
</section>

{% comment %}publications.yml is kept newest-first; take the first 3 journal articles or preprints in file order{% endcomment %}
<section class="section section-narrow">
<h2 class="center">Latest articles</h2>
<div class="rows rows-dated">
{% assign n = 0 %}
{% for pub in site.data.publications %}
{% if n < 3 %}{% if pub.type == "journal" or pub.type == "preprint" %}
<a class="row" href="{{ pub.url }}" target="_blank" rel="noreferrer"><span class="row-term">{{ pub.year }}</span><span><span class="row-title">{{ pub.title }}</span><span class="meta">{{ pub.authors | replace: "E.M. Young", "<strong>E.M. Young</strong>" }} · <i>{{ pub.venue }}</i></span></span></a>
{% assign n = n | plus: 1 %}
{% endif %}{% endif %}
{% endfor %}
</div>
<a class="section-more" href="{{ '/publications/' | relative_url }}">All publications →</a>
</section>

<section class="panel panel-bar">
<h2>Get our parts and tools</h2>
{% comment %}links come from _data/resources.yml: every link with a `home` label{% endcomment %}
<div class="pills">
{% for g in site.data.resources.groups %}{% for l in g.links %}{% if l.home %}
<a class="btn btn-outline btn-sm" href="{{ l.url }}">{{ l.home }}</a>
{% endif %}{% endfor %}{% endfor %}
</div>
</section>
