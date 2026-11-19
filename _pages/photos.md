---
layout: page
permalink: /photos/
title: photos
description: A few favorite photos. Click a photo to enlarge it.
nav: false
---

<!--
  To add photos, drop .jpg/.jpeg/.png files into assets/img/photos/ — they appear here automatically,
  sorted by file name (prefix names like 2025-03-kyoto.jpg to control the order; newest-first below).
  Optional captions go in _data/photos.yml.
-->

{% assign photos = site.static_files | where_exp: "f", "f.path contains '/assets/img/photos/'" | sort: "name" | reverse %}
{% assign photos = photos | where_exp: "f", "f.extname == '.jpg' or f.extname == '.jpeg' or f.extname == '.png' or f.extname == '.JPG' or f.extname == '.JPEG' or f.extname == '.PNG'" %}

{% if photos.size == 0 %}

Photos coming soon.

{% else %}

<div class="row">
  {% for photo in photos %}
    {% assign photo_path = photo.path | remove_first: '/' %}
    {% assign caption = site.data.photos[photo.name] %}
    <div class="col-sm-6 col-md-4 mt-3">
      {% include figure.liquid path=photo_path class="img-fluid rounded z-depth-1" zoomable=true caption=caption alt=caption sizes="(min-width: 768px) 300px, (min-width: 576px) 45vw, 95vw" %}
    </div>
  {% endfor %}
</div>

{% endif %}
