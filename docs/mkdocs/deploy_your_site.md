---
icon: logo
---

# Publishing your site

Detailed instructions on how to publish your site can be found in the [MkDocs documentation](https://www.mkdocs.org/user-guide/deploying-your-docs/).

And more specifically, the [Material for MkDocs documentation](https://squidfunk.github.io/mkdocs-material/publishing-your-site/) provides instructions on how to deploy your site to different platforms.

## Running your site locally

Run these commands from the project root, where `mkdocs.yml` is located. First, create and activate a Python virtual environment, then install Material for MkDocs (which includes MkDocs):

```console
python -m venv .venv
```

Activate the environment:

```console
# Windows PowerShell
.venv\Scripts\Activate.ps1

# macOS or Linux
source .venv/bin/activate
```

Install the project dependencies:

```console
python -m pip install mkdocs-material
```

Build the site into the `site/` directory:

```console
mkdocs build
```

To preview the site locally, start MkDocs' development server:

```console
mkdocs serve
```

Open [http://127.0.0.1:8000/](http://127.0.0.1:8000/) in your browser. The server rebuilds the site when you save documentation changes; stop it with `Ctrl+C`.

## Publishing your site

There are different ways to publish your site, depending on the platform you want to use. The most common platforms are GitHub Pages and GitLab Pages.

On the [Material for MkDocs documentation](https://squidfunk.github.io/mkdocs-material/publishing-your-site/) you can find instructions on how to deploy your site to different platforms.

Here are some specific instructions for publishing to one of the Deltares supported platforms.

``mkdocs gh-deploy --force``

## Deltares supported Pages

Deltares offers a number of hosting locations for your documentation site. 

### GitHub

GitHub specific instructions for deploying your site can be found in the [GitHub Pages documentation](https://docs.github.com/en/pages/getting-started-with-github-pages).

The following GitHub pages locations are available for hosting your documentation site:

* [Deltares GitHub Pages](https://deltares.github.io/) - for public documentation sites for the ``Deltares`` organization.
* [Deltares Research GitHub Pages](https://deltares-research.github.io/) - for documentation sites of the ``Deltares Research`` organization.

### GitLab

GitLab specific instructions for deploying your site can be found in the [GitLab Pages documentation](https://docs.gitlab.com/ee/user/project/pages/).


Currently, Deltares does not offer GitLab Pages hosting for documentation sites. However, we are working on providing this in the neer future. 

The expected GitLab Pages hosting locations for Deltares documentation sites are:

* [Deltares GitLab Pages](https://pages.deltares.nl/) - for public documentation sites hosted in the [Deltares GitLab](https://git.deltares.nl/) instance.
* [Open Deltares GitLab Pages](https://open-pages.deltares.nl/) - for public documentation sites hosted in the [Open Deltares GitLab](https://open-git.deltares.nl/) instance.