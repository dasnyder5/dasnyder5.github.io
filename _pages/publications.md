---
layout: page
permalink: /publications/
title: Publications
nav: true
nav_order: 2
---

<!--
<h3>Working Papers</h3>

{% assign page.bib_context = "first" %}
{% bibliography -q @*[is_working=true]* %}


<h3>Refereed Conference Papers</h3>

{% assign page.bib_context = "second" %}
{% bibliography -q @*[is_conference=true]* %}

<h3>Journal Papers</h3>

{% assign page.bib_context = "third" %}
{% bibliography -q @*[is_journal=true]* %}
-->

{% assign page.bib_context = "first" %}
{%- include working_papers.html %}

{% assign page.bib_context = "second" %}
{%- include refereed_conference_papers.html %}

{% assign page.bib_context = "third" %}
{%- include journal_papers.html %}

{% assign page.bib_context = nil %}