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
<div class="grid">
{% for p in site.data.people.alumni %}
	{% include person-card.html person=p %}
{% endfor %}
</div>
{% endif %}