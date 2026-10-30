---
icon: logo
---

# Packaging the theme

The theme can be packaged as a Python package named `mkdocs-deltares-theme`, so that other MkDocs sites can install it instead of copying files. The package registers a theme called `deltares` that extends an installed base theme (`material` or `materialx`).

The package is generated from `deltares/overrides` by `build_package.py` in the repository root. Do not edit the generated output in `build/`; change the sources and regenerate.

## Build the package

Install the build tools, then run the script from the repository root:

```console
python -m pip install build twine
python build_package.py --version 0.1.0 --base materialx --wheel
```

| Option | Meaning |
| --- | --- |
| `--version` | Version of the package. Default `0.1.0`. |
| `--base` | Theme to extend: `material` (default) or `materialx`. Use the one the consuming site uses. |
| `--wheel` | Also build a wheel and source distribution into `dist/`. |
| `--upload` | Build and upload to Nexus (see below). |

Without `--wheel` or `--upload`, only the package sources are generated in `build/mkdocs-deltares-theme`.

## Publish to Nexus

Packages are hosted in the `python-dev` repository on Nexus:

```text
https://internal-artifacts.deltares.nl/repository/python-dev/
```

Nexus credentials are supplied through environment variables. Never write them in a file in the repository.

**Windows (PowerShell)**

```powershell
$env:TWINE_USERNAME = "<nexus-username>"
$env:TWINE_PASSWORD = "<nexus-password>"
python build_package.py --version 0.1.1 --base materialx --upload
```

**macOS / Linux**

```sh
export TWINE_USERNAME="<nexus-username>"
export TWINE_PASSWORD="<nexus-password>"
python build_package.py --version 0.1.1 --base materialx --upload
```

!!! warning
    Nexus rejects an upload of a version that already exists. Increase `--version` for every upload.

Use a Nexus user token rather than a personal password where possible, and rotate it if it has been shared.

## Use the package in another project

The example below is based on a documentation project that is built with `uv` and MkDocs (or ProperDocs) on a CI runner. Replace the names with your own.

### 1. Add the dependency and the Nexus index

In `pyproject.toml`:

```toml
[project]
name = "my-docs"
requires-python = ">=3.12"
dependencies = [
    "mkdocs-materialx>=10.1.4",
    "mkdocs-deltares-theme>=0.1.0",
]

[tool.uv.sources]
mkdocs-deltares-theme = { index = "deltares-python-dev" }

[[tool.uv.index]]
name = "deltares-python-dev"
url = "https://internal-artifacts.deltares.nl/repository/python-dev/simple/"
explicit = true
```

`explicit = true` makes uv use this index only for `mkdocs-deltares-theme`, and all other packages still come from PyPI.

### 2. Supply the credentials

uv reads credentials for an index from environment variables derived from the index name. For the index `deltares-python-dev`:

```text
UV_INDEX_DELTARES_PYTHON_DEV_USERNAME
UV_INDEX_DELTARES_PYTHON_DEV_PASSWORD
```

Set them in your shell for local work, then lock and sync:

```powershell
$env:UV_INDEX_DELTARES_PYTHON_DEV_USERNAME = "<nexus-username>"
$env:UV_INDEX_DELTARES_PYTHON_DEV_PASSWORD = "<nexus-password>"
uv lock
uv sync
```

The credentials are not stored in `uv.lock`. Commit the updated `uv.lock`.

In GitLab CI, define the same two variables as masked CI/CD variables (or load them from your secrets manager). If dependencies are installed inside a Docker build, they must also be available there, for example as BuildKit secrets or build arguments, because `uv sync --locked` needs to reach Nexus:

```dockerfile
RUN --mount=type=secret,id=nexus_user \
    --mount=type=secret,id=nexus_password \
    UV_INDEX_DELTARES_PYTHON_DEV_USERNAME="$(cat /run/secrets/nexus_user)" \
    UV_INDEX_DELTARES_PYTHON_DEV_PASSWORD="$(cat /run/secrets/nexus_password)" \
    uv sync --locked --no-install-project
```

### 3. Select the theme in the site configuration

In `mkdocs.yml` (or `properdocs.yml`):

```yaml
theme:
  name: deltares
  # Optional: keep a local folder for extra templates, such as a custom home page
  custom_dir: overrides
```

The theme sets the logo, favicon, language, palette and default features. Any value in your own `theme:` block overrides these defaults. Local files in `custom_dir` override the templates in the package, and `extra_css` still works for site-specific styling.

### 4. Prefix base-theme plugins

Plugins that ship with `materialx` are registered as `materialx/<name>`. MkDocs only resolves the short name when the theme is called `materialx`, so with `name: deltares` write:

```yaml
plugins:
  - materialx/search
  - materialx/meta
  - materialx/tags
  - materialx/privacy:
      enabled: !ENV [CI, false]
```

Plugins from other packages, such as `awesome-nav`, keep their normal names. The same applies to `material` as base theme, where the prefix is `material/`.

### 5. Check the result

```console
uv run mkdocs build
```

Open the generated site and confirm the Deltares header and styling are present. If the build reports `The "deltares" theme is not installed`, the package is missing from the active environment. Run `uv sync` again with the credentials set.

## Troubleshooting

| Symptom | Cause and fix |
| --- | --- |
| `401 Unauthorized` from uv or twine | The username or password variable is missing or wrong. |
| `400 Bad Request` from twine | Most likely that version already exists. Bump `--version`. |
| `The "privacy" plugin is not installed` | Prefix base-theme plugins with `materialx/` (step 4). |
| Theme looks like plain Material | The package was built with a different `--base` than the site uses, or `name: deltares` is not set. |
