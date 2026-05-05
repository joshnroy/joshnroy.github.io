# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Josh Roy's personal portfolio site. Jekyll + GitHub Pages, deployed automatically from `master` to https://joshnroy.github.io. Uses the Minimal Mistakes theme (v4.26.2) via `remote_theme` — the theme is not vendored, so layouts/includes/SCSS partials are pulled from `mmistakes/minimal-mistakes` at build time and aren't browseable in this repo.

## Development Commands

```bash
bundle install                  # install dependencies
bundle exec jekyll serve        # local server at http://localhost:4000 (auto-rebuilds on file change)
bundle exec jekyll build        # one-shot build into _site/
bundle update github-pages      # update to track GitHub Pages' current gem versions
```

`_config.yml` changes are NOT picked up by `jekyll serve`'s auto-reload — restart the server.

## Architecture

- **Top-level pages** (rendered from root): `index.md` (homepage bio + publications), `papers.md` (annotated bibliography index), `blog.md` (meta-refresh redirect to medium.com/@thosehippos — there is no on-site blog), `404.html`. There is no `cv.md`; the CV is the static `Josh_Roy_CV.pdf` at the root, linked from `_config.yml`'s `author.links`.
- **Papers collection**: `_papers/*.md` is a Jekyll collection (configured in `_config.yml` under `collections.papers`) with permalink `/papers/:slug/`. `papers.md` iterates `site.papers` and renders each entry's frontmatter. To add a paper annotation, create a new file in `_papers/` matching the existing frontmatter shape (`title`, `authors`, `venue`, `paper_date`, `date`, `paper_url`, `categories`, `tags`, `excerpt`) — the homepage and `papers.md` will not auto-update; the publications list on `index.md` is hand-maintained separately.
- **Author profile sidebar** (avatar, location, social links) lives in `_config.yml` under `author:`, not in any page's frontmatter. Pages opt in via `author_profile: true`.
- **Styling**: `assets/css/main.scss` is the only custom stylesheet; theme styles are imported by Minimal Mistakes' default skin. No custom layouts or includes — all layouts come from the remote theme.
- **Analytics**: GA4 tracking ID `G-FSLWBL641C` is wired in via `_config.yml`'s `analytics` block (the theme reads it).

## Git Commit Guidelines

- Do not add Claude Code signatures or co-authorship to git commits.
- Keep commit messages clean and focused on the changes made.
