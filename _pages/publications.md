---
layout: page
permalink: /publications/
title: Publications
subtitle: A list of publications
nav: true
nav_order: 2
horizontal: false
papers: true
---
<script src="https://jquery.com"></script>
<script src="https://jsdelivr.net"></script>

<!-- 2. STYLING: No more reverse-counting hacks needed -->
<style>
    /* Turn off standard list styles to use brackets */
    #bibtex_display {
        list-style: none;
        padding-left: 0;
    }
    #bibtex_display li {
        margin-bottom: 12px;
        position: relative;
        padding-left: 2.5em;
    }
    /* Grabs the order number directly from the bibtex template layout below */
    #bibtex_display li::before {
        content: "[" attr(data-order) "] ";
        position: absolute;
        left: 0;
        top: 0;
        font-weight: bold;
    }
</style>

<!-- 3. TEMPLATE: Map the custom bibtex field to an HTML 'data-' attribute -->
<div id="bibtex_structure" style="display:none;">
    <div class="sections">
        <!-- The library will inject your custom number into 'data-order' -->
        <div class="info" data-order="order_number">
            <span class="author"></span>. 
            <span class="title" style="font-weight: bold;"></span>. 
            <span class="journal" style="font-style: italic;"></span> 
            <span class="year"></span>.
        </div>
    </div>
</div>

<!-- 4. CONTAINERS -->
<ol id="bibtex_errors"></ol>
<ol id="bibtex_display"></ol>

<!-- 5. DATA SOURCE: Tell it to sort by your custom field in descending order -->
<bibtex src="page_assets/full_publications.bib" sort="order_number" order="desc"></bibtex>
