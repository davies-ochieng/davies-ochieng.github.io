---
title: ""
layout: single
permalink: /projects/
---

{% for project in site.projects %}
- [{{ project.title }}]({{ project.url }})
{% endfor %}

### A series of my projects will be premiering in a few
Thank you for your patience
<div class="project-grid">
{% for project in site.projects %}
  <div class="project-card">
    <h3>{{ project.title }}</h3>

    <p>{{ project.excerpt }}</p>

    <a href="{{ project.url | relative_url }}">
      View Project →
    </a>
  </div>
{% endfor %}
</div>
