# Posts

Posts on this site are **pointers to writing published elsewhere** (Medium, Substack),
not full articles. A post here is a title + one-line teaser that links straight out to
the original. This directory is meant to stay empty until you actually publish something.

There are two ways to add one.

## 1. One at a time (manual)

Create `_posts/YYYY-MM-DD-some-slug.md`:

```markdown
---
layout: post
title: The title of the piece
date: 2026-08-14 10:00:00
description: One line describing what it's about — this shows under the title.
external_source: Medium
redirect: https://medium.com/@your-handle/the-actual-post
---
```

The body can be empty. `redirect:` is what makes the listing link out instead of opening a
page on this site, and it renders with a small external-link arrow next to the title.
`external_source:` is the label shown in the post metadata line.

## 2. Automatically, from an RSS feed

Uncomment a block under `external_sources:` in `_config.yml` and point it at your feed:

```yaml
external_sources:
  - name: Medium
    rss_url: https://medium.com/@your-handle/feed
    categories: [external-posts]
    tags: [medium]
```

Every post in that feed then appears on `/blog/` automatically, linking to the original.
No files needed in this directory.

> Note: the RSS route pulls the feed at **build time**, so new pieces show up on the next
> deploy rather than the moment you publish. Since `deploy.yml` runs on push, that means
> pushing a commit (or triggering the workflow manually) after you publish.

This file is excluded from the build via `exclude:` in `_config.yml`.
