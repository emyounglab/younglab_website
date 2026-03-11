---
layout: page
title: People
permalink: /people/
description: "Meet the Young Lab team at WPI — PI, graduate students, postdocs, and alumni working in synthetic biology and metabolic engineering."
---

<nav class="pub-nav pub-nav-green">
  <a href="#principal-investigator">PI</a>
  <a href="#postdoctoral-researchers">Postdocs</a>
  <a href="#students">Students</a>
  <a href="#alumni">Alumni</a>
</nav>

<div class="people-page">

<h2 id="principal-investigator">Principal Investigator</h2>
<div class="grid-single">
{% for p in site.data.people.pi %}
{% include person-card.html person=p %}
{% endfor %}
</div>

<div class="pub-section-title">
<h2 id="postdoctoral-researchers">Postdoctoral Researchers</h2>
<a href="#" class="back-to-top back-to-top-green">↑ top</a>
</div>
<div class="grid-single">
{% for p in site.data.people.postdocs %}
{% include person-card.html person=p %}
{% endfor %}
</div>

<div class="pub-section-title">
<h2 id="students">Students</h2>
<a href="#" class="back-to-top back-to-top-green">↑ top</a>
</div>
<div class="grid">
{% for p in site.data.people.students %}
{% include person-card.html person=p %}
{% endfor %}
</div>

{% if site.data.people.alumni and site.data.people.alumni.size > 0 %}
<div class="pub-section-title">
<h2 id="alumni">Alumni</h2>
<a href="#" class="back-to-top back-to-top-green">↑ top</a>
</div>
<ul>
{% for p in site.data.people.alumni %}
<li><strong>{{ p.name }}</strong>{% if p.role %} ({{ p.role }}){% endif %}{% if p.current %} — now at {{ p.current }}{% endif %}</li>
{% endfor %}
</ul>
{% endif %}

</div>
