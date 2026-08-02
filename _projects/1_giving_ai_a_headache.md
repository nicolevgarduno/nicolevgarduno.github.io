---
layout: project
title: Giving AI a Headache
description: An acoustic attack that degrades YOLO11 object detection by physically resonating the camera itself.
img: assets/img/projects/giving-ai-a-headache.jpg
importance: 1
featured: true
category: Adversarial ML, Computer Vision
github: https://github.com/nicolevgarduno/Giving-AI-a-Headache
arxiv: https://arxiv.org/abs/2606.14658
---

Most adversarial attacks on object detection work in the digital domain; perturb the pixels, fool the model. But we studied how sound can be used to physically resonate a device, and that motion falls outside what the camera's internal stabilization system was built to correct. The stabilizer compensates anyway, and in doing so writes artifacts into the frame. Downstream, YOLO11 misclassifies objects, misses targets, and hallucinates ones that were never there.

Earlier work in this space used ultrasonic frequencies above 20 kHz, which attenuate quickly and confine the attack to short range. We looked at frequencies in the audible band below 20 kHz and ran physical experiments against an off-the-shelf camera and an unmodified detection model, then looked at which image and object features actually drive the vulnerability.

The failure is introduced upstream of everything a conventional defense inspects.

First-authored, published at SPIE 2026, with Maksim Ekin Eren, Milo Prisbrey, Ben Migliori, and Michael Teti.

<div class="row justify-content-center mt-4">
  <div class="col-sm-10 mt-3 mt-md-0">
    {% include figure.liquid loading="eager" path="assets/img/projects/headache-methodology.jpg" title="Methodology overview" class="img-fluid rounded z-depth-1" %}
  </div>
</div>
<div class="caption">
  Methodology overview.
</div>

<div class="row justify-content-center mt-4">
  <div class="col-sm-10 mt-3 mt-md-0">
    {% include figure.liquid path="assets/img/projects/giving-ai-a-headache.jpg" title="Detection degradation under acoustic load" class="img-fluid rounded z-depth-1" %}
  </div>
</div>
<div class="caption">
  Detection degrading as the camera is driven at a resonant frequency.
</div>

<div class="nvg-links">
  <a class="nvg-link-btn" href="https://arxiv.org/abs/2606.14658">
    <i class="fa-solid fa-file-lines"></i>
    arXiv
  </a>
  <a class="nvg-link-btn" href="https://github.com/nicolevgarduno/Giving-AI-a-Headache">
    <i class="fa-brands fa-github"></i>
    Code
  </a>
</div>

## Citation

Villavicencio-Garduño, N., Eren, M. E., Prisbrey, M., Migliori, B., & Teti, M. (2026).
_Giving AI a Headache: Acoustic Adversarial Attacks to Computer Vision Applications._ SPIE.

### BibTeX

```bibtex
@inproceedings{villavicencio2026headache,
  title     = {Giving AI a Headache: Acoustic Adversarial Attacks to Computer Vision Applications},
  author    = {Villavicencio-Gardu{\~n}o, Nicole and Eren, Maksim Ekin and Prisbrey, Milo and Migliori, Ben and Teti, Michael},
  booktitle = {SPIE},
  year      = {2026},
  eprint    = {2606.14658},
  archivePrefix = {arXiv}
}
```
