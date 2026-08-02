---
layout: project
title: GoNoGo
description: A quality-gated CI/CD pipeline spanning three Terraform-provisioned GKE clusters.
img: assets/img/projects/gonogo.jpg
importance: 3
featured: true
category: Infrastructure
github: https://github.com/nicolevgarduno/GoNoGo
date: 2025-05-01
---

GoNoGo is a CI/CD pipeline built around a simple idea: a build should not be allowed to proceed on green tests alone. Jenkins orchestrates the pipeline, SonarQube enforces static-analysis quality gates, and a Hadoop MapReduce job runs as a downstream workload — with the whole thing deployed across three separate GKE clusters provisioned from Terraform.

Splitting the orchestration, analysis, and compute planes across distinct clusters made the infrastructure boundaries explicit rather than incidental. Terraform kept the three environments reproducible, so tearing the whole system down and standing it back up was a routine operation instead of an event.

<div class="row justify-content-center mt-4">
  <div class="col-sm-10 mt-3 mt-md-0">
    {% include figure.liquid loading="eager" path="assets/img/projects/gonogo.jpg" title="GoNoGo pipeline architecture" class="img-fluid rounded z-depth-1" %}
  </div>
</div>
<div class="caption">
  Pipeline architecture: orchestration, analysis, and compute planes on separate GKE clusters.
</div>

<div class="nvg-links">
  <a class="nvg-link-btn" href="https://github.com/nicolevgarduno/GoNoGo">
    <i class="fa-brands fa-github"></i>
    Write-Up
  </a>
</div>
