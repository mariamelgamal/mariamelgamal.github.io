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
nav: true
nav_order: 3
---
<!-- _pages/publications.md -->
<div class="publications">

{%- for section in page.sections %}
  <br/>
  <a id="{{section.text}}"></a>
  <h2 class="bibtitle">{{section.text}}</h2>
  {% bibliography -f {{site.scholar.bibliography}} -q {{section.bibquery}} %}
{%- endfor %}

</div>
