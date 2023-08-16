---
layout: page
title: Business for Acceleration

permalink: /Business/
---
I'm an accountant, equipped with a diverse skill set that spans beyond traditional number crunching. My multifaceted background as a tax preparer, bookkeeper, data analyst, and technology enthusiast empowers me to offer comprehensive and forward-thinking accounting services to individuals and businesses alike.
DECISION ANALYSIS| MANAGEMENT SCIENCE| PREDICTIVE MODELING |
8+ Yrs Financial Accounting and Tax Experience | [Certified QuickBooks ProAdvisor - Quickbooks Online (Advanced)](https://proadvisor.intuit.com/app/accountant/search?searchId=jordan-hay) | Data Science & Machine Learning | Dashboards and Data Visualization | Power BI | Power Query | Python

<ul>
  {%- for post in site.posts-%}
{% if post.categories contains 'biology' %}
  {%else %}
    <li>
    {%- assign date_format = site.minima.date_format | default: "%b %-d, %Y" -%}
    <span class="post-meta">{{ post.date | date: date_format }}</span>
    <h3>
     <a class="post-link" href="{{ post.url | relative_url }}">
      {{ post.title | escape }}
     </a>
     </h3>          
    </li>
{%endif %}
  
  
{%- endfor -%}
</ul>