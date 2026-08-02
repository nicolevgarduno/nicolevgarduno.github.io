---
layout: page
title: photography
permalink: /photography/
description: Away from the keyboard.
nav: true
nav_order: 2
images:
  lightbox2: true
---

<!--
  Add photos by dropping files into assets/img/photography/ and adding an entry
  to _data/photography.yml. Each entry needs a `path`; `alt` is optional but good
  for accessibility, and `caption` is optional (shown in the lightbox only).

  The grid is masonry (uneven heights) and clicking a photo opens it full-size.
  Captions are deliberately not shown under the thumbnails — this page is meant
  to read quieter than the project pages.
-->

{% if site.data.photography and site.data.photography.size > 0 %}

  <div class="photo-gallery">
    {% for photo in site.data.photography %}
      <a href="{{ photo.path | relative_url }}" data-lightbox="photography" {% if photo.caption %}data-title="{{ photo.caption }}"{% endif %}>
        {% include figure.liquid path=photo.path alt=photo.alt class="img-fluid rounded" %}
      </a>
    {% endfor %}
  </div>

{% else %}

<p class="text-muted mt-4">
  Nothing here yet. Add images to <code>assets/img/photography/</code> and list them in
  <code>_data/photography.yml</code>.
</p>

{% endif %}

<style>
  .photo-gallery {
    column-count: 3;
    column-gap: 1rem;
    margin-top: 2rem;
  }
  .photo-gallery > a {
    display: block;
    break-inside: avoid;
    margin-bottom: 1rem;
    line-height: 0;
  }
  .photo-gallery img {
    width: 100%;
    height: auto;
    transition: opacity 0.2s ease;
  }
  .photo-gallery > a:hover img {
    opacity: 0.85;
  }
  @media (max-width: 768px) {
    .photo-gallery {
      column-count: 2;
    }
  }
  @media (max-width: 480px) {
    .photo-gallery {
      column-count: 1;
    }
  }
</style>
