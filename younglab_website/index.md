---

layout: page

title: "Young Lab"

subtitle: "Research in X, Y, and Z"

permalink: /

---



<div class="hero">

&nbsp; <div>

&nbsp;   <p class="lead">

&nbsp;     The <strong>Young Lab</strong> develops methods and tools for <strong>X</strong>, <strong>Y</strong>, and <strong>Z</strong>.

&nbsp;     We combine experimental and computational approaches to enable scalable, reproducible research.

&nbsp;   </p>



&nbsp;   <div class="cta-row">

&nbsp;     <a class="button" href="{{ '/research/' | relative\_url }}">Explore research</a>

&nbsp;     <a class="button button-secondary" href="{{ '/join/' | relative\_url }}">Join the lab</a>

&nbsp;   </div>



&nbsp;   <div class="quick-facts">

&nbsp;     <div><strong>Department:</strong> Chemical Engineering</div>

&nbsp;     <div><strong>Institution:</strong> Your University</div>

&nbsp;     <div><strong>Location:</strong> City, State</div>

&nbsp;   </div>

&nbsp; </div>



&nbsp; <div class="hero-card">

&nbsp;   <h2 class="h3">Latest news</h2>

&nbsp;   {% assign items = site.data.news | sort: "date" | reverse | slice: 0, 3 %}

&nbsp;   {% if items.size > 0 %}

&nbsp;     <ul class="clean-list">

&nbsp;       {% for n in items %}

&nbsp;         <li>

&nbsp;           <span class="muted">{{ n.date | date: "%b %-d, %Y" }}</span><br/>

&nbsp;           <strong>{{ n.title }}</strong><br/>

&nbsp;           {{ n.text }}

&nbsp;         </li>

&nbsp;       {% endfor %}

&nbsp;     </ul>

&nbsp;     <p><a href="{{ '/news/' | relative\_url }}">All news →</a></p>

&nbsp;   {% else %}

&nbsp;     <p class="muted">No news yet.</p>

&nbsp;   {% endif %}

&nbsp; </div>

</div>



<hr/>



\## Selected publications



{% assign pubs = site.data.publications | sort: "year" | reverse | slice: 0, 3 %}

{% for pub in pubs %}

&nbsp; {% include pub-item.html pub=pub %}

{% endfor %}



<p><a href="{{ '/publications/' | relative\_url }}">All publications →</a></p>



<hr/>



\## Upcoming conferences



{% assign today = site.time | date: '%s' %}

{% assign upcoming = "" | split: "" %}

{% for c in site.data.conferences %}

&nbsp; {% if c.date %}

&nbsp;   {% assign cts = c.date | date: '%s' %}

&nbsp;   {% if cts >= today %}

&nbsp;     {% assign upcoming = upcoming | push: c %}

&nbsp;   {% endif %}

&nbsp; {% endif %}

{% endfor %}

{% assign upcoming = upcoming | sort: "date" | slice: 0, 3 %}



{% if upcoming.size > 0 %}

&nbsp; <ul class="clean-list">

&nbsp; {% for c in upcoming %}

&nbsp;   <li>

&nbsp;     <strong>{{ c.title }}</strong><br/>

&nbsp;     <span class="muted">

&nbsp;       {{ c.venue }}{% if c.type %} · {{ c.type }}{% endif %}{% if c.location %} · {{ c.location }}{% endif %} · {{ c.date | date: "%b %-d, %Y" }}

&nbsp;     </span>

&nbsp;   </li>

&nbsp; {% endfor %}

&nbsp; </ul>

&nbsp; <p><a href="{{ '/conferences/' | relative\_url }}">All conferences →</a></p>

{% else %}

&nbsp; <p class="muted">No upcoming conference items yet.</p>

{% endif %}



