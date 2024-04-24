---
layout: page
title: Portfolio
cover-img: /assets/images/splash.jpg
---

{% assign gallery_folder = 'assets/images/portfolio' %}
{% assign sorted_files = site.static_files | sort: 'name' | reverse %}

<ul class="gallery">
{% for file in sorted_files %}
{%   if file.path contains gallery_folder and file.extname == '.jpg' %}
{%     assign filenameparts = file.path | split: "/" %}
{%     assign filename = filenameparts | last | replace: file.extname,"" %}
{%     unless file.path contains 'thumbnails' %}
    <li>
        <a href="{{ file.path | relative_url }}">
            <img src="{{ gallery_folder }}/thumbnails/{{ filename }}-tn.jpg" alt="{{ filename }}" />
        </a>
    </li>
{%     endunless %}
{%   endif %}
{% endfor %}
</ul>
