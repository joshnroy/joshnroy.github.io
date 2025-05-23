# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is Josh Roy's personal portfolio website built with Jekyll and hosted on GitHub Pages at joshnroy.github.io. It uses the Minimal Mistakes theme (v4.26.2) for styling.

## Development Commands

```bash
# Install dependencies
bundle install

# Run local development server (default: http://localhost:4000)
bundle exec jekyll serve

# Build the static site
bundle exec jekyll build

# Update dependencies
bundle update
```

## Architecture

- **Static Site Generator**: Jekyll with GitHub Pages
- **Theme**: Minimal Mistakes (remote theme)
- **Main Content Files**:
  - `index.md` - Homepage content
  - `cv.md` - CV/resume page
  - `404.html` - Custom 404 error page
- **Configuration**: `_config.yml` contains site settings, author info, and theme configuration
- **Assets**: 
  - `/assets/images/` - Images (profile photo)
  - `/assets/css/main.scss` - Custom CSS overrides

## Key Configuration Notes

- The site uses `remote_theme` instead of local theme installation
- GitHub Pages gem is included for deployment compatibility
- Required plugins: `jekyll-feed`, `jekyll-include-cache`
- Changes to `_config.yml` require server restart to take effect

## Git Commit Guidelines

- Do not add Claude Code signatures or co-authorship to git commits
- Keep commit messages clean and focused on the changes made