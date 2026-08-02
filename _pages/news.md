---
layout: page
title: news
permalink: /news/
description: Papers, roles, and the occasional award.
nav: true
nav_order: 3
---

<!--
  Media-list layout: headline + one-line description + date on the left, optional
  thumbnail on the right. Entries come from _news/*.md — add `thumbnail:` to an
  item's front matter to give it an image here.

  The compact one-line list on the home page is separate: that one is rendered by
  the gem's news.liquid include from the same files.
-->

<div class="nvg-news-list">
  {% assign news_items = site.news | sort: "date" | reverse %}
  {% for item in news_items %}
    <article class="nvg-news-entry">
      <div class="nvg-news-body">
        <h2 class="nvg-news-headline">
          <a href="{{ item.url | relative_url }}">{{ item.title | default: item.content | strip_html | truncate: 90 }}</a>
        </h2>
        {% if item.description %}
          <p class="nvg-news-desc">{{ item.description }}</p>
        {% endif %}
        <p class="nvg-news-date">{{ item.date | date: '%b %-d, %Y' }}</p>
      </div>

      {% if item.thumbnail %}
        {% comment %}
          Strip double quotes: figure.liquid interpolates alt into an attribute
          unescaped, so a title containing " breaks the <img> tag.
        {% endcomment %}
        {% assign thumb_alt = item.title | replace: '"', "" %}
        <a class="nvg-news-thumb" href="{{ item.url | relative_url }}">
          {% include figure.liquid path=item.thumbnail alt=thumb_alt class="img-fluid" %}
        </a>
      {% endif %}
    </article>

{% endfor %}

</div>

{% if site.news == blank %}

  <p class="text-muted">No news yet.</p>
{% endif %}
