---
layout: sd-page
title: "Publications"
eyebrow: "Research output"
permalink: /publications/
---
{% comment %}
  Publications live in _data/publications.yml — add new papers there (newest first).
{% endcomment %}
{% assign pubs = site.data.publications %}
{% assign first = pubs | first %}
{% assign last = pubs | last %}

<div class="sd-pubbar">
  <p class="sd-pubbar__count"><strong>{{ pubs.size }}</strong> papers · {{ last.year }}–{{ first.year }} · also on <a href="{{ site.author.googlescholar }}">Google Scholar</a></p>
  <div class="sd-filters" role="group" aria-label="Filter by topic">
    <button type="button" class="sd-filter" data-filter="all" aria-pressed="true">All</button>
    <button type="button" class="sd-filter" data-filter="interaction" aria-pressed="false">Human–AI interaction</button>
    <button type="button" class="sd-filter" data-filter="feedback" aria-pressed="false">Human feedback</button>
    <button type="button" class="sd-filter" data-filter="evaluation" aria-pressed="false">Evaluation</button>
    <button type="button" class="sd-filter" data-filter="collaborative" aria-pressed="false">Collaborative training</button>
  </div>
</div>

{% assign years = pubs | group_by: "year" %}
{% for y in years %}
<section class="sd-year" data-year>
  <h2 class="sd-year__label">{{ y.name }}</h2>
  <div class="sd-pubs">
    {% for p in y.items %}{% include sd-pub.html pub=p %}{% endfor %}
  </div>
</section>
{% endfor %}

<script>
  (function () {
    var btns = document.querySelectorAll(".sd-filter");
    var pubs = document.querySelectorAll(".sd-pub");
    var years = document.querySelectorAll("[data-year]");
    btns.forEach(function (b) {
      b.addEventListener("click", function () {
        var f = b.getAttribute("data-filter");
        btns.forEach(function (x) { x.setAttribute("aria-pressed", x === b ? "true" : "false"); });
        pubs.forEach(function (p) {
          var show = f === "all" || (" " + p.getAttribute("data-topics") + " ").indexOf(" " + f + " ") > -1;
          p.hidden = !show;
        });
        years.forEach(function (y) {
          y.hidden = !y.querySelector(".sd-pub:not([hidden])");
        });
      });
    });
  })();
</script>
