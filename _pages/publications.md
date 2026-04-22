---
layout: page
permalink: /publications/
title: publications
description:
nav: true
nav_order: 3
---
<!-- _pages/publications.md -->
<div class="publications">

  <div class="pub-filters" role="tablist" aria-label="Filter publications by type">
    <button type="button" class="pub-filter is-active" role="tab" aria-selected="true" data-filter="all">
      All publications
      <span class="pub-filter-count" data-count-for="all"></span>
    </button>
    <button type="button" class="pub-filter" role="tab" aria-selected="false" data-filter="conference">
      Conferences
      <span class="pub-filter-count" data-count-for="conference"></span>
    </button>
    <button type="button" class="pub-filter" role="tab" aria-selected="false" data-filter="journal">
      Journals
      <span class="pub-filter-count" data-count-for="journal"></span>
    </button>
    <button type="button" class="pub-filter" role="tab" aria-selected="false" data-filter="workshop">
      Workshops
      <span class="pub-filter-count" data-count-for="workshop"></span>
    </button>
    <button type="button" class="pub-filter" role="tab" aria-selected="false" data-filter="other">
      Others
      <span class="pub-filter-count" data-count-for="other"></span>
    </button>
    <button type="button" class="pub-filter pub-filter-awards" role="tab" aria-selected="false" data-filter="awarded">
      Paper awards
      <span class="pub-filter-count" data-count-for="awarded"></span>
    </button>
  </div>

  <div class="pub-timeline">
    {% bibliography -f {{site.scholar.bibliography}} %}
  </div>

</div>

<script>
  (function () {
    var timeline = document.querySelector('.pub-timeline');
    if (!timeline) return;

    // Propagate data-pubtype from inner .pub-entry up to the <li> that
    // jekyll-scholar wraps each entry in, so we can hide/show via CSS.
    var entries = timeline.querySelectorAll('.pub-entry[data-pubtype]');
    var counts = { all: 0, conference: 0, workshop: 0, journal: 0, other: 0, awarded: 0 };

    entries.forEach(function (entry) {
      var li = entry.closest('li');
      if (!li) return;
      var type = entry.getAttribute('data-pubtype') || 'other';
      li.setAttribute('data-pubtype', type);
      counts.all++;
      type.split(/\s+/).forEach(function (t) {
        if (!t) return;
        counts[t] = (counts[t] || 0) + 1;
      });
      var awardN = parseInt(entry.getAttribute('data-awards') || '0', 10);
      if (awardN > 0) {
        li.setAttribute('data-awarded', 'true');
        counts.awarded += awardN;
      }
    });

    document.querySelectorAll('.pub-filter-count').forEach(function (el) {
      var key = el.getAttribute('data-count-for');
      var n = counts[key] != null ? counts[key] : 0;
      el.textContent = n;
      if (key !== 'all' && n === 0) {
        var btn = el.closest('.pub-filter');
        if (btn) btn.hidden = true;
      }
    });

    var filters = document.querySelectorAll('.pub-filter');
    filters.forEach(function (btn) {
      btn.addEventListener('click', function () {
        var value = btn.getAttribute('data-filter');
        filters.forEach(function (b) {
          var active = b === btn;
          b.classList.toggle('is-active', active);
          b.setAttribute('aria-selected', active ? 'true' : 'false');
        });
        timeline.setAttribute('data-active-filter', value);
      });
    });

    // Default filter
    timeline.setAttribute('data-active-filter', 'all');
  })();
</script>
