# Copilot Instructions

## Language & Runtime

- Python 3.12+ — use modern features: `match`/`case`, type unions with `X | Y`, `StrEnum`
- Managed with `uv` — use `uv add <package>` not `pip install`

## Code Style

- Type hints on all function signatures (parameters and return types)
- Google-style docstrings on all public functions and classes
- Line length: 120 characters max
- Formatting and linting handled by `ruff` — do not add `# noqa` without justification

## File Paths

- Always use `pathlib.Path` — never `os.path`
- Never hardcode absolute paths like `"/Users/lokesh/data/file.txt"`
- Resolve paths relative to the project root or `__file__`

## Logging & Output

- Use `logging` in `src/` code — never `print()`
- `print()` is acceptable in notebooks and scripts

## Secrets & Configuration

- Never hardcode credentials, API keys, or connection strings
- Use environment variables (loaded from `.env`) or files in `configs/`
- Reference `.env.example` for required variables

## Project Structure

- Production code lives in `src/`
- Notebooks are for exploration and prototyping only
- Keep notebooks in `notebooks/` with numbered prefixes (e.g., `01_exploration.ipynb`)

## Dependencies

- Add packages with `uv add <package>`
- Add dev packages with `uv add --group dev <package>`
- Never modify `pyproject.toml` dependencies by hand — use `uv add` / `uv remove`

## Git Workflow

- Never commit directly to `main` — use feature branches
- Write clear commit messages describing what changed and why
- Keep commits small and focused on a single change
