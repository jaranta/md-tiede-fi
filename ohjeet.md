---
layout: page
title: Ohjeet
---


{% for ohje in site.ohjeet %}
<li>
<a href="{{ site.baseurl }}{{ ohje.url }}">{{ ohje.title }}</a>
</li>
{% endfor %}
