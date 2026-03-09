---
layout: default
title: "Papers"
permalink: /formats/papers/
---

# Papers

The papers that shaped how we think about computing. These aren't just historically important -- they contain ideas that are still directly applicable to the systems we build today. I've picked the ones I found most valuable as a practitioner, not as an academic exercise.

<ul class="entries-list">
{% assign entries = site.entries | where: 'format', 'paper' | sort: 'year' %}
{% for entry in entries %}
  <li>
    <a class="entry-link" href="{{ entry.url | relative_url }}">{{ entry.title }}</a>
    <div class="entry-info">
      {{ entry.author }}{% if entry.year %}, {{ entry.year }}{% endif %} &middot; {{ entry.topic | replace: '-', ' ' | capitalize }}
    </div>
  </li>
{% endfor %}
</ul>
