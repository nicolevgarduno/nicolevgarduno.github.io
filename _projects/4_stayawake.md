---
layout: project
title: StayAwake
description: Real-time computer vision that detects lost focus from eye closure, yawning, and head orientation.
img: assets/img/projects/stayawake.jpg
importance: 4
featured: true
category: Computer Vision
github: https://github.com/nicolevgarduno/StayAwake
date: 2025-04-01
---

StayAwake watches for the physical signals that precede lost attention — sustained eye closure, yawning, and head orientation drifting away from the screen — and flags them in real time from a standard webcam feed.

The part that made it actually usable was per-user calibration. Baseline eye aperture, blink rate, and natural head position vary enough between people that a single fixed threshold produces constant false alarms for some users and silence for others. Calibrating against a short per-user baseline first, then measuring deviation from _that_, turned a noisy demo into something that could run in the background without being ignored.

<div class="row justify-content-center mt-4">
  <div class="col-sm-10 mt-3 mt-md-0">
    {%
      include video.liquid path="assets/video/stayawake-demo.mp4" class="img-fluid rounded z-depth-1"
      poster="assets/img/projects/stayawake.jpg" autoplay=true loop=true muted=true
    %}
  </div>
</div>
<div class="caption">
  Live detection firing as eyes close and a yawn is caught.
</div>

<div class="nvg-links">
  <a class="nvg-link-btn" href="https://github.com/nicolevgarduno/StayAwake">
    <i class="fa-brands fa-github"></i>
    Code
  </a>
</div>
