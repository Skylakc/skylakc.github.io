# Skylake's Blog

Personal site of Eric Shang (Skylake) — PhD student at PolyU EEE, founder of PhotonJoy Technology Co., Ltd.

Built with [Hugo](https://gohugo.io/) and [Hugo Theme Stack](https://github.com/CaiJimmy/hugo-theme-stack) v4. Deployed automatically to GitHub Pages via GitHub Actions.

## Requirements

- **Hugo 0.170.1+** (the extended edition no longer exists; all features except LibSass are in the single binary)
- **Dart Sass 1.108+** — required by Stack v4
  - Windows: install the [Dart Sass standalone release](https://github.com/sass/dart-sass/releases) and add its folder to `PATH` (the npm `sass` shim does not work reliably with Hugo on Windows)
  - macOS/Linux: `npm install`
- Git submodules for the theme

## Local development

```bash
git submodule update --init --recursive
npm install          # installs Dart Sass for macOS/Linux
hugo server -D       # http://localhost:1313
```

Production build:

```bash
hugo --gc --minify
```

## Writing

Each post is a page bundle under `content/post/<Folder>/`, with two language versions sharing the same bundle resources:

```
content/post/MyPost/
├── index.md        # English
├── index.zh.md     # 简体中文
├── cover.jpg
└── ...
```

Front matter template:

```yaml
---
title: "Post title"
date: 2026-11-24
description: "One-line summary"
slug: my-post-slug
categories:
  - Motor
tags:
  - FOC
series:
  - Notes
image: cover.jpg
---
```

- `slug` keeps URLs stable even if the title changes.
- Use Markdown images (`![](photo.jpg)`), not raw `<img>` tags — Stack v4 generates responsive WebP/AVIF variants automatically.
- Put photos inside the post bundle.

## Deployment

Push to `main`. The workflow in `.github/workflows/deploy.yml` builds the site with Hugo and Dart Sass and publishes it to GitHub Pages. No build output is committed to the repository.

A snapshot of the pre-Actions deployment (built with Hugo 0.121.2) is preserved as the tag `archive/live-2024-01`.
