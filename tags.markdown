---
layout: page
title: Tags
permalink: /tags/
---

{% assign sorted_tags = site.tags | sort %}

{% if sorted_tags.size > 0 %}
<p>
{% for tag_entry in sorted_tags %}
{% assign tag_name = tag_entry[0] %}
<a class="chip chip--tag" href="#{{ tag_name | slugify }}">{{ tag_name }}</a>
{% endfor %}
</p>

{% for tag_entry in sorted_tags %}
{% assign tag_name = tag_entry[0] %}
{% assign tag_posts = tag_entry[1] %}
<section class="taxonomy-group" id="{{ tag_name | slugify }}">
  <h2>{{ tag_name }}</h2>
  <ul>
    {% for post in tag_posts %}
    <li>
      <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
      <span class="post-card__meta">({{ post.date | date: "%b %-d, %Y" }})</span>
    </li>
    {% endfor %}
  </ul>
</section>
{% endfor %}
{% else %}
<p>No tags found.</p>
{% endif %}
