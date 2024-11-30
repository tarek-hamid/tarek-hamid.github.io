---
layout: page
title: research
permalink: /research/
nav: true
nav_order: 3
display_categories: [PhD]
horizontal: false
---

<div class="row">
  <div class="col-md-9">
    <p>
      The primary focus of my research at the Watson Research Lab focuses on <a href="https://dl.acm.org/doi/10.1145/3569502">Lumos</a>, a multi-wavelength wearable optical sensor that covers wavelengths spanning the entirety of the visible spectrum, as well as some of the NIR and IR spectrums. We are using this sensor to develop new applications in wearable health monitoring such as non-invasive glucose, blood pressure, macronutrient, lactate, and cosmetic monitoring.
      <br>
      <br>
      Below are projects that I worked on using this sensor across these various applications; more will be added as patents/papers are published.
    </p>
  </div>
  <div class="col-md-3">
    <img src="{{ site.baseurl }}/assets/img/lumos.png" alt="Lumos Sensor" class="img-fluid">
  </div>
</div>


<!-- pages/projects.md -->
<div class="projects">
{% if site.enable_project_categories and page.display_categories %}
  <!-- Display categorized projects -->
  {% for category in page.display_categories %}
  <a id="{{ category }}" href=".#{{ category }}">
    <h2 class="category">{{ category }}</h2>
  </a>
  {% assign categorized_projects = site.projects | where: "category", category %}
  {% assign sorted_projects = categorized_projects | sort: "importance" %}
  <!-- Generate cards for each project -->
  {% if page.horizontal %}
  <div class="container">
    <div class="row row-cols-1 row-cols-md-2">
    {% for project in sorted_projects %}
      {% include projects_horizontal.liquid %}
    {% endfor %}
    </div>
  </div>
  {% else %}
  <div class="row row-cols-1 row-cols-md-3">
    {% for project in sorted_projects %}
      {% include projects.liquid %}
    {% endfor %}
  </div>
  {% endif %}
  {% endfor %}

{% else %}

<!-- Display projects without categories -->

{% assign sorted_projects = site.projects | sort: "importance" %}

  <!-- Generate cards for each project -->

{% if page.horizontal %}

  <div class="container">
    <div class="row row-cols-1 row-cols-md-2">
    {% for project in sorted_projects %}
      {% include projects_horizontal.liquid %}
    {% endfor %}
    </div>
  </div>
  {% else %}
  <div class="row row-cols-1 row-cols-md-3">
    {% for project in sorted_projects %}
      {% include projects.liquid %}
    {% endfor %}
  </div>
  {% endif %}
{% endif %}
</div>