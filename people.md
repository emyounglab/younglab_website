---
layout: default
title: People
permalink: /people/
key: green
wrap: wide
toc:
  - { title: Principal Investigator, id: principal-investigator }
  - { title: Current members, id: members }
  - { title: Alumni, id: alumni }
description: "Meet the Young Lab team at WPI — PI, graduate students, postdocs, and alumni working in synthetic biology and metabolic engineering."
---

<div class="with-toc">

{% include toc.html %}

<div class="toc-main">

<div class="section">
<h1>People</h1>
{% for p in site.data.people.pi %}
<section class="panel edge media" id="principal-investigator">
{% if p.photo %}<img class="portrait" src="{{ p.photo | relative_url }}" alt="{{ p.name | escape }}">{% endif %}
<div class="media-body">
<span class="label label-key">Principal Investigator</span>
<h2 class="title">{{ p.name }}</h2>
<p>{{ p.bio }}</p>
<p class="meta">{% if p.email %}<a href="mailto:{{ p.email }}">{{ p.email }}</a>{% endif %}{% for l in p.links %} · <a href="{{ l.url }}" target="_blank" rel="noreferrer">{{ l.label }}</a>{% endfor %}</p>
</div>
</section>
{% endfor %}
</div>

{% assign members = site.data.people.postdocs | concat: site.data.people.students %}
{% if site.data.people.staff %}{% assign members = members | concat: site.data.people.staff %}{% endif %}
<section class="section" id="members">
<h2>Current members</h2>
<div class="rows rows-split">
{% for p in members %}
<div class="row"><span class="row-term">{{ p.name }}<span class="row-role">{{ p.role }}</span></span><span class="row-body">{{ p.interests }}</span></div>
{% endfor %}
</div>
</section>

{% if site.data.people.alumni.size > 0 %}
<section class="panel edge" id="alumni">
<h2>Alumni</h2>
<div class="grid alumni">
{% for p in site.data.people.alumni %}
<span><b>{{ p.name }}</b><br><span class="muted">{{ p.role }}{% if p.current %} → {{ p.current }}{% endif %}</span></span>
{% endfor %}
</div>
</section>
{% endif %}

</div>
</div>
