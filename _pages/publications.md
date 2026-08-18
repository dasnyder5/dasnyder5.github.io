---
layout: page
permalink: /publications/
title: Publications
nav: true
nav_order: 2
---

<!-- 2. YOUR CONTENT AND BIBLIOGRAPHY LISTS -->
<h3>Working Papers</h3>
<div class="custom-bib-group" data-sort-attr="usera" data-sort-order="desc">
  {% bibliography -q @*[is_working=true]* --extra usera %}
</div>

<h3>Conference Papers</h3>
<div class="custom-bib-group" data-sort-attr="userb" data-sort-order="desc">
  {% bibliography -q @*[is_conference=true]* --extra userb %}
</div>

<!-- 3. PLACE THE CONTROLLER SCRIPT AT THE ABSOLUTE BOTTOM OF THE FILE -->
<script>
  document.addEventListener("DOMContentLoaded", function() {
    document.querySelectorAll('.custom-bib-group').forEach(group => {
      const attrName = group.getAttribute('data-sort-attr');   
      const sortOrder = group.getAttribute('data-sort-order'); 
      
      const listParent = group.querySelector('ol.bibliography, ul.bibliography');
      if (!listParent) return;

      const items = Array.from(listParent.querySelectorAll('li'));

      items.sort((a, b) => {
        const classA = Array.from(a.classList).find(c => c.startsWith(attrName + '-'));
        const classB = Array.from(b.classList).find(c => c.startsWith(attrName + '-'));

        let valA = classA ? parseInt(classA.substring(attrName.length + 1)) : 0;
        let valB = classB ? parseInt(classB.substring(attrName.length + 1)) : 0;

        return sortOrder === 'desc' ? (valB - valA) : (valA - valB);
      });

      items.forEach((item, index) => {
        listParent.appendChild(item);

        if (!item.querySelector('.bib-bracket')) {
          const bracket = document.createElement('span');
          bracket.className = 'bib-bracket';
          bracket.textContent = `[${index + 1}] `;
          item.insertBefore(bracket, item.firstChild);
        }
      });
    });
  });
</script>