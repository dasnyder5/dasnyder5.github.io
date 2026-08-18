---
layout: page
permalink: /publications/
title: Publications
nav: true
nav_order: 2
---

<!-- ======================================================= -->
<!-- BIBLIOGRAPHY 1: Working Papers                          -->
<!-- ======================================================= -->
<h3>Working Papers</h3>

{% assign page.bib_context = "first" %}
{% bibliography -q @*[is_working=true]* %}


<!-- ======================================================= -->
<!-- BIBLIOGRAPHY 2: Conference Papers                       -->
<!-- ======================================================= -->
<h3>Refereed Conference Papers</h3>

{% assign page.bib_context = "second" %}
{% bibliography -q @*[is_conference=true]* %}

<!-- ======================================================= -->
<!-- BIBLIOGRAPHY 3: Journal Papers                          -->
<!-- ======================================================= -->
<h3>Journal Papers</h3>

{% assign page.bib_context = "second" %}
{% bibliography -q @*[is_journal=true]* %}

<!-- ======================================================= -->
<!-- SANITIZATION: Clean up the variable state               -->
<!-- ======================================================= -->
{% assign page.bib_context = nil %}

<!--
{%- include working_papers.html %}

{%- include refereed_conference_papers.html %}

{%- include journal_papers.html %} -->