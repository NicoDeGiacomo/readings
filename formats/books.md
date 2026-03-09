---
layout: default
title: "Books"
permalink: /formats/books/
---

# Books

Books that are worth the time investment. Unlike papers or blog posts, these give you a deep, structured understanding of a topic. I only include books I've read substantially -- not ones I skimmed or abandoned halfway through.

<ul class="entries-list">
{% assign entries = site.entries | where: 'format', 'book' | sort: 'year' %}
{% for entry in entries %}
  <li>
    <a class="entry-link" href="{{ entry.url | relative_url }}">{{ entry.title }}</a>
    <div class="entry-info">
      {{ entry.author }}{% if entry.year %}, {{ entry.year }}{% endif %} &middot; {{ entry.topic | replace: '-', ' ' | capitalize }}
    </div>
  </li>
{% endfor %}
</ul>
