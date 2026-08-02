---
layout: page
title: projects
permalink: /projects/
description: Research and things I've built.
nav: true
nav_order: 1
---

<!--
  Category filter + masonry grid.

  Categories come from each project's `category:` front matter (a project may list
  several, comma-separated). The filter pills are generated from whatever values
  exist, so adding a new category to a project is all that's needed — nothing here
  has to change.

  Cards are laid out with CSS columns, so a project with a longer description gets
  a taller card instead of everything being forced to a uniform height.
-->

{% assign all_projects = site.projects | sort: "importance" %}

{% comment %} Build the unique, ordered list of categories across all projects. {% endcomment %}
{% assign category_list = "" %}
{% for project in all_projects %}
{% assign cats = project.category | split: "," %}
{% for c in cats %}
{% assign trimmed = c | strip %}
{% unless category_list contains trimmed %}
{% assign category_list = category_list | append: trimmed | append: "|" %}
{% endunless %}
{% endfor %}
{% endfor %}
{% assign categories = category_list | split: "|" %}

{% if categories.size > 1 %}

  <div class="nvg-filter" role="group" aria-label="Filter projects by category">
    <button type="button" class="nvg-filter-btn is-active" data-filter="all">All</button>
    {% for category in categories %}
      <button type="button" class="nvg-filter-btn" data-filter="{{ category | slugify }}">{{ category }}</button>
    {% endfor %}
  </div>
{% endif %}

{% comment %}
`.grid` / `.grid-item` are what al_folio_core's masonry.js looks for. It initialises
Masonry with `horizontalOrder: true`, which fills left-to-right in source order —
so the cards read in `importance` order across each row, while still sizing to their
own content. (Plain CSS columns fill top-to-bottom down each column instead, which
scrambles the reading order.)
{% endcomment %}

<div class="grid nvg-projects-grid">
  <div class="grid-sizer"></div>
  {% for project in all_projects %}
    {% assign cats = project.category | split: "," %}
    {% capture slugs %}
      {% for c in cats %}{{ c | strip | slugify }} {% endfor %}
    {% endcapture %}
    <div class="grid-item nvg-project-item" data-categories="{{ slugs | strip }}">
      {% include projects.liquid %}
    </div>
  {% endfor %}
</div>

<p class="nvg-filter-empty" hidden>No projects in that category yet.</p>

<script>
  (function () {
    var buttons = document.querySelectorAll(".nvg-filter-btn");
    var items = Array.prototype.slice.call(document.querySelectorAll(".nvg-project-item"));
    var empty = document.querySelector(".nvg-filter-empty");
    var grid = document.querySelector(".nvg-projects-grid");
    if (!buttons.length || !grid) return;

    // masonry.js (from al_folio_core) initialises the instance on DOMContentLoaded.
    // Grab it so filtering can hide items and re-lay-out, rather than fighting it.
    function instance() {
      return window.Masonry && typeof window.Masonry.data === "function" ? window.Masonry.data(grid) : null;
    }

    function apply(filter) {
      var msnry = instance();
      var shown = 0;
      items.forEach(function (item) {
        var cats = (item.getAttribute("data-categories") || "").split(/\s+/);
        var match = filter === "all" || cats.indexOf(filter) !== -1;
        item.style.display = match ? "" : "none";
        // `ignore` keeps Masonry from reserving space for a hidden card.
        if (msnry) {
          if (match) {
            msnry.unignore(item);
          } else {
            msnry.ignore(item);
          }
        }
        if (match) shown++;
      });
      if (empty) empty.hidden = shown !== 0;
      if (msnry) {
        msnry.reloadItems();
        msnry.layout();
      }
    }

    buttons.forEach(function (btn) {
      btn.addEventListener("click", function () {
        buttons.forEach(function (b) {
          b.classList.toggle("is-active", b === btn);
        });
        apply(btn.getAttribute("data-filter"));
      });
    });
  })();
</script>
