---
title: Hugo - Static Site Generator
tags: [web, website, hugo, static-site-generator, site-generator, website-generator]
---

TODO
* `{{ .Site.Title }}`
* `{{ .Page.Title }}`
* `{{ partial "meta.html" . }}`
* `{{ .Title }}`
* `{{ .Content }}`
* `{{ block "main" . }}{{ end }}`
* `{{ define "main" }}<p>sth</p>{{ end }}`
* `{{ print .Page.Title }}`
```
{{ $style := resources.Get "sass/main.scss" | resources.ToCSS | resources.Minify }}
<link rel="stylesheet" href="{{ $style.Permalink }}">
```

Create new hugo website.

```sh
hugo new site NAME
```

Modify `baseURL` and `title` values in `config.toml` file.

Run Hugo server in background.

```sh
hugo serve --buildDrafts --noHTTPCache
# Press <Ctrl+Z> # Stop current process.
bg # Continue stopped process in backgroud.
```

To create first page using markdown.

```sh
echo '# First Markdown Page' > content/_index.md
```

```
echo "theme = 'anake'" >> config.toml
```

## Structure

* config.toml - general settings such as project title, author etc.
* themes - place to put a hugo "theme", that is things below prepared by someone
* content/ - Content written in markdown format.
    * _index.md - You can add inforamtion to directory using _index.md
* layouts/ - HTML templates for markdown files (uses go-template language)
    * _default/
        * baseof.html - Base  for any page, both single and list.
        * list.html   - Template for pages from directories.
        * single.html - Template for pages from markdowns.
    * partials/ - HTML template part, it can be called from other template.
        * nav.html - Example of partial layout for navigation bar.
    * index.html - General templates are overwritten when the template has the same name.
* archetypes - markdown template for a new page, use: `hugo new SECTION/NAME.md`.
* public/ - `hugo` command generates the website there
* assets/
    * sass/main.scss
