---
layout: default
title: "Microservices"
permalink: /topics/microservices/
---

# Microservices

<ul class="entries-list">
{% assign entries = site.entries | where: 'topic', 'microservices' | sort: 'year' | reverse %}
{% for entry in entries %}
  <li>
    <a class="entry-link" href="{{ entry.url | relative_url }}">{{ entry.title }}</a>
    <div class="entry-info">
      {{ entry.author }}{% if entry.year %}, {{ entry.year }}{% endif %} &middot; {{ entry.format | capitalize }}
    </div>
  </li>
{% endfor %}
</ul>
