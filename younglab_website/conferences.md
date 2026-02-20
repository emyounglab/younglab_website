---
layout: page
title: Conferences
permalink: /conferences/
---

{% assign today = site.time | date: '%s' %}
{% assign upcoming = "" | split: "" %}
{% assign past = "" | split: "" %}

{% for c in site.data.conferences %}
  {% if c.date %}
    {% assign cts = c.date | date: '%s' %}
    {% if cts >= today %}
      {% assign upcoming = upcoming | push: c %}
    {% else %}
      {% assign past = past | push: c %}
    {% endif %}
  {% else %}
    {% comment %}If no date, treat as upcoming so it shows up until you set one{% endcomment %}
    {% assign upcoming = upcoming | push: c %}
  {% endif %}
{% endfor %}

{% assign upcoming = upcoming | sort: "date" %}
{% assign past = past | sort: "date" | reverse %}

## Upcoming
{% if upcoming.size > 0 %}
  <p class="muted">Only upcoming items are shown here (based on the <code>date</code> field).</p>

  {% assign years = "" | split: "" %}
  {% for c in upcoming %}
    {% assign y = c.date | date: "%Y" %}
    {% unless years contains y %}
      {% assign years = years | push: y %}
    {% endunless %}
  {% endfor %}

  {% for y in years %}
  ### {{ y }}
    {% for c in upcoming %}
      {% if c.date and c.date | date: "%Y" == y %}
        <div class="pub-item">
          <div class="pub-title">
            {% if c.url %}
              <a href="{{ c.url }}" target="_blank" rel="noreferrer">{{ c.title }}</a>
            {% else %}
              {{ c.title }}
            {% endif %}
          </div>
          <div class="pub-authors">{{ c.presenters }}</div>
          <div class="pub-venue muted">
            {{ c.venue }}
            {% if c.type %} · {{ c.type }}{% endif %}
            {% if c.location %} · {{ c.location }}{% endif %}
            {% if c.date %} · {{ c.date | date: "%b %-d, %Y" }}{% endif %}
          </div>
          {% if c.tags %}
            <div class="pub-tags">
              {% for tag in c.tags %}
                <span class="tag">{{ tag }}</span>
              {% endfor %}
            </div>
          {% endif %}
        </div>
      {% endif %}
    {% endfor %}
  {% endfor %}
{% else %}
  <p class="muted">No upcoming conference items yet. Add them to <code>_data/conferences.yml</code>.</p>
{% endif %}

{% if past.size > 0 %}
<hr/>

## Past
<p class="muted">Most recent past items first.</p>
{% for c in past %}
  <div class="pub-item">
    <div class="pub-title">
      {% if c.url %}
        <a href="{{ c.url }}" target="_blank" rel="noreferrer">{{ c.title }}</a>
      {% else %}
        {{ c.title }}
      {% endif %}
    </div>
    <div class="pub-authors">{{ c.presenters }}</div>
    <div class="pub-venue muted">
      {{ c.venue }}
      {% if c.type %} · {{ c.type }}{% endif %}
      {% if c.location %} · {{ c.location }}{% endif %}
      {% if c.date %} · {{ c.date | date: "%b %-d, %Y" }}{% endif %}
    </div>
    {% if c.tags %}
      <div class="pub-tags">
        {% for tag in c.tags %}
          <span class="tag">{{ tag }}</span>
        {% endfor %}
      </div>
    {% endif %}
  </div>
{% endfor %}
{% endif %}