---
layout: default
title: Evidence
permalink: /_evidence/
---

# Evidence by Capability

This page maps selected examples to capability areas. Detailed evidence remains private; these are public, sanitised summaries.

<div class="card-grid">
  {% assign sorted_evidence = site.evidence | sort: "order" %}
  {% for item in sorted_evidence %}
    <article class="card">
      <h2>
        {{ item.url | relative_url }}
          {{ item.title }}
        </a>
      </h2>

      <p>{{ item.summary }}</p>

      {% if item.tags %}
        <ul class="badge-list">
          {% for tag in item.tags %}
            <li>{{ tag }}</li>
          {% endfor %}
        </ul>
      {% endif %}
    </article>
  {% endfor %}
</div>