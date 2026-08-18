---
layout: page
permalink: /publications/
title: Publications
nav: true
nav_order: 2
---

<div class="publications">

  <h2>Working Papers</h2>
  {% assign current_group = "working" %}
  {% bibliography -f papers -q @*[is_working=true]* %}

  <h2>Refereed Conference Papers</h2>
  {% assign current_group = "conference" %}
  {% bibliography -f papers -q @*[is_conference=true]* %}

  <h2>Journal Papers</h2>
  {% assign current_group = "journal" %}
  {% bibliography -f papers -q @*[is_journal=true]* %}

</div>
