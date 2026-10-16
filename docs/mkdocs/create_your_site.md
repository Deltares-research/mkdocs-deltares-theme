---
icon: logo
---

# Create your site

The **Deltares MkDocs template** is a starting point for creating your own documentation site. It provides a basic structure and configuration that you can customize to fit your needs.

In this guide, we will walk you through the steps to customize your own documentation site using the Deltares MkDocs template.

## Prerequisites

- Python 3
- pip

You also need Material for MkDocs installed in your Python environment. See
[Running your site locally](deploy_your_site.md#running-your-site-locally) for
the setup commands.

## Configure mkdocs.yml

The `mkdocs.yml` file in the project root controls your site's name, theme,
navigation, and Markdown features. Edit this file rather than files in the
generated `site` directory, which are overwritten on each build.

YAML uses indentation to group settings. Use spaces, not tabs, and keep list
items aligned. Update the existing sections rather than adding duplicate
top-level keys such as `theme` or `nav`.

### Site name and URL

Start by replacing the demonstration site's details with your own:

```yaml
site_name: My project documentation
site_url: https://deltares-research.github.io/my-project/
site_description: User and developer documentation for my project.
site_author: Deltares
```

| Setting | Purpose |
| --- | --- |
| `site_name` | The name displayed in the header and browser title. |
| `site_url` | The full public URL where the site will be published, including a project subpath when applicable. Keep the trailing slash. |
| `site_description` | An optional summary used in the site's HTML metadata. |
| `site_author` | Optional author metadata. |

The URL above is an example; use your actual publishing location. Setting
`site_url` does not deploy the site. See [Deploy your site](deploy_your_site.md)
for publishing instructions.

### Keep the Deltares theme

This project uses Material for MkDocs with local Deltares template overrides.
Keep the following settings to retain the Deltares layout, logo, and colours:

```yaml
theme:
  name: material
  custom_dir: deltares/overrides
  logo: assets/logo-of-deltares.svg
  favicon: assets/favicon-16x16.png
  language: en
  palette:
    - scheme: default
      primary: custom
      accent: custom
```

`custom_dir` is relative to the directory containing `mkdocs.yml`. It loads
the templates and assets from `deltares/overrides`, including the Deltares
stylesheet through `main.html`. Keep that directory when reusing this
configuration in another project; installing Material alone does not provide
these overrides.

The logo and favicon paths refer to site assets. The supplied files are in
`deltares/overrides/assets`. To use your own images, place them in an `assets`
directory under `docs` and change `logo` and `favicon` to their paths relative
to `docs`, for example `assets/my-project-logo.svg`.

`language` controls the theme's interface labels, not the language of your
Markdown content. For Dutch interface labels, use `language: nl`.

### Navigation and interface features

The `features` list belongs inside the existing `theme` section:

```yaml
theme:
  # Keep the other theme settings here.
  features:
    - navigation.tabs
    - navigation.tabs.sticky
    - navigation.expand
    - navigation.path
    - navigation.top
    - navigation.footer
    - search.suggest
    - search.highlight
    - content.code.copy
    - toc.integrate
```

| Feature | Effect |
| --- | --- |
| `navigation.tabs` | Shows top-level navigation sections as tabs on larger screens. |
| `navigation.tabs.sticky` | Keeps navigation tabs visible while scrolling. |
| `navigation.expand` | Expands navigation sections by default. |
| `navigation.path` | Enables breadcrumb navigation in Material versions that support it. |
| `navigation.top` | Adds a back-to-top button. |
| `navigation.footer` | Shows previous and next page links in the footer. |
| `search.suggest` | Enables search suggestions. |
| `search.highlight` | Highlights matching search terms on destination pages. |
| `content.code.copy` | Adds copy buttons to code blocks. |
| `toc.integrate` | Places the page's table of contents in the left navigation instead of a separate sidebar. |

Remove a feature's list entry to disable it. Do not leave an empty `-` entry.
Feature availability can depend on your installed Material version; consult
the [Material setup documentation](https://squidfunk.github.io/mkdocs-material/setup/)
when choosing additional features.

### Organize pages with nav

Use the top-level `nav` section to choose page labels, order, and grouping.
For example, the following uses pages already included in this project:

```yaml
nav:
  - Home: index.md
  - Get started:
      - MkDocs: mkdocs/mkdocs.md
      - Create your site: mkdocs/create_your_site.md
      - Deploy your site: mkdocs/deploy_your_site.md
  - Deltares styles:
      - Buttons: style_examples/buttons.md
      - Headers: style_examples/headers.md
      - Lists: style_examples/lists.md
      - Tables: style_examples/tables.md
```

Page paths are relative to `docs` by default, not to `mkdocs.yml`. For example,
to add a user guide, create `user_guide.md` inside `docs`, then add
`- User guide: user_guide.md` at the desired position in `nav`.
The label before the colon controls the menu text; the page's Markdown heading
controls its visible heading.

With `navigation.tabs` enabled, top-level groups such as `Get started` become
tabs. Nested entries form their navigation menus. Removing a page from `nav`
does not delete it or prevent MkDocs from building it.

### Enable Markdown features

The top-level `markdown_extensions` section enables syntax used by the example
pages:

```yaml
markdown_extensions:
  - attr_list
  - pymdownx.emoji:
      emoji_index: !!python/name:material.extensions.emoji.twemoji
      emoji_generator: !!python/name:material.extensions.emoji.to_svg
  - def_list
  - pymdownx.tasklist:
      custom_checkbox: true
  - tables
  - pymdownx.superfences
  - pymdownx.tabbed:
      alternate_style: true
```

`attr_list` supports attributes such as the CSS classes used for
[buttons](../style_examples/buttons.md). The other entries enable emoji and
icons, definition lists, task lists, tables, enhanced fenced code blocks, and
content tabs. Keep the extensions required by your pages. The extensions shown
here are available with the Material for MkDocs installation.

### Add project-specific CSS or JavaScript

The project includes optional files in `docs/stylesheets/extra.css` and
`docs/javascripts/extra.js`. Enable them by uncommenting the corresponding
settings in `mkdocs.yml`:

```yaml
extra_css:
  - stylesheets/extra.css
extra_javascript:
  - javascripts/extra.js
```

These are top-level settings, not entries under `theme`. Paths are relative to
`docs`. Use these files for project-specific additions rather than modifying
Material's installed files. The Deltares stylesheet is already loaded by the
template override; it does not need an `extra_css` entry.

## Preview your configuration

From the project root, with your Python environment activated, run:

```console
python -m mkdocs serve
```

Open the local URL printed in the terminal. Save `mkdocs.yml` or a Markdown
page to rebuild the preview automatically. Check the site title, navigation,
images, and any Markdown features you use. If MkDocs reports an error, check
YAML indentation and confirm that referenced pages and assets exist.

Before publishing, build the static site:

```console
python -m mkdocs build
```

For additional settings, see the
[MkDocs configuration reference](https://www.mkdocs.org/user-guide/configuration/)
and the [Material for MkDocs documentation](https://squidfunk.github.io/mkdocs-material/).