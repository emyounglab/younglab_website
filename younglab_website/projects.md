---

layout: page

title: Projects

permalink: /projects/

---



<p class="muted">Projects are managed in <code>\_data/projects.yml</code>.</p>



<div class="cards">

{% for proj in site.data.projects %}

&nbsp; {% include project-card.html project=proj %}

{% endfor %}

</div>



