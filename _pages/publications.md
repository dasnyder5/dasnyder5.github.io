---
layout: pubs
permalink: /publications/
title: Publications
nav: true
nav_order: 2
---

{% assign current_context = "first" %}
{%- include working_papers.html %}

{% assign current_context = "second" %}
{%- include refereed_conference_papers.html %}

{% assign current_context = "third" %}
{%- include journal_papers.html %}

{% assign current_context = nil %}
