# Josh Roy's Personal Website

Source for my personal academic site at [joshnroy.github.io](https://joshnroy.github.io), built with Jekyll and the [al-folio](https://github.com/alshedivat/al-folio) theme.

## Local development

Requires **Ruby 3.x or newer** and **ImageMagick**:

```bash
brew install ruby imagemagick      # if you don't already have them
bundle install                     # first run compiles native gems (a few minutes)
LANG=en_US.UTF-8 bundle exec jekyll serve
```

Then open <http://localhost:4000>. The `LANG=en_US.UTF-8` (any UTF-8 locale) is required — without it the build fails with `invalid byte sequence in US-ASCII`. Add `export LANG=en_US.UTF-8` to your shell profile so you don't have to type it each time.

> al-folio is a **gem-based** theme: its layouts, includes, and styles live in the `al_folio_*` gems (see `Gemfile`), not in this repo. This repo only contains content, config, and media.

## Editing content (all Markdown / YAML)

| What | Where |
| --- | --- |
| Bio + Awards (homepage) | `_pages/about.md` |
| Publications | `_bibliography/papers.bib` (one BibTeX entry per paper; `selected={true}` features it on the homepage) |
| News items | `_news/*.md` (one short file per item) |
| Social links + CV path | `_data/socials.yml` |
| CV PDF | `assets/pdf/Josh_Roy_CV.pdf` |
| Profile photo | `assets/img/prof_pic.jpg` |
| Blog link (→ Medium) | `_pages/blog.md` |
| Site settings (title, URL, analytics, scholar name) | `_config.yml` (restart `jekyll serve` after changing) |

### Add a publication

Append an entry to `_bibliography/papers.bib`, e.g.:

```bibtex
@inproceedings{yourkey2026,
  abbr={NeurIPS},
  title={Your Paper Title},
  author={Roy, Josh and Coauthor, Jane},
  booktitle={Advances in Neural Information Processing Systems (NeurIPS)},
  year={2026},
  arxiv={2601.01234},
  abstract={One-paragraph summary.},
  selected={true}
}
```

### Add a news item

Create `_news/2026-12-01-something.md`:

```markdown
---
layout: post
date: 2026-12-01 09:00:00-0400
inline: true
related_posts: false
---

Short announcement with a [link](https://example.com).
```

## Deployment

Pushing to `master` triggers `.github/workflows/deploy.yml`, which builds the site and publishes it to the **`gh-pages`** branch via GitHub Actions.

**One-time setup:** in the repo's **Settings → Pages**, set the source to the `gh-pages` branch. (Unlike the previous Minimal Mistakes setup, GitHub Pages no longer builds directly from `master`.)
