---
layout: page
permalink: /publications/
title: publications
description: 
sections:
  - bibquery: "@inproceedings"
    text: "Publications"
  - bibquery: "@misc"
    text: "Peer-Reviewed Workshop Publications"
  - bibquery: "@article"
    text: "Journal Publications"
  - bibquery: "@techreport"
    text: "Non-Technical Articles"
nav: true
nav_order: 3
---
<!-- _pages/publications.md -->
<div class="publications">

{%- for section in page.sections %}
  <br/>
  <a id="{{section.text}}"></a>
  <h3 class="bibtitle">{{section.text}}</h3>
  {% bibliography -f {{site.scholar.bibliography}} -q {{section.bibquery}} %}
{%- endfor %}

</div>
