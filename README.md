# alessiochen.me

Personal portfolio site for Alessio Chen — AI Engineer & Full-Stack Developer.

Built with [Hugo](https://gohugo.io/) and the [hugo-profile](https://github.com/gurusabarish/hugo-profile) theme. Deployed to GitHub Pages at [alessiochen.me](https://alessiochen.me).

## Getting started

**Prerequisites:** Hugo extended v0.128.0+

```bash
# Clone with submodule
git clone --recurse-submodules https://github.com/AlessioChen/alessiochen.github.io.git

# Or if already cloned
git submodule init && git submodule update

# Serve locally
hugo server

# Build for production
hugo --minify
```

## Customization

All content (hero, projects, achievements, contact) is configured in `hugo.yaml` under `params`. No markdown content files are used.

Static assets go in `static/` — `cv.pdf` is served at `/cv.pdf`.

Layout overrides in `layouts/` take precedence over the theme without modifying the submodule.

## Deployment

Pushing to `main` triggers the GitHub Actions workflow (`.github/workflows/hugo.yml`), which builds and deploys to GitHub Pages automatically.
