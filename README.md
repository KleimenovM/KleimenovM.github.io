# Maksim Kleimenov’s website

A static website built with Jekyll. Existing HTML page URLs and article image paths are preserved.

## Local preview

With Ruby and Bundler installed:

```sh
bundle install
bundle exec jekyll serve
```

Open http://127.0.0.1:4000. Preview the built website through Jekyll rather than opening source HTML files directly: source pages now contain template metadata.

To build without starting a server:

```sh
bundle exec jekyll build
```

The generated website is written to `_site/`, which is ignored by Git. Restart the preview server after changing `_config.yml`.

## Shared navigation and layout

- `_includes/navigation.html` is the single sidebar used by every page. Edit its links, name, or profile photo once to update all pages.
- `_layouts/default.html` supplies the document head, shared CSS, and page wrapper. `{{ content }}` is replaced by each page’s HTML.
- Each page starts with YAML front matter selecting its layout and title. Page-specific CSS is listed under `stylesheets`.

For example:

```html
---
layout: default
title: My page
stylesheets:
  - /css/blog.css
---

<section class="notes">
  <h1>My page</h1>
  <p>Page content goes here.</p>
</section>
```

Keep article images alongside their article and use relative links such as `image1.jpg`. Shared templates use Jekyll’s `relative_url` filter so links respect the configured `baseurl`.

## Publishing

Commit the source files, including `_includes`, `_layouts`, and `_config.yml`. For GitHub Pages, use a Jekyll build (such as Pages’ branch publishing), rather than deploying the unprocessed source as plain HTML. Do not add `.nojekyll`.

The repository does not include a deployment workflow or change your GitHub Pages settings. If your existing deployment uploads static files directly, change it to build Jekyll and upload `_site/`.
