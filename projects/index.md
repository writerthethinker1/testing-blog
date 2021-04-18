---
layout: default
title: "Projects"
---

# {{ page.title }} <i class="fas fa-dice"></i>

{% for item in site.data.projects.structure %}
  <h2 style="color:#ECB055">{{ item.title }}</h2>
  <p>## {{ item.desc }}</p>
  <div>
  {% assign notes = site.static_files | where: item.reference, true %}
    {% for mystuff in notes %}
      <h3>## <a href="{{ site.baseurl }}{{ mystuff.path }}">{{ mystuff.basename }}</a></h3>
    {% endfor %}
  </div>
{% endfor %}
