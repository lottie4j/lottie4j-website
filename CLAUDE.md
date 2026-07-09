# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

The marketing/docs website for [Lottie4J](https://github.com/lottie4j/lottie4j) (a Java/JavaFX Lottie animation library), built with Hugo and the `hugo-theme-relearn` theme. Deployed to `lottie4j.com` via GitHub Pages. This repo is content and theme overrides only — no application code, no test suite, no package manager.

### New Release

When a new release gets added, make sure to:

* Add the release to `content/releases/` similar to the existing entries, with a link to the GitHub compare view for that version range.
* Update the version/date callout on the homepage (`content/_index.md`, in the `l4j-hero-release` line and the Maven/Gradle snippets in the Quick start section).
* Add a blog post under `content/status/<year>/` if there are any noteworthy changes to highlight.

## Commands

Requires the Hugo **extended** binary (pinned to `0.163.3` in CI, see `.github/workflows/hugo.yml`) and Dart Sass.

```bash
hugo server                 # local dev server with live reload
hugo --quiet --gc           # production build, output to ./public (mirrors CI)
hugo --minify --destination /tmp/l4j_build --baseURL "https://lottie4j.com/"   # exact CI build
```

There are no lint or test commands — verification is: run a build and confirm it completes without warnings/errors, then check the rendered page in a browser or via `curl` against `hugo server`.

Deployment is automatic: pushes to `main` trigger `.github/workflows/hugo.yml`, which builds with Hugo + Dart Sass and deploys `./public` to GitHub Pages.

## Architecture

- **`themes/hugo-theme-relearn/`** is vendored in full (not a git submodule, despite `submodules: recursive` in the CI checkout step — that's a no-op leftover from the workflow template). Never edit files under here for site-specific behavior; override them instead.
- **Project overrides live in `layouts/`**, mirrored at the same path as the theme file they replace (e.g. `layouts/partials/title.gotmpl` overrides `themes/hugo-theme-relearn/layouts/partials/title.gotmpl`, `layouts/partials/custom-header.html` and `layouts/partials/menu-footer.html` similarly). Hugo resolves project `layouts/` before theme `layouts/` automatically — this is the only mechanism used to customize theme behavior. Each override file's header comment states exactly what it changes vs. the theme default; keep that comment accurate when editing.
- **Content front matter is TOML** (`+++ ... +++`) for structural/section pages (e.g. `content/_index.md`, `content/releases.md`) but **YAML** (`--- ... ---`) for dated status posts under `content/status/<year>/`. Match whichever convention the surrounding files in that directory use.
- **`content/status/<year>/*.md`** are dated dev-log/blog posts (filename often `YYYYMMDD` or `YYYYMMDD-slug`). `content/status/_index.md` lists children by weight/date. The homepage (`content/_index.md`) pulls the latest N of these via the custom shortcode `layouts/shortcodes/latest-status.html` (`{{< latest-status 4 >}}`), which queries `site.RegularPages "Section" "status"` sorted by date — no manual list to maintain when adding a post.
- **`content/releases.md`** is a single flat changelog page, one `## YYYY-MM-DD, x.y.z` section per release, newest first, each linking to the GitHub compare view for that version range. When adding a release, also update the version/date callout on the homepage (`content/_index.md`, in the `l4j-hero-release` line and the Maven/Gradle snippets in the Quick start section).
- **Static assets** (`static/css/`, `static/js/`, `static/img/`, `static/favicon/`) are served as-is at the site root. `static/css/custom.css` / `static/js/custom.js` are auto-loaded by the theme override in `layouts/partials/custom-header.html` if present.
- SEO/meta concerns (canonical URL, JSON-LD structured data, social share image) are centralized in `layouts/partials/custom-header.html` — extend there rather than per-page.
