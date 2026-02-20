---
layout: page
title: "Bioindustrial Hub"
subtitle: "Advanced biotech infrastructure for discovery, scale-up, and translation"
permalink: /
---

<div class="hero">
  <div>
    <p class="lead">
      We are a bioindustrial hub that accelerates the pathway from <strong>idea → prototype → scale-up</strong>.
      Our facilities support high-throughput engineering, bioprocess development, and hands-on building.
    </p>

    <div class="cta-row">
      <a class="button" href="{{ '/facilities/' | relative_url }}">Explore facilities</a>
      <a class="button button-secondary" href="{{ '/partners/' | relative_url }}">Partner with us</a>
    </div>

    <div class="quick-facts">
      <div><strong>Focus:</strong> biomanufacturing, synthetic biology, scale-up, workforce</div>
      <div><strong>Services:</strong> DBTL workflows, fermentation, analytics, prototyping</div>
      <div><strong>Engagement:</strong> industry collaborations, training, shared resources</div>
    </div>

    <hr/>

    <h2 class="h3">Network resources</h2>
    <ul>
      <li><a href="https://www.wpi.edu/" target="_blank" rel="noreferrer">WPI website</a></li>
      <li><a href="https://www.mass.gov/orgs/massachusetts-bioindustrial-initiative" target="_blank" rel="noreferrer">MBI (Massachusetts Bioindustrial Initiative)</a></li>
      <li><a href="https://www.mass.gov/lists/massachusetts-bioindustrial-initiative" target="_blank" rel="noreferrer">MBI Regional Biomanufacturing Strategy</a></li>
      <li><a href="https://masstech.org/" target="_blank" rel="noreferrer">MassTech Collaborative</a></li>
    </ul>
  </div>

  <div class="hero-card">
    <h2 class="h3">Latest news</h2>
    {% assign items = site.data.news | sort: "date" | reverse | slice: 0, 3 %}
    {% if items.size > 0 %}
      <ul class="clean-list">
        {% for n in items %}
          {% include news-item.html item=n %}
        {% endfor %}
      </ul>
      <p><a href="{{ '/news/' | relative_url }}">All news →</a></p>
    {% else %}
      <p class="muted">No news yet.</p>
    {% endif %}
  </div>
</div>
