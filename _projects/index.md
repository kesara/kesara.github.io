---
layout:         page
title:          Projects
description:    FOSS Projects
permalink:      /projects/
---

{% for item in site.projects %}
  {% if item.title != "Projects" %}
## [{{ item.title }}]({{ item.url }})

{{ item.description }}
  {% endif %}
{% endfor %}
