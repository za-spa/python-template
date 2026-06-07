# CLAUDE.md

This is a [Copier](https://copier.readthedocs.io/) template repository for Python projects.

## Repository Structure

- `copier.yml` — template variables and prompts
- `template/` — the actual template files copied into new projects (set as `_subdirectory`)
  - Files ending in `.jinja` are rendered with Jinja2 using variables from `copier.yml`
  - Directories/files with `{% ... %}` in their names are conditional

## Template Variables

| Variable | Type | Default | Description |
| --- | --- | --- | --- |
| `project_name` | str | — | Project name |
| `package_name` | str | derived from `project_name` | Python package name |
| `python_version` | str | `"3.12"` | Python version |
| `is_package` | bool | `true` | Whether to install as a package |
| `has_cli` | bool | `false` | Whether to add a CLI entry point |

## How to Test the Template

Generate a test project from the template:

```bash
copier copy . /tmp/test-project
cd /tmp/test-project
git init
task setup
task check
task test
```

## Included Tools (in generated projects)

| Tool | Purpose |
| --- | --- |
| uv | Package management and virtual environments |
| ruff | Linter and formatter |
| pyright | Type checker |
| pytest | Testing |
| pre-commit | Pre-commit hooks |
| Task | Task runner |
| GitHub Actions | CI |
