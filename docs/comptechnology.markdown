---
layout: page
title: CompTech
menu: CompTech
pagetitle: Technology for Innovation

permalink: /Technology/
---
Intersection of BioChem, BusAcct and technology through a coding lens.

<ul>
  {%- for post in site.categories.technology -%}
  
    <li>
    {%- assign date_format = site.minima.date_format | default: "%b %-d, %Y" -%}
    <span class="post-meta">{{ post.date | date: date_format }}</span>
    <h3>
     <a class="post-link" href="{{ post.url | relative_url }}">
      {{ post.title | escape }}
     </a>
     </h3>          
    </li>
  
  
{%- endfor -%}
</ul>

