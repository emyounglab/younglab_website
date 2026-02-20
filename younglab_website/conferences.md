---

layout: page

title: Conferences

permalink: /conferences/

---



{% assign today = site.time | date: '%s' %}

{% assign upcoming = "" | split: "" %}

{% assign past = "" | split: "" %}



{% for c in site.data.conferences %}

&nbsp; {% if c.date %}

&nbsp;   {% assign cts = c.date | date: '%s' %}

&nbsp;   {% if cts >= today %}

&nbsp;     {% assign upcoming = upcoming | push: c %}

&nbsp;   {% else %}

&nbsp;     {% assign past = past | push: c %}

&nbsp;   {% endif %}

&nbsp; {% else %}

&nbsp;   {% comment %}If no date, treat as upcoming so it shows up until you set one{% endcomment %}

&nbsp;   {% assign upcoming = upcoming | push: c %}

&nbsp; {% endif %}

{% endfor %}



{% assign upcoming = upcoming | sort: "date" %}

{% assign past = past | sort: "date" | reverse %}



\## Upcoming

{% if upcoming.size > 0 %}

&nbsp; <p class="muted">Only upcoming items are shown here (based on the <code>date</code> field).</p>



&nbsp; {% assign years = "" | split: "" %}

&nbsp; {% for c in upcoming %}

&nbsp;   {% assign y = c.date | date: "%Y" %}

&nbsp;   {% unless years contains y %}

&nbsp;     {% assign years = years | push: y %}

&nbsp;   {% endunless %}

&nbsp; {% endfor %}



&nbsp; {% for y in years %}

&nbsp; ### {{ y }}

&nbsp;   {% for c in upcoming %}

&nbsp;     {% if c.date and c.date | date: "%Y" == y %}

&nbsp;       <div class="pub-item">

&nbsp;         <div class="pub-title">

&nbsp;           {% if c.url %}

&nbsp;             <a href="{{ c.url }}" target="\_blank" rel="noreferrer">{{ c.title }}</a>

&nbsp;           {% else %}

&nbsp;             {{ c.title }}

&nbsp;           {% endif %}

&nbsp;         </div>

&nbsp;         <div class="pub-authors">{{ c.presenters }}</div>

&nbsp;         <div class="pub-venue muted">

&nbsp;           {{ c.venue }}

&nbsp;           {% if c.type %} · {{ c.type }}{% endif %}

&nbsp;           {% if c.location %} · {{ c.location }}{% endif %}

&nbsp;           {% if c.date %} · {{ c.date | date: "%b %-d, %Y" }}{% endif %}

&nbsp;         </div>

&nbsp;         {% if c.tags %}

&nbsp;           <div class="pub-tags">

&nbsp;             {% for tag in c.tags %}

&nbsp;               <span class="tag">{{ tag }}</span>

&nbsp;             {% endfor %}

&nbsp;           </div>

&nbsp;         {% endif %}

&nbsp;       </div>

&nbsp;     {% endif %}

&nbsp;   {% endfor %}

&nbsp; {% endfor %}

{% else %}

&nbsp; <p class="muted">No upcoming conference items yet. Add them to <code>\_data/conferences.yml</code>.</p>

{% endif %}



{% if past.size > 0 %}

<hr/>



\## Past

<p class="muted">Most recent past items first.</p>

{% for c in past %}

&nbsp; <div class="pub-item">

&nbsp;   <div class="pub-title">

&nbsp;     {% if c.url %}

&nbsp;       <a href="{{ c.url }}" target="\_blank" rel="noreferrer">{{ c.title }}</a>

&nbsp;     {% else %}

&nbsp;       {{ c.title }}

&nbsp;     {% endif %}

&nbsp;   </div>

&nbsp;   <div class="pub-authors">{{ c.presenters }}</div>

&nbsp;   <div class="pub-venue muted">

&nbsp;     {{ c.venue }}

&nbsp;     {% if c.type %} · {{ c.type }}{% endif %}

&nbsp;     {% if c.location %} · {{ c.location }}{% endif %}

&nbsp;     {% if c.date %} · {{ c.date | date: "%b %-d, %Y" }}{% endif %}

&nbsp;   </div>

&nbsp;   {% if c.tags %}

&nbsp;     <div class="pub-tags">

&nbsp;       {% for tag in c.tags %}

&nbsp;         <span class="tag">{{ tag }}</span>

&nbsp;       {% endfor %}

&nbsp;     </div>

&nbsp;   {% endif %}

&nbsp; </div>

{% endfor %}

{% endif %}



