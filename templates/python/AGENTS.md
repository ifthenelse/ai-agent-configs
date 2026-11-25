# <project>: instructions for AI coding agents

## Scope
- Canonical contract for coding agents (Claude Code, Codex, Copilot, Aider). `CLAUDE.md` and
  `.github/copilot-instructions.md` only point here.

## Stack
- Python 3.12 or later, managed with `uv` (`pyproject.toml` plus committed `uv.lock`).
- Layout: `src/<package>/` (code), `tests/` (offline tests with fakes).
- MCP servers: stdio transport, read-only by default, compact output to keep token cost low.

## Commands
- Install: `uv sync`.
- Verify everything: `uv run ruff format --check && uv run ruff check && uv run pytest`.

## Verification
- Run the verify command before handing work back; it must pass. CI runs the same checks.
- Add or update tests for behaviour you change. Tests must not call live services unless opted in.

## Constraints
- Commit messages follow Conventional Commits 1.0.0 (see `.gitmessage.txt`). Keep changes small and focused.
- Versioning follows Semantic Versioning 2.0.0. The single version source is `version` in `pyproject.toml`.
  Release tags are `vMAJOR.MINOR.PATCH` and must equal that field.
- Do not reformat unrelated code. Never edit `uv.lock` by hand; use `uv lock`.
- Never commit secrets or `.env` files. `.env.example` holds names and safe placeholders only.

## Approval boundaries
Ask the user before: adding or upgrading a dependency, changing CI/CD or infrastructure, changing a data
schema or public contract, deleting files, touching secrets or credentials, pushing or opening a PR.

## Hand-off
Summarise what changed and why, which checks you ran with their result, and any open risk or follow-up.
