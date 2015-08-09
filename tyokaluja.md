---
layout: page
title: Työkaluja
---

Tässä listattuna erilaisia työkaluja, joille tällä sivustolla on ohjeita.

{% for tyokalu in site.tyokalut %}
<li>
<a href="{{ site.baseurl }}{{ tyokalu.url }}">{{ tyokalu.title }}</a>
</li>
{% endfor %}
