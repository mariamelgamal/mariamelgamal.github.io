---
layout: page
permalink: /publications/
title: publications
description: 
sections:
  - bibquery: "@inproceedings"
    text: "Conference Publications"
  - bibquery: "@article"
    text: "Journal Publications"
  - bibquery: "@techrepor"
    text: "Peer-Reviewed Workshop Publications"
  - bibquery: "@misc"
    text: "Theses"
nav: true
nav_order: 2
---
<!-- _pages/publications.md -->
<div class="publications">

{%- for section in page.sections %}
  <a id="{{section.text}}"></a>
  <h3 class="bibtitle">{{section.text}}</h3>
  {% bibliography -f {{ site.scholar.bibliography }} %}
{%- endfor %}

</div>
