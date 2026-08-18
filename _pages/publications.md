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
<!-- 1. DEPENDENCIES: Only keep these if your platform doesn't already load jQuery -->
<script src="https://jquery.com"></script>
<script src="https://jsdelivr.net"></script>

<!-- 2. STYLING: Scoped CSS rules for the bracketed countdown layout -->
<style>
    #bibtex_display {
        list-style: none;
        padding-left: 0;
    }
    #bibtex_display li {
        counter-increment: bib-counter -1; 
        margin-bottom: 12px;
        position: relative;
        padding-left: 2.5em;
    }
    #bibtex_display li::before {
        content: "[" counter(bib-counter) "] ";
        position: absolute;
        left: 0;
        top: 0;
        font-weight: bold;
    }
</style>

<!-- 3. TEMPLATE: Tells bibtex-js how to format the text inside each entry -->
<div id="bibtex_structure" style="display:none;">
    <div class="sections">
        <div class="info">
            <span class="author"></span>. 
            <span class="title" style="font-weight: bold;"></span>. 
            <span class="journal" style="font-style: italic;"></span> 
            <span class="year"></span>.
        </div>
    </div>
</div>

<!-- 4. CONTAINERS: Where the template outputs your compiled entries -->
<ol id="bibtex_errors"></ol>
<ol id="bibtex_display"></ol>

<!-- 5. DATA SOURCE: Tells the script to fetch your file and reverse-sort it -->
<bibtex src="../_bibliography/papers.bib" sort="year" order="desc"></bibtex>

<!-- 6. AUTOMATION: Calculates the total dynamic entries to set your starting number -->
<script>
    $(window).on('load', function() {
        setTimeout(function() {
            var totalItems = $('#bibtex_display li').length;
            $('#bibtex_display').css('counter-reset', 'bib-counter ' + (totalItems + 1));
        }, 500); 
    });
</script>
