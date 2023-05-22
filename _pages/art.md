---
layout: page
permalink: /art/
title: art
description: 
nav: true
nav_order: 7
display_categories: [poetry, digital art, photography]
---

<!-- pages/art.md -->
<div class="projects">
{%- if site.enable_project_categories and page.display_categories %}
  <!-- Display categorized projects -->
  {%- for category in page.display_categories %}
  <h2 class="category">{{ category }}</h2>
  {%- assign categorized_projects = site.art | where: "category", category -%}
  {%- assign sorted_projects = categorized_projects | sort: "importance" %}
  <!-- Generate cards for each project -->
  {% if page.card_link -%}
    {% if page.horizontal -%}
    <div class="container">
        <div class="row row-cols-2">
        {%- for project in sorted_projects -%}
        {% include projects_horizontal_card_link.html %}
        {%- endfor %}
        </div>
    </div>
    {%- else -%}
    <div class="grid">
        {%- for project in sorted_projects -%}
        {% include projects_card_link.html %}
        {%- endfor %}
    </div>
    {%- endif -%}
  {%- else -%}
    {% if page.horizontal -%}
    <div class="container">
        <div class="row row-cols-2">
        {%- for project in sorted_projects -%}
        {% include projects_horizontal.html %}
        {%- endfor %}
        </div>
    </div>
    {%- else -%}
    <div class="grid">
        {%- for project in sorted_projects -%}
        {% include projects.html %}
        {%- endfor %}
    </div>
    {%- endif -%}
  {%- endif -%}
  {% endfor %}

{%- else -%}
<!-- Display projects without categories -->
  {%- assign sorted_projects = site.art | sort: "importance" -%}
  <!-- Generate cards for each project -->

  {% if page.card_link -%}
    {% if page.horizontal -%}
    <div class="container">
        <div class="row row-cols-2">
        {%- for project in sorted_projects -%}
        {% include projects_horizontal_card_link.html %}
        {%- endfor %}
        </div>
    </div>
    {%- else -%}
    <div class="grid">
        {%- for project in sorted_projects -%}
        {% include projects_card_link.html %}
        {%- endfor %}
    </div>
    {%- endif -%}
  {%- else -%}
    {% if page.horizontal -%}
    <div class="container">
        <div class="row row-cols-2">
        {%- for project in sorted_projects -%}
        {% include projects_horizontal.html %}
        {%- endfor %}
        </div>
    </div>
    {%- else -%}
    <div class="grid">
        {%- for project in sorted_projects -%}
        {% include projects.html %}
        {%- endfor %}
    </div>
    {%- endif -%}
  {%- endif -%}
{%- endif -%}
</div>