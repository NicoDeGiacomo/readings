---
layout: default
title: "Information Theory"
permalink: /topics/information-theory/
---

# Information Theory

<ul class="entries-list">
{% assign entries = site.entries | where: 'topic', 'information-theory' | sort: 'year' | reverse %}
{% for entry in entries %}
  <li>
    <a class="entry-link" href="{{ entry.url | relative_url }}">{{ entry.title }}</a>
    <div class="entry-info">
      {{ entry.author }}{% if entry.year %}, {{ entry.year }}{% endif %} &middot; {% include format-label.html format=entry.format %}
    </div>
  </li>
{% endfor %}
</ul>
