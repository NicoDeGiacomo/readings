---
layout: default
title: "AI Engineering"
permalink: /topics/ai-engineering/
---

# AI Engineering

<ul class="entries-list">
{% assign entries = site.entries | where: 'topic', 'ai-engineering' | sort: 'year' | reverse %}
{% for entry in entries %}
  <li>
    <a class="entry-link" href="{{ entry.url | relative_url }}">{{ entry.title }}</a>
    <div class="entry-info">
      {{ entry.author }}{% if entry.year %}, {{ entry.year }}{% endif %} &middot; {{ entry.format | capitalize }}
    </div>
  </li>
{% endfor %}
</ul>
