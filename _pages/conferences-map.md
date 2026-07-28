---
layout: single
title: "Conference Map"
permalink: /conference-map/
---


<link rel="stylesheet"
href="https://unpkg.com/leaflet/dist/leafletight:700px;"></div>

<script srckg.com/leaflet/dist/leaflet.jsscript>

<script>

document.addEventListener("DOMContentLoaded", function() {

    var map = L.map('map').setView([25, 0], 2);

    L.tileLayer(
        'https://tile.openstreetmap.org/{z}/{x}/{y}.png',
        {
            attribution: '&copy; OpenStreetMap'
        }
    ).addTo(map);

    {% for conf in site.data.conferences %}

    L.marker([
        {{ conf.lat }},
        {{ conf.lon }}
    ])
    .addTo(map)
    .bindPopup(`
        <strong>{{ conf.conference }}</strong><br>
        {{ conf.year }}<br>
        {{ conf.city }}, {{ conf.country }}<br><br>

        <em>{{ conf.title }}</em><br>
        {{ conf.contribution }}

        {% if conf.url %}
        <br><a href="{{ conf.url }}" target="_blank">
        Conference website
        </a>
        {% endif %}

        {% if conf.slides %}
        <br><a href="{{ conf.slides }}" target="_blank">
        Slides
        </a>
        {% endif %}
    `);

    {% endfor %}

});

</script>





function markerColor(type){

    if(type === "Oral presentation")
        return "green";

    if(type === "Poster")
        return "blue";

    return "red";
}

