---
layout: pubs
permalink: /publications/
title: Publications
nav: true
nav_order: 2
---

{%- include working_papers.html %}

{% assign first_context = false %}
{% assign second_context = true %}

{%- include refereed_conference_papers.html %}

{% assign second_context = false %}
{% assign third_context = true %}

{%- include journal_papers.html %}

{% assign third_context = false %}
