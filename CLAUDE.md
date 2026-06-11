# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Josh Roy's personal academic site. Jekyll + the [al-folio](https://github.com/alshedivat/al-folio) theme, deployed to https://joshnroy.github.io. al-folio is **gem-based**: the theme runtime (`theme: al_folio_core` in `_config.yml`) plus a family of `al_*`/`al_folio_*` gems ship the layouts, includes, SCSS/Tailwind, and Liquid plugins (see `Gemfile`). None of that is vendored in this repo — this repo holds only configuration, content, and media. To inspect a theme layout/include, look under `vendor/bundle/ruby/*/gems/al_folio_core-*/`.

## Development Commands

Requires **Ruby 3.x+** (e.g. `brew install ruby`) and **ImageMagick** (`brew install imagemagick`, used to generate responsive images). The system Ruby (2.6) is too old.

```bash
bundle install                                   # install theme gems (first run compiles native extensions)
LANG=en_US.UTF-8 bundle exec jekyll serve        # local server at http://localhost:4000 (auto-rebuilds)
LANG=en_US.UTF-8 bundle exec jekyll build        # one-shot build into _site/
```

`LANG`/`LC_ALL` **must** be a UTF-8 locale, or the build dies with `invalid byte sequence in US-ASCII` when al-folio scans the UTF-8 Markdown. Set it in your shell profile to avoid prefixing every command. `_config.yml` changes are not picked up by `jekyll serve`'s auto-reload — restart the server. Node is **not** needed for local development (the CI-only purgecss optimization is the only thing that uses it).

## Architecture

Everything a human edits is Markdown/YAML:

- **Homepage / bio**: `_pages/about.md` (`layout: about`, `permalink: /`). Body holds the bio and the **Awards** section. Frontmatter controls the profile photo (`profile.image`), the under-photo `more_info`, and the toggles for selected papers, social icons, and the news list.
- **Publications**: `_bibliography/papers.bib` — a single BibTeX file; jekyll-scholar renders `_pages/publications.md` automatically and the `selected={true}` entries on the homepage. Add a paper by appending a BibTeX entry. Useful fields: `abbr` (venue badge), `abstract`, `selected`, `award`/`award_name`, `arxiv`/`pdf`/`url`. Author names matching `scholar.last_name`/`first_name` in `_config.yml` are auto-bolded.
- **News**: one Markdown file per item in `_news/` (`layout: post`, `inline: true`). They render on the homepage and `/news/`, newest first.
- **CV**: the PDF lives at `assets/pdf/Josh_Roy_CV.pdf`. `_pages/cv.md` embeds it and offers a download link. The CV is reachable only via the navbar page — intentionally not in the social icon rows. (The al-folio structured-CV renderer is intentionally not used.)
- **Blog**: `_pages/blog.html` is a bare page that instantly redirects (meta refresh 0 + JS) to https://medium.com/@thosehippos — there is no on-site blog. All blog links (navbar, bio) point at `/blog/` so they behave identically; don't link Medium directly.
- **Social links**: `_data/socials.yml` (email, Google Scholar, LinkedIn, GitHub, X). Note: the jekyll-socials plugin renders every key present regardless of value — to hide an icon, delete its line.
- **Site-wide settings**: `_config.yml` — identity (`first_name`/`last_name`), `url`/`baseurl` (root site, so `baseurl: ""`), `scholar` author names, `analytics.google` (GA4 `G-FSLWBL641C`), and the theme/plugin wiring. Leave the `al_folio`, `scholar`, `sass`, and `plugins` blocks alone unless you know what they do.
- **Nav order**: each page's `nav_order` frontmatter sets navbar position (publications → cv → blog).

## Deployment

Deploys via **GitHub Actions**, not GitHub Pages' built-in build. `.github/workflows/deploy.yml` builds the site on push to `master` and publishes `_site/` to the **`gh-pages`** branch. One-time setup: in the repo **Settings → Pages**, set the source to the `gh-pages` branch. (This differs from the old Minimal Mistakes setup, which built directly from `master`.)

## Git Commit Guidelines

- Do not add Claude Code signatures or co-authorship to git commits.
- Keep commit messages clean and focused on the changes made.
