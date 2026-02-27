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

Open this repo in VS Code and click **"Reopen in Container"** when prompted. The devcontainer installs uv, syncs dependencies, and sets up pre-commit hooks automatically.

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
├── data/                   # Data directory (gitignored except samples)
│   ├── README.md
│   └── sample.txt
├── docs/                   # Documentation
├── notebooks/              # Jupyter notebooks for exploration
│   └── 01_pathlib_example.ipynb
├── pipelines/              # CI/CD pipeline definitions
│   └── azure-pipelines-ci.yml
├── scripts/                # Utility scripts
├── src/                    # Production source code
├── .env.example            # Environment variables template
├── .gitignore
├── .pre-commit-config.yaml
├── .python-version
├── pyproject.toml          # Project metadata and dependencies
└── README.md
```

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
