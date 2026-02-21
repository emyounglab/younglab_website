---
layout: page
title: People
permalink: /people/
---

## Principal Investigator
<div class="grid">
{% for p in site.data.people.pi %}
	{% include person-card.html person=p %}
{% endfor %}
</div>

## Students
<div class="grid">
{% for p in site.data.people.students %}
	{% include person-card.html person=p %}
{% endfor %}
</div>

## Staff
<div class="grid">
{% for p in site.data.people.staff %}
	{% include person-card.html person=p %}
{% endfor %}
</div>

{% if site.data.people.alumni and site.data.people.alumni.size > 0 %}
## Alumni
<ul>
{% for p in site.data.people.alumni %}
  <li>
    <strong>{{ p.name }}</strong>{% if p.role %} ({{ p.role }}){% endif %}{% if p.current %} — now at {{ p.current }}{% endif %}
  </li>
{% endfor %}
</ul>
{% endif %}