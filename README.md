# ai-agent-configs

Drop-in instruction files for AI coding agents (Claude Code, Codex, GitHub Copilot, Aider), tuned to the kinds of
projects I build. One canonical `AGENTS.md` per project; every tool-specific file only points to it.

## What I build (July to November 2026, public and private repos)

| Project type | Public examples | Template |
| --- | --- | --- |
| Rust command-line tools and demos | `migadu-cli`, `router-monitor`, `raycasting-webassembly-demo` | `templates/rust` |
| Python MCP servers, agent skills, ML and macOS tools | `renpho-mcp-server`, `oss-showcase`, `Super-Mario-Bros-AI` | `templates/python` |
| TypeScript MCP servers, scrapers, browser extensions, web apps and games | `nabz`, `GIT-for-AI-crash-course` | `templates/typescript` |
| Native Apple apps (Swift) | | `templates/swift` |

Low-level demos (assembly) are not templated: they are too small to need one.

## How the tools read these files

Checked against Claude Code 2.1.x, Codex CLI 0.17x and GitHub Copilot (coding agent, CLI and VS Code) in November 2026.

| Tool | Reads | In this repo |
| --- | --- | --- |
| Codex | `AGENTS.md` (walks up from the working directory to the repo root) | `AGENTS.md` only |
| Claude Code | `CLAUDE.md` | `CLAUDE.md` containing `@AGENTS.md` |
| GitHub Copilot | `AGENTS.md`, `.github/copilot-instructions.md`, `.github/instructions/*.instructions.md` | `.github/copilot-instructions.md` pointer |
| Aider | files named in `.aider.conf.yml` | `read: AGENTS.md` |

## Use it

Copy `templates/base` plus one stack into your project, then replace `<project>` and adjust the commands:

```bash
cp -R templates/base/. /path/to/project/
cp templates/rust/AGENTS.md /path/to/project/AGENTS.md
git -C /path/to/project config commit.template .gitmessage.txt
```

## Versioning

- Commits follow [Conventional Commits 1.0.0](https://www.conventionalcommits.org/en/v1.0.0/); pull requests are checked by commitlint.
- Versions follow [Semantic Versioning 2.0.0](https://semver.org/). On every push to `main`,
  [release-please](https://github.com/googleapis/release-please) opens or updates a release pull request that bumps the version
  from the commit types (`fix` is a patch, `feat` a minor, `!` or `BREAKING CHANGE` a major; while below 1.0.0 breaking changes bump the minor)
  and updates `CHANGELOG.md`. Merging it tags the release.

## License

MIT
