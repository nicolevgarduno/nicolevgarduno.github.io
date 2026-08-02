# CLAUDE.md

Guidance for coding agents working in this repo.

This is **Nicole Villavicencio-Garduño's personal site** — not the al-folio template. It was
created from al-folio v1.x, and the template's own docs, tests, Docker setup, and maintenance
CI have been removed. Do not reintroduce them.

## What this is

al-folio v1.x is a _thin starter_: layouts, includes, Sass, and feature JavaScript ship from
versioned `al_*` gems pinned in the `Gemfile`, not from this repo. This repo holds content,
configuration, and a small set of deliberate overrides.

## Local overrides — read before changing anything visual

These gem files are shadowed on purpose, to carry over the look of the previous
academicpages site. Everything else comes from the gems untouched.

| File                        | Purpose                                                                                                                                          |
| --------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------ |
| `_sass/_custom.scss`        | Palette and typography: text `#494e52`, links `#52adc8`, muted `#7a8288`, borders `#f2f3f3`, system sans, bold headings. Loaded last so it wins. |
| `assets/css/main.scss`      | Verbatim copy of the gem's file plus one trailing `@use "custom";`.                                                                              |
| `_layouts/about.liquid`     | Home page: left-sidebar profile (oval portrait, pronouns, bio, icon list) instead of the gem's right-floated photo.                              |
| `_layouts/cv.liquid`        | Fixes CV section order and gives Leadership the Experience renderer (date badges).                                                               |
| `_layouts/project.liquid`   | Project detail pages, with a "back to projects" link.                                                                                            |
| `_layouts/news_item.liquid` | News detail pages, with a "back to news" link.                                                                                                   |

On a gem upgrade, diff the forked layouts against the gem's versions in
`$(bundle show al_folio_core)/_layouts/`.

Prefer config and content over new overrides. Do **not** add a local Tailwind or CSS build
pipeline — compiled Tailwind ships from `al_folio_core`.

## Content map

| Area                            | Location                                            |
| ------------------------------- | --------------------------------------------------- |
| Home page / bio / sidebar       | `_pages/about.md`                                   |
| Projects (cards + detail pages) | `_projects/*.md`                                    |
| News                            | `_news/*.md`                                        |
| Photography gallery             | `_data/photography.yml` + `assets/img/photography/` |
| CV                              | `_data/cv.yml`, PDF in `assets/pdf/`                |
| External-link blog posts        | `_posts/` — see `_posts/README.md`                  |
| Social links                    | `_data/socials.yml`                                 |

## Build and verify

```bash
bundle exec jekyll build     # or `jekyll serve` for a live preview at :4000
npx prettier . --check
bundle exec al-folio upgrade audit
```

Three traps that produce confusing failures:

1. **A UTF-8 locale is required.** `al_folio_core` reads files with the default external
   encoding; under a `C`/POSIX locale the ñ in "Garduño" raises
   `invalid byte sequence in US-ASCII` and the build dies. Export
   `LANG=en_US.UTF-8 LC_ALL=en_US.UTF-8`.
2. **`_config.yml` is not hot-reloaded** by `jekyll serve`. Restart the server after editing it.
3. **`figure.liquid` interpolates `alt` unescaped**, so a title containing a double quote
   breaks the `<img>` tag. Strip quotes before passing it (see `_pages/news.md`).

In YAML content files, quote any list item containing a colon — otherwise it parses as a
mapping and renders as a raw hash. This has already caused one bug in `_data/cv.yml`.

## Deployment

`.github/workflows/deploy.yml` builds and force-pushes `_site` to the `gh-pages` branch on
push to `main`/`master`; GitHub Pages serves that branch. The root `CNAME`
(`nicolevgarduno.com`) must stay — the force-push would otherwise drop the custom domain.

The local branch is `main`; the GitHub default branch is `master`.

## Two files that are not in git

`MAINTAINING.md` (the owner's private how-to) and `.claude/settings.local.json` are
gitignored. Don't commit them or reference them from tracked files.
