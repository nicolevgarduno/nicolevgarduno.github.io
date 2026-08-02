---
layout: project
title: Waste Detection Drone
description: Real-time trash detection from a DJI Tello using YOLOv5.
img: assets/img/projects/waste-detection-drone.gif
importance: 7
featured: false
category: Computer Vision
github: https://github.com/melvinczyk/Waste-detection-drone
date: 2024-05-01
---

A YOLOv5 model running against the live video feed from a DJI Tello, detecting litter from the air in real time. The constraint that shaped the project was the platform: the Tello is a small consumer drone with a low-resolution camera, limited flight time, and no onboard compute worth speaking of, so inference happens off-board against a streamed feed.

That splits the problem in two — keeping detection accurate on small, motion-blurred objects viewed from above, and keeping the stream-and-inference loop tight enough that results still mean something by the time they arrive. A collaborator project.

<div class="row justify-content-center mt-4">
  <div class="col-sm-10 mt-3 mt-md-0">
    {% include figure.liquid loading="eager" path="assets/img/projects/waste-detection-drone.gif" title="Aerial waste detection" class="img-fluid rounded z-depth-1" %}
  </div>
</div>
<div class="caption">
  Live detection from the drone's camera feed.
</div>

<div class="nvg-links">
  <a class="nvg-link-btn" href="https://github.com/melvinczyk/Waste-detection-drone">
    <i class="fa-brands fa-github"></i>
    Code
  </a>
</div>
