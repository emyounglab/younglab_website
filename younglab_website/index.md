---

layout: page

title: "Young Lab"

subtitle: "Research in X, Y, and Z"

permalink: /

---



<div class="hero">

	<div>

		<p class="lead">

		The <strong>Young Lab</strong> uses genomics, synthetic biology, and metabolic engineering to engineer organisms for a sustainable future.
		
		We are designing the next generation of biosensors and cell factories for a sustainable future.
		
		We are developing biofoundry-based workflows to enable engineering across the tree of life.

		</p>



		<div class="cta-row">

			<a class="button" href="{{ '/research/' | relative\_url }}">Explore research</a>

			<a class="button button-secondary" href="{{ '/join/' | relative\_url }}">Join the lab</a>

		</div>



		<div class="quick-facts">

			<div><strong>Department:</strong> Chemical Engineering</div>

			<div><strong>Institution:</strong> WPI</div>

			<div><strong>Location:</strong> Worcester, MA</div>

		</div>

	</div>



	<div class="hero-card">

		<h2 class="h3">Latest news</h2>

		{% assign items = site.data.news | sort: "date" | reverse | slice: 0, 3 %}

		{% if items.size > 0 %}

			<ul class="clean-list">

				{% for n in items %}

					<li>

						<span class="muted">{{ n.date | date: "%b %-d, %Y" }}</span><br/>

						<strong>{{ n.title }}</strong><br/>

						{{ n.text }}

					</li>

				{% endfor %}

			</ul>

			<p><a href="{{ '/news/' | relative\_url }}">All news →</a></p>

		{% else %}

			<p class="muted">No news yet.</p>

		{% endif %}

	</div>

</div>



<hr/>



## Selected publications

{% assign pubs = site.data.publications | sort: "year" | reverse | slice: 0, 3 %}
{% for pub in pubs %}
  {% include pub-item.html pub=pub %}
{% endfor %}

<p><a href="{{ '/publications/' | relative_url }}">All publications →</a></p>

<hr/>

## Upcoming conferences

{% assign today = site.time | date: '%s' %}
{% assign upcoming = "" | split: "" %}
{% for c in site.data.conferences %}
  {% if c.date %}
    {% assign cts = c.date | date: '%s' %}
    {% if cts >= today %}
      {% assign upcoming = upcoming | push: c %}
    {% endif %}
  {% endif %}
{% endfor %}
{% assign upcoming = upcoming | sort: "date" | slice: 0, 3 %}

{% if upcoming.size > 0 %}
  <ul class="clean-list">
  {% for c in upcoming %}
    <li>
      <strong>{{ c.title }}</strong><br/>
      <span class="muted">
        {{ c.venue }}{% if c.type %} · {{ c.type }}{% endif %}{% if c.location %} · {{ c.location }}{% endif %} · {{ c.date | date: "%b %-d, %Y" }}
      </span>
    </li>
  {% endfor %}
  </ul>
  <p><a href="{{ '/conferences/' | relative_url }}">All conferences →</a></p>
{% else %}
  <p class="muted">No upcoming conference items yet.</p>
{% endif %}