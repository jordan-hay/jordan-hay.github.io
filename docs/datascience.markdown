---
layout: page
title: DataSci
menu: DataSci
pagetitle: Data Science for Discovery

permalink: /Data/
---
Decision Intelligence, Artificial Intelligence, Statistics, Numerical Analysis

<ul>
  {%- for post in site.categories.data -%}
  
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

