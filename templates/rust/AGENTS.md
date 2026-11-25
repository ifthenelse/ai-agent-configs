# <project>: instructions for AI coding agents

## Scope
- Canonical contract for coding agents (Claude Code, Codex, Copilot, Aider). `CLAUDE.md` and
  `.github/copilot-instructions.md` only point here.

## Stack
- Rust (edition 2021 or later, pin `rust-version` in `Cargo.toml`). Keep direct dependencies few.
- Layout: `src/` (library plus `main.rs`), `tests/` (offline tests with fakes).

## Commands
- Verify everything: `cargo fmt --check && cargo clippy --all-targets -- -D warnings && cargo test`.
- Build and run: `cargo run --release -- --help`.

## Verification
- Run the verify command before handing work back; it must pass. CI runs the same checks.
- Add or update tests for behaviour you change. Live or state-changing tests must be opt-in.

## Constraints
- Commit messages follow Conventional Commits 1.0.0 (see `.gitmessage.txt`). Keep changes small and focused.
- Versioning follows Semantic Versioning 2.0.0. The single version source is `version` in `Cargo.toml`
  (`Cargo.lock` follows it). Release tags are `vMAJOR.MINOR.PATCH` and must equal that field.
- Do not reformat unrelated code. Do not edit generated files or lockfiles by hand.
- Never commit secrets or `.env` files. `.env.example` holds names and safe placeholders only.

## Approval boundaries
Ask the user before: adding or upgrading a dependency, changing CI/CD or infrastructure, changing a data
schema or public contract, deleting files, touching secrets or credentials, pushing or opening a PR.

## Hand-off
Summarise what changed and why, which checks you ran with their result, and any open risk or follow-up.
