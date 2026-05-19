---
layout: page
title: Categories
permalink: /categories/
---

{% assign sorted_categories = site.categories | sort %}

{% if sorted_categories.size > 0 %}
<p>
{% for category_entry in sorted_categories %}
{% assign category_name = category_entry[0] %}
<a class="chip" href="#{{ category_name | slugify }}">{{ category_name }}</a>
{% endfor %}
</p>

{% for category_entry in sorted_categories %}
{% assign category_name = category_entry[0] %}
{% assign category_posts = category_entry[1] %}
<section class="taxonomy-group" id="{{ category_name | slugify }}">
  <h2>{{ category_name }}</h2>
  <ul>
    {% for post in category_posts %}
    <li>
      <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
      <span class="post-card__meta">({{ post.date | date: "%b %-d, %Y" }})</span>
    </li>
    {% endfor %}
  </ul>
</section>
{% endfor %}
{% else %}
<p>No categories found.</p>
{% endif %}
