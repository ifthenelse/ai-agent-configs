# <project>: instructions for AI coding agents

## Scope
- Canonical contract for coding agents (Claude Code, Codex, Copilot, Aider). `CLAUDE.md` and
  `.github/copilot-instructions.md` only point here.

## Stack
- Swift 6 with SwiftUI, built with Xcode; Swift Package Manager for dependencies.
- Layout: app target, `Tests/` (unit tests) and a UI test target. Health or personal data stays on device.

## Commands
- Build: `xcodebuild -scheme <scheme> -destination 'platform=iOS Simulator,name=iPhone 17' build`.
- Verify everything: the same command with `test` instead of `build`.

## Verification
- Run the verify command before handing work back; it must pass. CI runs the same checks.
- Add or update tests for behaviour you change. Check UI changes in the simulator.

## Constraints
- Commit messages follow Conventional Commits 1.0.0 (see `.gitmessage.txt`). Keep changes small and focused.
- Versioning follows Semantic Versioning 2.0.0. The version source is `MARKETING_VERSION` in the Xcode project;
  bump `CURRENT_PROJECT_VERSION` for every build. Release tags are `vMAJOR.MINOR.PATCH`.
- Do not reformat unrelated code. Do not edit `project.pbxproj` by hand when Xcode or a tool can do it.
- Never commit secrets, signing certificates, provisioning profiles or `.env` files.

## Approval boundaries
Ask the user before: adding or upgrading a dependency, changing CI/CD or signing, changing a data
schema or public contract, deleting files, touching secrets or credentials, pushing or opening a PR.

## Hand-off
Summarise what changed and why, which checks you ran with their result, and any open risk or follow-up.
