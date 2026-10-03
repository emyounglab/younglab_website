---
layout: default
title: People
permalink: /people/
key: green
wrap: narrow
description: "Meet the Young Lab team at WPI — PI, graduate students, postdocs, and alumni working in synthetic biology and metabolic engineering."
---

{% for p in site.data.people.pi %}
<section class="intro" id="principal-investigator">
{% if p.photo %}<img class="portrait" src="{{ p.photo | relative_url }}" alt="{{ p.name | escape }}">{% endif %}
<h1>{{ p.name }}</h1>
<p class="lede">{{ p.bio }}</p>
<p class="intro-links">{% if p.email %}<a href="mailto:{{ p.email }}">{{ p.email }}</a>{% endif %}{% for l in p.links %} · <a href="{{ l.url }}" target="_blank" rel="noreferrer">{{ l.label }}</a>{% endfor %}</p>
</section>
{% endfor %}

{% assign members = site.data.people.postdocs | concat: site.data.people.students %}
{% if site.data.people.staff %}{% assign members = members | concat: site.data.people.staff %}{% endif %}
<section class="section" id="members">
<h2 class="center">Current members</h2>
<div class="rows rows-split">
{% for p in members %}
<div class="row"><span class="row-term">{{ p.name }}<span class="row-role">{{ p.role }}</span></span><span class="row-body">{{ p.interests }}</span></div>
{% endfor %}
</div>
</section>

{% if site.data.people.alumni.size > 0 %}
<section class="panel edge" id="alumni">
<h2 class="center">Alumni</h2>
<div class="grid alumni">
{% for p in site.data.people.alumni %}
<span><b>{{ p.name }}</b><br><span class="muted">{{ p.role }}{% if p.current %} → {{ p.current }}{% endif %}</span></span>
{% endfor %}
</div>
</section>
{% endif %}
