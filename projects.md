---
layout: default
title: Projects
permalink: /projects/
---

# Projects

These are selected, sanitised examples of practical ICT, automation and service delivery work.

<div id="filter-status" style="display: none; margin-bottom: 25px; background: #1e2530; padding: 10px 15px; border-radius: 6px; border: 1px solid #2d3748;">
  <span style="font-size: 0.95rem;">Filtering by: <strong id="active-tag-text" style="color: #00bcd4; text-transform: capitalize;"></strong></span>
  <button id="clear-filter" style="margin-left: 15px; background: #00bcd4; color: #10151d; border: none; padding: 4px 12px; border-radius: 4px; cursor: pointer; font-weight: 600; font-size: 0.8rem;">
    Show All
  </button>
</div>

<div class="card-grid">
  {% assign sorted_projects = site.projects | sort: "order" %}
  {% for project in sorted_projects %}
    
    {% assign project_tags = project.tags | join: ',' | downcase %}
    
    <article class="card" data-tags="{{ project_tags }}">
      <h2>
        <a href="{{ project.url | relative_url }}">
          {{ project.title }}
        </a>
      </h2>

      <p>{{ project.summary }}</p>

      {% if project.tags %}
        <ul class="badge-list">
          {% for tag in project.tags %}
            <li>
              <button class="tag-filter-btn" data-tag="{{ tag | downcase }}">
                {{ tag }}
              </button>
            </li>
          {% endfor %}
        </ul>
      {% endif %}
    </article>
  {% endfor %}
</div>

<script>
  document.addEventListener('DOMContentLoaded', function () {
    const tagButtons = document.querySelectorAll('.tag-filter-btn');
    const cards = document.querySelectorAll('.card');
    const filterStatus = document.getElementById('filter-status');
    const activeTagText = document.getElementById('active-tag-text');
    const clearFilterBtn = document.getElementById('clear-filter');

    tagButtons.forEach(button => {
      button.addEventListener('click', function (e) {
        e.preventDefault();
        const selectedTag = this.getAttribute('data-tag');
        filterProjects(selectedTag);
      });
    });

    clearFilterBtn.addEventListener('click', function () {
      resetFilter();
    });

    function filterProjects(tag) {
      cards.forEach(card => {
        const cardTags = card.getAttribute('data-tags').split(',');
        if (cardTags.includes(tag)) {
          card.style.display = 'flex';
        } else {
          card.style.display = 'none';
        }
      });

      // Update and show the filter status bar
      activeTagText.textContent = tag;
      filterStatus.style.display = 'block';
    }

    function resetFilter() {
      cards.forEach(card => {
        card.style.display = 'flex';
      });
      filterStatus.style.display = 'none';
    }
  });
</script>
