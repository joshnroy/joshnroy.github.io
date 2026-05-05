source "https://rubygems.org"

# Run with: bundle exec jekyll serve
#
# Note: GitHub Pages builds this site with its own pinned gem set on the server,
# regardless of what's in this Gemfile. We previously used the `github-pages`
# meta-gem to mirror those pins locally, but it dragged in transitive deps with
# unpatched CVEs. This Gemfile pins modern jekyll directly for local dev; the
# deployed site is unaffected.

gem "jekyll", "~> 3.10"
gem "minimal-mistakes-jekyll", "~> 4.26"
gem "kramdown-parser-gfm", "~> 1.1"

group :jekyll_plugins do
  gem "jekyll-feed", "~> 0.17"
  gem "jekyll-include-cache", "~> 0.2"
  gem "jekyll-remote-theme", "~> 0.4"
  gem "jekyll-seo-tag", "~> 2.8"
  gem "jekyll-sitemap", "~> 1.4"
  gem "jekyll-paginate", "~> 1.1"
end

# csv, bigdecimal, base64, and webrick are no longer default gems in Ruby 3.x —
# Jekyll 3.x / Liquid / safe_yaml / `jekyll serve` still require them.
gem "csv"
gem "bigdecimal"
gem "base64"
gem "webrick"

# Windows and JRuby don't include zoneinfo files; bundle the tzinfo-data gem.
platforms :mingw, :x64_mingw, :mswin, :jruby do
  gem "tzinfo", ">= 1", "< 3"
  gem "tzinfo-data"
end

# Performance-booster for watching directories on Windows
gem "wdm", "~> 0.1", :platforms => [:mingw, :x64_mingw, :mswin]

# Pin http_parser.rb on JRuby (newer versions lack a Java counterpart).
gem "http_parser.rb", "~> 0.6.0", :platforms => [:jruby]
