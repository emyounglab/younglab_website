source "https://rubygems.org"
# Pins Jekyll and its plugins to what GitHub Pages runs. Use `bundle exec jekyll serve`.
gem "github-pages", "~> 232", group: :jekyll_plugins

# Windows does not include zoneinfo files
platforms :windows, :mswin, :jruby do
  gem "tzinfo", ">= 1", "< 3"
  gem "tzinfo-data"
end

# Faster file watching on Windows
gem "wdm", "~> 0.1", :platforms => [:windows, :mswin]
