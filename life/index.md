---
layout: default
title: "Life"
---

# Life <i class="fas fa-feather-alt"></i>

> "Do not dwell in the past, do not dream of the future, concentrate the mind on the present moment." -- Buddha

---

{% for thing in site.life %}
  <h2><a href="{{ site.baseurl }}{{ thing.url }}">## {{ thing.title }} <i class="fas fa-feather-alt"></i></a></h2>
{% endfor %}
