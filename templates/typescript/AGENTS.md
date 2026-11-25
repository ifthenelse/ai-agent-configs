# <project>: instructions for AI coding agents

## Scope
- Canonical contract for coding agents (Claude Code, Codex, Copilot, Aider). `CLAUDE.md` and
  `.github/copilot-instructions.md` only point here.

## Stack
- TypeScript (strict) on the Node version in `.node-version`; npm with a committed `package-lock.json`.
- Layout: `src/` (code), `tests/` (unit tests; Playwright for browser flows when the project has a UI).
- MCP servers: read-only tools by default, validate every tool input, keep responses compact, never log secrets.
- Scrapers: respect the site's terms, rate-limit requests, keep selectors in one place.
- Browser extensions and web tools: no tracking, no external services unless the project states otherwise.

## Commands
- Install: `npm ci`.
- Verify everything: `npm run lint && npm run typecheck && npm test` (add the scripts if missing).
- Build: `npm run build`.

## Verification
- Run the verify command before handing work back; it must pass. CI runs the same checks.
- Add or update tests for behaviour you change.

## Constraints
- Commit messages follow Conventional Commits 1.0.0 (see `.gitmessage.txt`). Keep changes small and focused.
- Versioning follows Semantic Versioning 2.0.0. The single version source is `version` in `package.json`
  (keep `manifest.json` in sync for extensions). Release tags are `vMAJOR.MINOR.PATCH`.
- Do not reformat unrelated code. Never edit `package-lock.json` by hand.
- Never commit secrets or `.env` files. `.env.example` holds names and safe placeholders only.

## Approval boundaries
Ask the user before: adding or upgrading a dependency, changing CI/CD or infrastructure, changing a data
schema or public contract, deleting files, touching secrets or credentials, pushing or opening a PR.

## Hand-off
Summarise what changed and why, which checks you ran with their result, and any open risk or follow-up.
