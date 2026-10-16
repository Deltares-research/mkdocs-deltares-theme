# MkDocs Deltares Theme

A documentation site demonstrating the Deltares styling for [Material for
MkDocs](https://squidfunk.github.io/mkdocs-material/). The site configuration
is in `mkdocs.yml` and the Markdown source files are in `docs/`.

## Requirements

- Python 3
- pip

## Set up locally

From the project directory, create and activate a virtual environment, then
install Material for MkDocs (which includes MkDocs):

**Windows (PowerShell)**

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
python -m pip install mkdocs-material
```

**macOS / Linux**

```sh
python3 -m venv .venv
source .venv/bin/activate
python -m pip install mkdocs-material
```

## Build the site


Build the static site into the `site/` directory:

```
python -m mkdocs build
```

**Build in PyCharm terminal**

```pycharm
mkdocs build
```

## Serve locally

Start the development server:

```
python -m mkdocs serve
```

**Serve from PyCharm terminal**

```pycharm
mkdocs serve
```

Open [http://127.0.0.1:8000/mkdocs-deltares-theme](http://127.0.0.1:8000/mkdocs-deltares-theme) in your browser. The
server rebuilds the site when documentation or configuration files change.
Press `Ctrl+C` to stop it.

## Check out the site

> [!NOTE]
> Please note that the site is a work in progress.

The site is available at [https://deltares-research.github.io/mkdocs-deltares-theme/](https://deltares-research.github.io/mkdocs-deltares-theme/).