---
layout: default
title: Home
---

# Readings

<p class="page-description">Summaries, reasons to read, and key learnings from papers, books, and blog posts in software engineering.</p>

<div class="filters">
  <div class="filter-group">
    <span class="filter-label">Format</span>
    <button class="filter-pill active" data-filter="format" data-value="all">All</button>
    <button class="filter-pill" data-filter="format" data-value="paper">Paper</button>
    <button class="filter-pill" data-filter="format" data-value="book">Book</button>
    <button class="filter-pill" data-filter="format" data-value="blog">Blog</button>
  </div>
  <div class="filter-group">
    <span class="filter-label">Topic</span>
    <button class="filter-pill active" data-filter="topic" data-value="all">All</button>
    {% assign topics = site.entries | map: 'topic' | uniq | sort %}
    {% for topic in topics %}
    <button class="filter-pill" data-filter="topic" data-value="{{ topic }}">{{ topic | replace: '-', ' ' | capitalize }}</button>
    {% endfor %}
  </div>
</div>

<table class="entries-table">
  <thead>
    <tr>
      <th>Title</th>
      <th>Author</th>
      <th>Year</th>
      <th>Format</th>
      <th>Topic</th>
    </tr>
  </thead>
  <tbody>
  {% assign sorted_entries = site.entries | sort: 'year' | reverse %}
  {% for entry in sorted_entries %}
    <tr data-format="{{ entry.format }}" data-topic="{{ entry.topic }}">
      <td><a href="{{ entry.url | relative_url }}">{{ entry.title }}</a></td>
      <td>{{ entry.author }}</td>
      <td>{{ entry.year }}</td>
      <td><a href="{{ '/formats/' | append: entry.format | append: 's/' | relative_url }}">{{ entry.format | capitalize }}</a></td>
      <td><a href="{{ '/topics/' | append: entry.topic | append: '/' | relative_url }}">{{ entry.topic | replace: '-', ' ' | capitalize }}</a></td>
    </tr>
  {% endfor %}
  </tbody>
</table>

<p class="no-results" style="display:none;">No entries match the selected filters.</p>

<div class="browse-links">
  <div class="browse-section">
    <h3>Browse by topic</h3>
    <a href="{{ '/topics/distributed-systems/' | relative_url }}">Distributed Systems</a>
    <a href="{{ '/topics/information-theory/' | relative_url }}">Information Theory</a>
    <a href="{{ '/topics/operating-systems/' | relative_url }}">Operating Systems</a>
    <a href="{{ '/topics/microservices/' | relative_url }}">Microservices</a>
    <a href="{{ '/topics/security/' | relative_url }}">Security</a>
  </div>
  <div class="browse-section">
    <h3>Browse by format</h3>
    <a href="{{ '/formats/papers/' | relative_url }}">Papers</a>
    <a href="{{ '/formats/books/' | relative_url }}">Books</a>
    <a href="{{ '/formats/blogs/' | relative_url }}">Blogs</a>
  </div>
</div>

<script>
(function () {
  var active = { format: 'all', topic: 'all' };
  var pills = document.querySelectorAll('.filter-pill');
  var rows = document.querySelectorAll('.entries-table tbody tr');
  var noResults = document.querySelector('.no-results');

  function applyFilters() {
    var visible = 0;
    rows.forEach(function (row) {
      var matchFormat = active.format === 'all' || row.dataset.format === active.format;
      var matchTopic = active.topic === 'all' || row.dataset.topic === active.topic;
      var show = matchFormat && matchTopic;
      row.style.display = show ? '' : 'none';
      if (show) visible++;
    });
    noResults.style.display = visible === 0 ? '' : 'none';
  }

  pills.forEach(function (pill) {
    pill.addEventListener('click', function () {
      var group = this.dataset.filter;
      active[group] = this.dataset.value;
      document.querySelectorAll('.filter-pill[data-filter="' + group + '"]').forEach(function (p) {
        p.classList.remove('active');
      });
      this.classList.add('active');
      applyFilters();
    });
  });
})();
</script>
