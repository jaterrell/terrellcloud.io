# terrellcloud.io

GitHub Pages source for [terrellcloud.io](https://terrellcloud.io) — the
site and blog of TerrellCloud.io, a Cloud & AI Systems consultancy
established in 2021.

Built with [Jekyll](https://jekyllrb.com/) using the `minima` theme and the
`github-pages` gem, so GitHub Pages builds it natively — no CI workflow
required.

## Local preview

```sh
bundle install
bundle exec jekyll serve
```

Then open <http://localhost:4000>. The `github-pages` gem pins Jekyll and
plugin versions to match production GitHub Pages.

## Adding a post

Create a Markdown file in `_posts/` named `YYYY-MM-DD-your-slug.md` with
front matter:

```yaml
---
layout: post
title: "Post title"
date: YYYY-MM-DD HH:MM:SS -0500
categories: [cloud]            # e.g. cloud, generative-ai, announcements
tags: [cloud, architecture]
---
```

Posts are published at `/blog/:year/:month/:slug/` and listed on
[/blog/](https://terrellcloud.io/blog/) (paginated, 10 per page) and in the
RSS feed at `/feed.xml`.

## Site structure

- `_config.yml` — site settings, theme, plugins, navigation
- `index.md` — homepage
- `blog/index.html` — blog listing page
- `about.md` — about page
- `_posts/` — blog posts
- `CNAME` — custom domain (do not remove)

## Deployment

GitHub Pages builds and deploys automatically on push. One-time setup:
in the repository **Settings → Pages**, set **Source** to "Deploy from a
branch" and select the `main` branch (root folder).
