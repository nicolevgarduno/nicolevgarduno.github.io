---
layout: about
title: about
headline: Hello, world! My name is Nicole.
permalink: /

profile:
  image: prof_pic.jpg
  image_alt: Nicole Villavicencio-Garduño
  pronouns: she/her
  bio: Post-master's researcher working on adversarial AI and machine learning.
  location: Los Alamos, NM
  employer: Los Alamos National Laboratory
  employer_url: https://www.lanl.gov/

selected_papers: false # includes a list of papers marked as "selected={true}"
social: false # social links live in the sidebar instead (see _layouts/about.liquid)

announcements:
  enabled: true # includes a list of news items
  scrollable: false # adds a vertical scroll bar if there are more than 3 news items
  limit: 4 # leave blank to include all the news in the `_news` folder

latest_posts:
  enabled: false
  scrollable: true # adds a vertical scroll bar if there are more than 3 new posts items
  limit: 3 # leave blank to include all the blog posts
---

🔬 I work on adversarial AI and machine learning at Los Alamos National Laboratory.

💻 My research sits at the intersection of computer vision and the physical world — mostly how object detection models can be made to fail.

🎓 M.S. in Information Security, AI Engineering focus, Carnegie Mellon — Rales Fellow.

🎞️ In my free time, I love taking and developing film.

## About me

Hi! I'm a post-master's researcher at LANL's Advanced Research for Cyber Systems group where I work on adversarial AI and machine learning — mostly at the intersection of computer vision and the physical world.

I earned my M.S. in Information Security with a focus in AI Engineering at Carnegie Mellon as a [Rales Fellow](https://www.cmu.edu/graduate/rales-fellows), and studied Applied Computer Science at Birmingham-Southern College. I'm interested in how AI systems fail in the physical world, and what that means for building ones that are actually trustworthy under adversarial conditions.

Outside of trying to break things, I am incredibly interested in supporting first-generation minorities in STEM. I am the Vice President of Operations for the [NM Society of Hispanic Professional Engineers](https://shpenewmexico.org/) Chapter and a co-lead for the CMU Rales Alumni Network.

Always happy to connect with people working in adversarial ML, computer vision, mentorship, and inclusivity in STEM fields.

## Selected projects

A few things I've built and broken. [See all &rarr;]({{ '/projects/' | relative_url }})

<div class="projects">
  <div class="row row-cols-1 row-cols-md-3">
    {% assign featured_projects = site.projects | where: "featured", true | sort: "importance" %}
    {% for project in featured_projects %}
      {% include projects.liquid %}
    {% endfor %}
  </div>
</div>
