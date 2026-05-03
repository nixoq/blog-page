# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Commands

All commands run from the `nico-blog/` directory:

```bash
# Install dependencies
bundle install

# Local dev server with live reload
bundle exec jekyll serve

# Build to _site/
bundle exec jekyll build

# Wipe build cache and rebuild
bundle exec jekyll clean && bundle exec jekyll build
```

## Architecture

Jekyll static site with two custom collections:

- **`_translations/`** — translated content, outputs to `/translations/{slug}/`
- **`_oshi_log/`** — fan activity logs, outputs to `/oshi-log/{slug}/`

Both collections use the `post` layout (`_layouts/post.html`), which wraps content with category, date, tags, and prev/next navigation. The base layout (`_layouts/default.html`) provides the hero header, nav, and footer.

**SCSS structure** (`_sass/`):
- `_variables.scss` — single source of truth for colors, fonts, and spacing
- `_base.scss` — reset, typography, utility classes
- `_header.scss` — hero and navigation
- `_home.scss` — welcome section and two-column latest-posts grid
- `_posts.scss` — individual post page

All SCSS is imported through `assets/css/main.scss`, which Jekyll compiles to `_site/assets/css/main.css`.

**New content** goes in `_translations/` or `_oshi_log/` as Markdown files named `YYYY-MM-DD-slug.md` with front matter:

```yaml
---
layout: post
title: "Post Title"
date: YYYY-MM-DD
category: translations   # or oshi-log
tags: [tag1, tag2]
---
```

## Design tokens

Deep navy background (`#0B0F16`), gold accents (`#c9a84c`), blue highlights (`#3DA6FF`). Display font: Cinzel Decorative; body: EB Garamond. Decorative symbols (`✦`, `♛`, corner ornaments) are used as flourishes — keep additions consistent with this aesthetic.
