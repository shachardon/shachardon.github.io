---
layout: sd-page
title: "Personal"
eyebrow: "Off the clock"
lede: "When I'm not working on papers, I enjoy traveling and exploring new places with my husband Daniel and little Telem."
permalink: /personal/

# Travel highlights — newest first. `image` is a web-sized copy in /images/web/.
trips:
  - place: "Utah"
    year: 2025
    caption: "Dead Horse Point State Park"
    image: "/images/web/utah.jpg"
  - place: "Scotland"
    year: 2024
    caption: "Old Man of Storr"
    image: "/images/web/scotland_24.jpg"
  - place: "Scotland"
    year: 2023
    caption: "The West Highland Way"
    image: "/images/web/scotland_23.jpg"
  - place: "Canada"
    year: 2022
    caption: "Wilcox Pass Trail, Alberta"
    image: "/images/web/canada.jpg"
---

<h2 class="sd-h2 sd-h2--small">Some highlights from my travels</h2>

<div class="sd-gallery">
  {% for t in page.trips %}
  <figure class="sd-photo{% if forloop.first %} sd-photo--wide{% endif %}">
    <img src="{{ t.image }}" alt="{{ t.caption }}, {{ t.place }} {{ t.year }}" loading="lazy">
    <figcaption>
      <span class="sd-photo__place">{{ t.place }} <span>{{ t.year }}</span></span>
      <span class="sd-photo__caption">{{ t.caption }}</span>
    </figcaption>
  </figure>
  {% endfor %}
</div>

<p class="sd-muted sd-center">More photos and stories coming soon!</p>
