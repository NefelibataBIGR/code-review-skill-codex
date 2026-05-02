[English](./CONTRIBUTING.md) | [简体中文](./CONTRIBUTING.zh-CN.md)

# Contributing

This repository packages a Codex skill. Contributions should preserve discoverability, progressive disclosure, and review quality.

## Goals

- keep the skill easy for Codex to discover
- keep core instructions short and specific
- move detailed material into `reference/`
- improve review accuracy without bloating the trigger metadata

## Repository Conventions

### Required files

- `SKILL.md`
- `agents/openai.yaml`

### Optional support files

- `reference/*.md`
- `assets/*`
- `scripts/*`

### Current layout

```text
code-review-codex/
|-- SKILL.md
|-- README.md
|-- README.zh-CN.md
|-- CONTRIBUTING.md
|-- CONTRIBUTING.zh-CN.md
|-- agents/
|   `-- openai.yaml
|-- reference/
|-- assets/
`-- scripts/
```

## Editing Rules

### `SKILL.md`

- Keep `name` stable unless there is a migration reason.
- Keep `description` focused on trigger conditions.
- Start the description with `Use when...`.
- Do not summarize the full workflow in the description.
- Keep the body focused on process and navigation.

### `agents/openai.yaml`

- `display_name` should stay human-readable.
- `short_description` should match the skill scope without repeating the full README.

### `reference/`

- Put heavy guidance here, not in `SKILL.md`.
- Prefer one topic per file.
- Keep filenames lowercase and hyphenated.

### `README*`

- `README.md` is the English primary document.
- `README.zh-CN.md` is the Chinese companion.
- Both files must include language-switch links at the top.
- Keep installation and usage examples aligned across both languages.

### `CONTRIBUTING*`

- `CONTRIBUTING.md` is the English primary document.
- `CONTRIBUTING.zh-CN.md` is the Chinese companion.
- Keep contribution rules aligned between both documents.

## Adding or Updating Reference Guides

When adding a new language or topic guide:

1. Add the file under `reference/`.
2. Use a clear, lowercase, hyphenated filename.
3. Link to it from `SKILL.md` only if the skill should actively route readers there.
4. Update both README files if the supported scope changed.

## Validation Checklist

Before merging:

- Confirm `SKILL.md` frontmatter is valid YAML.
- Confirm `name` and `description` still match the intended trigger behavior.
- Confirm `agents/openai.yaml` exists and is in sync with the skill name.
- Confirm language-switch links work in all four docs.
- Confirm example installation paths still match Codex conventions.
- Confirm new reference files are actually referenced or intentionally discoverable by name.

## Suggested Manual Verification

Use a fresh Codex session after installation.

### Explicit invocation test

Ask Codex:

```text
Use code-review-codex to review these changes for bugs, regressions, and missing tests.
```

Expected result:

- review is structured
- bugs and risks are prioritized
- feedback is not dominated by formatting trivia

### Natural trigger test

Ask Codex:

```text
Review these changes for security issues and maintainability problems.
```

Expected result:

- Codex recognizes this as a code review task
- the response emphasizes findings, severity, and concrete review feedback

## Non-Goals

- Do not turn the skill into a generic programming guide.
- Do not duplicate large sections from `reference/` into `SKILL.md`.
- Do not add extra docs unless they materially improve installation, contribution, or bilingual usability.
