---
layout: default
title: "Blogs"
permalink: /formats/blogs/
---

# Blogs

Blog posts and articles that punch above their weight. These are shorter reads that either explain a complex concept exceptionally well, introduce a pattern I now use regularly, or changed how I think about a problem.

<ul class="entries-list">
{% assign entries = site.entries | where: 'format', 'blog' | sort: 'year' | reverse %}
{% for entry in entries %}
  <li>
    <a class="entry-link" href="{{ entry.url | relative_url }}">{{ entry.title }}</a>
    <div class="entry-info">
      {{ entry.author }}{% if entry.year %}, {{ entry.year }}{% endif %} &middot; {{ entry.topic | replace: '-', ' ' | capitalize }}
    </div>
  </li>
{% endfor %}
</ul>
