---
layout: default
title: Projects
permalink: /projects/
---

# Projects

These are selected, sanitised examples of practical ICT, automation and service delivery work.

<div class="card-grid">
  {% assign sorted_projects = site.projects | sort: "order" %}
  {% for project in sorted_projects %}
    <article class="card">
      <h2>
        {{ project.url | relative_url }}
          {{ project.title }}
        </a>
      </h2>

      <p>{{ project.summary }}</p>

      {% if project.tags %}
        <ul class="badge-list">
          {% for tag in project.tags %}
            <li>{{ tag }}</li>
          {% endfor %}
        </ul>
      {% endif %}
    </article>
  {% endfor %}
</div>