# Project Name

> CBRE Investment IQ — AI team project. Clone from template and update this README.

## Quick Start

### Prerequisites

- Python 3.12+
- [uv](https://docs.astral.sh/uv/) — install with `curl -LsSf https://astral.sh/uv/install.sh | sh`

### Setup

```bash
# Install dependencies (creates .venv automatically)
uv sync

# Install pre-commit hooks
uv run pre-commit install

# Copy environment variables template
cp .env.example .env
# Edit .env with your credentials
```

### Devcontainer (Alternative)

The devcontainer provides a fully configured environment — Python 3.12, uv, Azure CLI, AWS CLI, pre-commit hooks, and all VS Code extensions — with zero local setup.

1. Install [Docker Desktop](https://www.docker.com/products/docker-desktop/) and the [Dev Containers](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers) VS Code extension
2. Open this repo in VS Code
3. When prompted, click **"Reopen in Container"** (or run `Dev Containers: Reopen in Container` from the command palette)
4. Wait for the build to finish — dependencies sync and pre-commit hooks install automatically
5. Copy `.env.example` to `.env` and fill in your credentials

Everything is ready to use once the container starts. Subsequent opens are fast since the image is cached.

## After Cloning This Template

Update the project metadata in `pyproject.toml`:

```toml
[project]
name = "your-project-name"             # Replace with your project name
version = "0.1.0"                       # Reset or keep as-is
description = "What this project does"  # One-line summary
```

Then update the heading and description at the top of this `README.md` to match your project.

> There are no `uv` commands for changing name or description — edit `pyproject.toml` directly. Version can be bumped manually or via `uv add`/`uv remove` which regenerates the lockfile automatically.

## Project Structure

```
.
├── .devcontainer/          # Dev container configuration
│   └── devcontainer.json
├── .github/
│   └── copilot-instructions.md
├── .vscode/                # Shared VS Code settings
│   ├── extensions.json
│   └── settings.json
├── configs/                # Configuration files (YAML, JSON, etc.)
├── data/                   # Data directory (gitignored — see conventions below)
│   └── sample.txt
├── docs/                   # Documentation
├── notebooks/              # Jupyter notebooks for exploration
│   └── 01_pathlib_example.ipynb
├── pipelines/              # CI/CD pipeline definitions (placeholder)
├── scripts/                # Utility scripts
├── src/                    # Production source code
├── .env.example            # Environment variables template
├── .gitignore
├── .pre-commit-config.yaml
├── .python-version
├── pyproject.toml          # Project metadata and dependencies
└── README.md
```

## Data Directory Conventions

The `data/` directory is gitignored. Create subdirectories as needed:

- `raw/` — Original, immutable data
- `processed/` — Cleaned, transformed data
- `external/` — Data from third-party sources

Never commit real data files to git. Only `data/sample.txt` is tracked as a template example.

## Daily Workflow

1. **Pick a task** from Azure DevOps board
2. **Create a branch**: `git checkout -b feature/your-task-name`
3. **Code** — write your changes in `src/`, explore in `notebooks/`
4. **Commit** — pre-commit hooks run automatically (ruff lint + format, file hygiene)
5. **Push**: `git push -u origin feature/your-task-name`
6. **Create a PR** targeting `main`
7. **Squash merge** after review

> Direct commits to `main` are blocked by a pre-commit hook. Always use feature branches.

## Dependency Management

```bash
# Add a package
uv add pandas

# Add a dev-only package
uv add --group dev pytest

# Remove a package
uv remove pandas

# Sync all dependencies (after pulling changes)
uv sync
```

## Code Quality

Ruff handles both linting and formatting. Pre-commit hooks run these automatically on every commit, but you can also run them manually:

```bash
# Lint check
uv run ruff check .

# Lint with auto-fix
uv run ruff check . --fix

# Format check
uv run ruff format . --check

# Format (apply changes)
uv run ruff format .

# Run all pre-commit hooks on all files
uv run pre-commit run --all-files
```
