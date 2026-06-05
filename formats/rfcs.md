---
layout: default
title: "RFCs"
permalink: /formats/rfcs/
---

# RFCs

The specifications themselves. RFCs are where the protocols and formats we build on are actually defined -- dense and precise, but the real source of truth when the secondary explanations disagree. These are the ones I've read closely enough to recommend.

<ul class="entries-list">
{% assign entries = site.entries | where: 'format', 'rfc' | sort: 'year' %}
{% for entry in entries %}
  <li>
    <a class="entry-link" href="{{ entry.url | relative_url }}">{{ entry.title }}</a>
    <div class="entry-info">
      {{ entry.author }}{% if entry.year %}, {{ entry.year }}{% endif %} &middot; {{ entry.topic | replace: '-', ' ' | capitalize }}
    </div>
  </li>
{% endfor %}
</ul>
