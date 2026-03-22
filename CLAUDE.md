# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Commands

```bash
# Install submodule 
git submodule init 
git submodule update

# Serve locally with live reload
hugo server

# Build for production
hugo --minify

# Build with explicit base URL
hugo --minify --baseURL "https://alessiochen.me/"
```

Hugo version used in CI: **0.128.0 extended**. The theme requires the extended version (for Sass).

## Architecture

This is a single-page Hugo portfolio site deployed to GitHub Pages via `.github/workflows/hugo.yml` on every push to `main`. The live site is at `alessiochen.me`.

**Theme:** `themes/hugo-profile` is a git submodule (upstream: `gurusabarish/hugo-profile`). Do not edit files inside `themes/` — override them instead.

**All site content lives in `hugo.yaml`** — there are no markdown content files. The entire page (hero, projects, achievements, contact) is driven by `params` in this single config file.

**Layout overrides** in `layouts/` take precedence over the theme:
- `layouts/partials/sections/projects.html` — custom compact list layout (replaces the theme's card-grid)
- `layouts/partials/sections/achievements.html` — custom compact list layout with emoji support
- `layouts/partials/head/extensions.html` — injects global CSS tweaks (padding overrides, `.icon-hf` for HuggingFace SVG icons)

**Static assets** in `static/` are served at the root: `static/cv.pdf` → `/cv.pdf`, `static/images/` → `/images/`.

## Adding/editing content

**Projects** — add an entry to `params.projects.items` in `hugo.yaml`:
```yaml
- title: "Project Name"
  date: "Mon YYYY"
  content: "Description."
  badges:
    - "Tech1"
  links:
    - icon: fab fa-github
      url: https://github.com/AlessioChen/repo
    - icon: fas fa-external-link-alt
      url: https://live-url.com
```

**Achievements** — add an entry to `params.achievements.items`:
```yaml
- title: "Title"
  content: "Subtitle or detail"
  emoji: "🏆"
  url: https://optional-link.com   # omit if no link
```

## Deployment

Pushing to `main` triggers the GitHub Actions workflow which builds and deploys to GitHub Pages automatically. The `public/` directory is the build output — it is committed locally but the CI build regenerates it; no need to commit it manually.
