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
			<a class="button" href="{{ '/research/' | relative_url }}">Explore research</a>
			<a class="button button-secondary" href="{{ '/join/' | relative_url }}">Join the lab</a>
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

			<p><a href="{{ '/news/' | relative_url }}">All news →</a></p>

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