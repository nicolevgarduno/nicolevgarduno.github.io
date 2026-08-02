---
layout: project
title: Benign and Malicious PDF Detection
description: Turning PDFs into binary visualizations and training a CNN to tell malicious from benign.
img: assets/img/projects/pdf-detection.jpg
importance: 6
featured: false
category: Machine Learning, Cybersecurity
date: 2024-05-01
github: https://github.com/nicolevgarduno/Benign-and-Malicious-PDF-Detection
---

PDFs are a durable malware delivery vector because the format is large enough to hide things in — embedded JavaScript, malformed objects, obfuscated streams. Signature-based scanning catches what it already knows about; the interesting question is whether the _shape_ of a file gives it away.

This project treats the problem visually. Each PDF's raw bytes are rendered as a binary visualization, turning a file into an image, and a CNN is trained to classify those images as benign or malicious. Structural regularities — where entropy clusters, how sections are laid out — become visual texture the network can learn, without parsing the format or knowing anything about a specific exploit.

<div class="row justify-content-center mt-4">
  <div class="col-sm-10 mt-3 mt-md-0">
    {% include figure.liquid loading="eager" path="assets/img/projects/pdf-detection.jpg" title="Binary visualization of a PDF" class="img-fluid rounded z-depth-1" %}
  </div>
</div>
<div class="caption">
  A PDF rendered as a binary visualization — the input the CNN actually sees.
</div>

<div class="nvg-links">
  <a class="nvg-link-btn" href="https://github.com/nicolevgarduno/Benign-and-Malicious-PDF-Detection">
    <i class="fa-brands fa-github"></i>
    Code
  </a>
</div>
