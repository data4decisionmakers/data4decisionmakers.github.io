# AGENTS.md

This file provides guidance to AI agents when working with code in this repository.

## About Data for Decision Makers (D4DM)

D4DM is a data literacy initiative premised on a gap: data is abundant but unevenly usable. Availability is largely solved; **accessibility** (permission, format, skills, governance) and **judgement** (knowing when a number should not be trusted) are not. That gap is widest in the public and social sectors, where the stakes are highest and the capacity is thinnest — which is where the project aims its work.

The project's framing, used verbatim as the site's hero text on `index.qmd`:

> **Building a community of practice on data and its use for transformative change**
>
> We are a community of practitioners from diverse sectors, engaging in data of different shapes and sizes with varying skills, capacities, and tools. We support each other through grounded and practical short courses, open and accessible technical guidance, and impactful peer-to-peer learning.

**The full narrative lives in `about/index.qmd`** — read it before writing or editing any site copy. It is the source of truth for how the project describes itself; this section is only a summary.

Three voice conventions follow from it and apply across all pages:

- **Practitioner to practitioner**, not instructor to student.
- **Grounded in real decisions**, not technique in the abstract.
- **Open by default.**

Use British spellings (`visualisation`, `analyse`, `realised`) in prose.

## What this is

A [Quarto](https://quarto.org/) website for the Data for Decision Makers (D4DM) project, published at <https://d4dm.org>. The locally rendered HTML lives in `_site/`. The website is served via GitHub Pages from the `main` branch through a GitHub Actions workflow (.github/workflows/publish.yml).

## Key commands

**Preview locally** (live-reload dev server):

``` bash
quarto preview
```

**Full render** (builds all posts into `_site/`):

``` bash
quarto render
```

Either `quarto preview` or `quarto render` can be run to view the locally-generated website for previewing and checking changes/edits made to the website.

## Website structure

The website is intended to have the following pages:

* About (about/index.qmd) - About page that gives an overview of the Data 4 Decision Makers project and provides snippets of the other pages.

* Courses (courses/) - Courses page that gives an overview of the previous and upcoming courses of the project. Within this directory, course-specific pages within their own directory.

* Community (community/) - Community page that gives an overview of the Data 4 Decision Makers community and community activities.

* Resources (resources/) - Resources page that gives an overview of the various Data 4 Decision Makers project resources.

* Blog (posts/) - Blog page that gives an overview of previous and current blog posts. Within this directory, each blog post has its own sub-directory with the following format:

    * Posts live under `posts/<YYYY-MM-DD-slug>/`. Use `index.qmd`.

Minimal front matter:

``` yaml
---
title: "Post title"
subtitle: "Post sub-title"
description: "Post description"
author: "Post author"
date: "YYYY-MM-DD"
date-modified: last-modified
image: "images/image.png"
draft: false
categories:
  - tutorial
  - visualisation
---

```

- `image: images/image.png` (optional, relative to post directory) sets the listing thumbnail.

## Publishing

1.  `quarto render` or `quarto preview` to check website changes locally
2.  Commit source files and make a pull request to main. Should pass render test to allow merging to main.
3.  Merge to main to initiate GitHub Actions workflow to publish and render website via GitHub Pages.

## Repeatable workflows

Step-by-step procedures for common tasks live in `.agent/workflows/` as plain markdown — agent-agnostic and the single source of truth for each task:

- `.agent/workflows/new-post.md` — scaffold a new blog post under `posts/<YYYY-MM-DD-slug>/`.
- `.agent/workflows/new-course.md` — scaffold a new course page under `courses/<slug>/`.
- `.agent/workflows/publish-post.md` — flip a draft to published, verify the render, and open a PR to `main`.

Claude Code exposes these as slash commands (`/new-post`, `/new-course`, `/publish-post`) via thin adapters in `.claude/skills/` that just point back to these files. Other agents can read and follow the workflow files directly.

