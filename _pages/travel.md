---
layout: page
permalink: /travel/
title: travel
description: Places I've been, for conferences, research, and fun.
nav: false
map: true
---

<!-- Add trips in _data/travel.yml; entries with lat/lon also appear on the map. -->

{% assign places = site.data.travel.places %}
{% assign mapped = places | where_exp: "p", "p.lat and p.lon" %}

{% if places.size == 0 %}

Travel notes and photos coming soon.

{% else %}

{% if mapped.size > 0 %}

```geojson
{
  "type": "FeatureCollection",
  "features": [
    {% for p in mapped %}{ "type": "Feature", "properties": { "name": {{ p.place | jsonify }} }, "geometry": { "type": "Point", "coordinates": [{{ p.lon }}, {{ p.lat }}] } }{% unless forloop.last %},{% endunless %}
    {% endfor %}
  ]
}
```

{% endif %}

{% assign by_year = places | group_by: "year" | sort: "name" | reverse %}
{% for group in by_year %}

<h2 class="year">{{ group.name }}</h2>

<ul class="travel-list">
  {% for p in group.items %}
    <li>
      <strong>{% if p.link %}<a href="{{ p.link | relative_url }}">{{ p.place }}</a>{% else %}{{ p.place }}{% endif %}</strong>{% if p.when %} · {{ p.when }}{% endif %}
      {% if p.note %}<br>{{ p.note | markdownify | remove: '<p>' | remove: '</p>' }}{% endif %}
      {% if p.photo %}
        <div class="col-sm-6 px-0 mt-2">
          {% assign photo_path = p.photo | prepend: 'assets/img/photos/' %}
          {% include figure.liquid path=photo_path class="img-fluid rounded z-depth-1" zoomable=true alt=p.place %}
        </div>
      {% endif %}
    </li>
  {% endfor %}
</ul>
{% endfor %}

{% endif %}
