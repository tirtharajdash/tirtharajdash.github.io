---
layout: page
permalink: /publications/
title: publications
description: Publications in reversed chronological order. Selected preprints are included.
years: [2026,2025,2024,2023,2022,2021,2020,2019,2018,2017,2016,2015,2014]
nav: true
nav_order: 2
---
<!-- _pages/publications.md -->

<div class="pub-note">
This page may not always be up to date. For the most current list, see my <a rel="external nofollow" href="https://scholar.google.com/citations?user=1ZcwKZEAAAAJ" target="_blank">Google Scholar profile</a>. For the group's publications, visit the <a href="https://mahi-group.github.io/publications/" target="_blank">MAHI Lab publications page</a>.
</div>

<div class="publications">

{%- for y in page.years %}
  <h2 class="year">{{y}}</h2>
  {% bibliography -f papers -q @*[year={{y}}]* %}
{% endfor %}

</div>
