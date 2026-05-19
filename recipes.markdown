---
layout: page
title: Recipes
permalink: /recipes/
---

<p>Browse every recipe from newest to oldest.</p>

{% if site.posts.size > 0 %}
  <div class="cards-grid">
    {% for post in site.posts %}
      {% include post-card.html post=post %}
    {% endfor %}
  </div>
{% else %}
  <p>No recipes have been published yet.</p>
{% endif %}
