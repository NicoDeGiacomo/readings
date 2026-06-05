---
layout: default
title: Home
---

<h1 class="home-title">Readings</h1>
<p class="home-subtitle">Summaries, reasons to read, and key learnings from papers, books, and blog posts in software engineering.</p>

<div class="filters">
  <div class="filter-group">
    <span class="filter-label">Format</span>
    <button class="filter-pill active" data-filter="format" data-value="all">All</button>
    <button class="filter-pill" data-filter="format" data-value="paper">Paper</button>
    <button class="filter-pill" data-filter="format" data-value="book">Book</button>
    <button class="filter-pill" data-filter="format" data-value="blog">Blog</button>
    <button class="filter-pill" data-filter="format" data-value="rfc">RFC</button>
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
      <td><a href="{{ '/formats/' | append: entry.format | append: 's/' | relative_url }}">{% include format-label.html format=entry.format %}</a></td>
      <td><a href="{{ '/topics/' | append: entry.topic | append: '/' | relative_url }}">{{ entry.topic | replace: '-', ' ' | capitalize }}</a></td>
    </tr>
  {% endfor %}
  </tbody>
</table>

<p class="no-results" style="display:none;">No entries match the selected filters.</p>

<div class="browse-links">
  <div class="browse-section">
    <h3>Browse by topic</h3>
    <a href="{{ '/topics/ai-engineering/' | relative_url }}">AI Engineering</a>
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
    <a href="{{ '/formats/rfcs/' | relative_url }}">RFCs</a>
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
      if (show) {
        row.style.display = '';
        row.style.opacity = '0';
        row.style.transform = 'translateY(4px)';
        requestAnimationFrame(function () {
          row.style.transition = 'opacity 0.3s ease, transform 0.3s ease';
          row.style.opacity = '1';
          row.style.transform = 'translateY(0)';
        });
        visible++;
      } else {
        row.style.display = 'none';
      }
    });
    noResults.style.display = visible === 0 ? '' : 'none';
    markLastVisible();
    updatePillAvailability();
  }

  function markLastVisible() {
    var last = null;
    rows.forEach(function (row) {
      row.classList.remove('last-visible');
      if (row.style.display !== 'none') {
        last = row;
      }
    });
    if (last) {
      last.classList.add('last-visible');
    }
  }

  function updatePillAvailability() {
    pills.forEach(function (pill) {
      var group = pill.dataset.filter;
      var value = pill.dataset.value;
      if (value === 'all') {
        pill.classList.remove('disabled');
        return;
      }
      var otherGroup = group === 'format' ? 'topic' : 'format';
      var otherActive = active[otherGroup];
      var hasMatch = Array.prototype.some.call(rows, function (row) {
        return row.dataset[group] === value &&
          (otherActive === 'all' || row.dataset[otherGroup] === otherActive);
      });
      pill.classList.toggle('disabled', !hasMatch);
    });
  }

  pills.forEach(function (pill) {
    pill.addEventListener('click', function () {
      if (this.classList.contains('disabled')) return;
      var group = this.dataset.filter;
      active[group] = this.dataset.value;
      document.querySelectorAll('.filter-pill[data-filter="' + group + '"]').forEach(function (p) {
        p.classList.remove('active');
      });
      this.classList.add('active');
      applyFilters();
    });
  });

  markLastVisible();
  updatePillAvailability();
})();
</script>
