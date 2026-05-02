[English](./README.md) | [简体中文](./README.zh-CN.md)

# Code Review Codex for Codex

Reference: adapted from https://github.com/awesome-skills/code-review-skill

A modular skill for Codex that turns code review into a structured, high-signal process.

It is designed for pull requests, patch review, architecture review, security review, and general code quality work across multi-language repositories.

## What This Repository Contains

- `SKILL.md`: the primary skill entrypoint and trigger metadata
- `agents/openai.yaml`: Codex UI metadata
- `reference/`: language- and topic-specific review guides loaded as needed
- `assets/`: reusable templates and checklists
- `scripts/`: helper tooling, including PR analysis support

## Supported Review Areas

- React
- Vue
- TypeScript
- Python
- Java
- Go
- Rust
- C
- C++
- CSS / Less / Sass
- Qt
- Architecture review
- Performance review
- Security review
- Common bug patterns

## How Codex Uses This Skill

The skill is discovered through the metadata in [SKILL.md](./SKILL.md). Its trigger description is intentionally focused on when the skill should load:

- reviewing pull requests
- reviewing code changes
- conducting architecture reviews
- conducting security reviews
- checking code quality
- finding bugs
- giving structured review feedback

Once loaded, Codex can selectively read files from `reference/` instead of pulling the entire skill into context at once.

## Install

### Global installation

Clone or copy this repository into your Codex skills directory:

```bash
# macOS / Linux
git clone https://github.com/awesome-skills/code-review-skill.git \
  ~/.codex/skills/code-review-codex

# Windows PowerShell
git clone https://github.com/awesome-skills/code-review-skill.git `
  "$env:USERPROFILE\.codex\skills\code-review-codex"
```

### Alternative location

If your setup prefers personal agent skills, copy it into:

```bash
~/.agents/skills/code-review-codex
```

After installation, restart Codex so the new skill metadata is picked up.

## Usage

### Explicit invocation

Ask Codex to use the skill directly:

```text
Use code-review-codex to review this PR.
Focus on bugs, regressions, security issues, and missing tests.
```

### Natural-language triggering

The skill is also designed to trigger from ordinary requests such as:

```text
Review these changes for bugs and maintainability issues.
```

```text
Do an architecture review of this refactor.
```

```text
Check this service for security problems before merge.
```

## Review Style

This skill is optimized for reviews that:

- prioritize bugs and regressions over style trivia
- separate blocking issues from minor suggestions
- focus on correctness, security, performance, and maintainability
- use constructive, specific feedback
- lean on language-specific guides only when relevant

## Repository Layout

```text
code-review-codex/
|-- SKILL.md
|-- agents/
|   `-- openai.yaml
|-- reference/
|   |-- react.md
|   |-- vue.md
|   |-- typescript.md
|   |-- python.md
|   |-- java.md
|   |-- go.md
|   |-- rust.md
|   |-- c.md
|   |-- cpp.md
|   |-- qt.md
|   |-- css-less-sass.md
|   |-- architecture-review-guide.md
|   |-- performance-review-guide.md
|   |-- security-review-guide.md
|   |-- common-bugs-checklist.md
|   `-- code-review-best-practices.md
|-- assets/
|   |-- review-checklist.md
|   `-- pr-review-template.md
`-- scripts/
    `-- pr-analyzer.py
```

## Notes for Maintainers

- Keep `SKILL.md` focused on triggers and core process, not exhaustive reference material.
- Put detailed patterns in `reference/`.
- Update both language docs when installation or usage changes.
- Keep examples realistic and review-oriented.

See [CONTRIBUTING.md](./CONTRIBUTING.md) for contribution and validation guidance.
