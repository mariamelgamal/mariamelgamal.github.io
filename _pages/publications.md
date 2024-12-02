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
  - bibquery: "@report"
    text: "Peer-Reviewed Workshop Publications"
  - bibquery: "@techreport"
    text: "Technical Reports"
  - bibquery: "@misc"
    text: "Theses"
nav: true
nav_order: 2
---
<!-- _pages/publications.md -->
<div class="publications">

{% bibliography -f {{ site.scholar.bibliography }} %}

</div>
