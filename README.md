# Josh Roy's Personal Portfolio

This is the source code for my personal portfolio website, built with Jekyll and hosted on GitHub Pages at [joshnroy.github.io](https://joshnroy.github.io).

## 🚀 Quick Start

### Prerequisites

- Ruby (version 2.5 or higher)
- Bundler gem (`gem install bundler`)

### Local Development

1. Clone the repository:
   ```bash
   git clone https://github.com/joshnroy/joshnroy.github.io.git
   cd joshnroy.github.io
   ```

2. Install dependencies:
   ```bash
   bundle install
   ```

3. Run the development server:
   ```bash
   bundle exec jekyll serve
   ```

4. Open your browser and navigate to `http://localhost:4000`

## 📁 Repository Organization

```
joshnroy.github.io/
├── _config.yml          # Jekyll configuration and site metadata
├── index.md             # Homepage content
├── cv.md                # CV/Resume page
├── 404.html             # Custom 404 error page
├── assets/              # Static assets
│   ├── css/            # Custom styles
│   └── images/         # Images (profile photo, etc.)
├── Gemfile             # Ruby dependencies
└── Gemfile.lock        # Locked dependency versions
```

## 🎨 Theme

This site uses the [Minimal Mistakes](https://mmistakes.github.io/minimal-mistakes/) Jekyll theme (v4.26.2) via remote theme functionality.

## ✏️ Making Changes

### Updating Content

- **Homepage**: Edit `index.md`
- **CV/Resume**: Edit `cv.md`
- **Site settings**: Edit `_config.yml` (requires server restart)
- **Profile photo**: Replace `/assets/images/profile.jpeg`

### Adding New Pages

1. Create a new `.md` file in the root directory
2. Add front matter at the top:
   ```yaml
   ---
   layout: single
   title: "Your Page Title"
   permalink: /your-page-url/
   ---
   ```
3. Add your content below in Markdown format

### Styling

Custom CSS can be added to `/assets/css/main.scss`. The theme's default styles will be automatically included.

## 🚢 Deployment

The site automatically deploys to GitHub Pages when changes are pushed to the `master` branch. No manual deployment steps are required.

## 📝 Notes

- Changes to `_config.yml` require restarting the Jekyll server
- The site is configured for the custom domain joshnroy.github.io
- GitHub Pages handles the Jekyll build process automatically