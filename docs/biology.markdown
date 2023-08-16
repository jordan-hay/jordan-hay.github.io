---
layout: page
title: Biology for Amplification
menu: Biology for Amplification

permalink: /Biology/
---
I'm a biochemist. I've been teaching Biology for over 20 years and am a published author and award-winning research mentor to students.     
HIGH SCHOOL BIOLOGY LESSONS | RESEARCH PROJECTS | AP BIOLOGY
| RESEARCH INDEPENDENT STUDY| USABO | [EdTech Videos](https://www.youtube.com/@Biology101LearningCenter) | COnstraint-Based Reconstruction and Analysis (COBRA) | Flux Balance Analysis (FBA) | Metabolic Networks | Metabolic Engineering | MATLAB | Python

<ul>
  {%- for post in site.categories.biology -%}
  
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

