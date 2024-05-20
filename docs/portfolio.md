---
layout: page
title: Portfolio
cover-img: /assets/images/splash.jpg
---

{% assign gallery_folder = 'assets/images/portfolio' %}
{% assign sorted_files = site.static_files | sort: 'name' | reverse %}

<div class="portfolio row mt-3">
{% for file in sorted_files %}
{%   if file.path contains gallery_folder and file.extname == '.jpg' %}
{%     assign filenameparts = file.path | split: "/" %}
{%     assign filename = filenameparts | last | replace: file.extname,"" %}
{%     unless file.path contains 'thumbnails' %}
  <div class="col mb-5">
    <a href="{{ file.path | relative_url }}">
      <img src="{{ gallery_folder }}/thumbnails/{{ filename }}.jpg" alt="{{ filename }}" />
    </a>
  </div>
{%     endunless %}
{%   endif %}
{% endfor %}
</div>
