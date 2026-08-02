---
layout: project
title: FIFA Player Value Prediction
description: Comparing four ML approaches for predicting player market value from skill attributes.
img: assets/img/projects/fifa-player-value.jpg
importance: 5
featured: false
category: Machine Learning
github: https://github.com/nicolevgarduno/FIFA-Scouting-Report
date: 2024-08-01
---

A comparison study: how well can a player's market value be predicted from their recorded skill attributes, and does model complexity actually buy accuracy on a problem like this one?

Four approaches were evaluated against the same dataset — linear regression as a baseline, random forest, a multilayer perceptron, and a CNN. The framing question is whether the added capacity of the neural approaches pays off on structured tabular attributes, or whether a well-specified tree ensemble is the more honest answer for this shape of data.

This page is a summary of the write-up rather than a runnable notebook.

<div class="row justify-content-center mt-4">
  <div class="col-sm-10 mt-3 mt-md-0">
    {% include figure.liquid loading="eager" path="assets/img/projects/fifa-player-value.jpg" title="World Cup match" class="img-fluid rounded z-depth-1" %}
  </div>
</div>
<div class="caption">
  Player value is the thing being predicted from recorded skill attributes.
  Photo via <a href="https://www.bostonherald.com/2026/07/01/down-to-10-players-u-s-wins-2-0-to-advance-in-the-world-cup/">Boston Herald</a>.
</div>

<div class="nvg-links">
  <a class="nvg-link-btn" href="https://github.com/nicolevgarduno/FIFA-Scouting-Report">
    <i class="fa-brands fa-github"></i>
    Write-up
  </a>
</div>
