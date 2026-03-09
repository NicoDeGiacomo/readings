---
layout: default
title: Home
---

# Readings

<p class="page-description">Summaries, reasons to read, and key learnings from papers, books, and blog posts in software engineering.</p>

<div class="filter-bar">
  <span>Topics:</span>
  <a href="{{ '/' | relative_url }}">All</a>
  <a href="{{ '/topics/distributed-systems/' | relative_url }}">Distributed Systems</a>
  <a href="{{ '/topics/information-theory/' | relative_url }}">Information Theory</a>
  <a href="{{ '/topics/operating-systems/' | relative_url }}">Operating Systems</a>
  <a href="{{ '/topics/microservices/' | relative_url }}">Microservices</a>
  <a href="{{ '/topics/security/' | relative_url }}">Security</a>
</div>

<div class="filter-bar">
  <span>Format:</span>
  <a href="{{ '/' | relative_url }}">All</a>
  <a href="{{ '/formats/papers/' | relative_url }}">Papers</a>
  <a href="{{ '/formats/books/' | relative_url }}">Books</a>
  <a href="{{ '/formats/blogs/' | relative_url }}">Blogs</a>
</div>

<ul class="entries-list">
{% assign sorted_entries = site.entries | sort: 'year' | reverse %}
{% for entry in sorted_entries %}
  <li>
    <a class="entry-link" href="{{ entry.url | relative_url }}">{{ entry.title }}</a>
    <div class="entry-info">
      {{ entry.author }}{% if entry.year %}, {{ entry.year }}{% endif %} &middot; {{ entry.format | capitalize }} &middot; {{ entry.topic | replace: '-', ' ' | capitalize }}
    </div>
  </li>
{% endfor %}
</ul>
