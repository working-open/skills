# Skills Umbrella Repository

This repository combines skills from multiple sources into a single workspace.

## Structure

| Directory | Description |
|---|---|
| [`custom/`](./custom) | My own custom skills, specs, and templates |
| [`anthropic/`](./anthropic) | Upstream [Anthropic skills](https://github.com/anthropics/skills) (git submodule) |
| [`superpowers/`](./superpowers) | [obra's superpowers](https://github.com/obra/superpowers) skills (git submodule) |

## Getting Started

Clone with submodules:

```bash
git clone --recurse-submodules <this-repo-url>
```

If you already cloned without `--recurse-submodules`:

```bash
git submodule update --init --recursive
```

## Updating Upstream Skills

Pull the latest from all submodules:

```bash
git submodule update --remote
```

Or update a specific one:

```bash
git submodule update --remote anthropic
git submodule update --remote superpowers
```

## Custom Skills

The `custom/` directory contains:

- [`custom/skills/`](./custom/skills) — Skill definitions
- [`custom/spec/`](./custom/spec) — The Agent Skills specification
- [`custom/template/`](./custom/template) — Skill template

For more information on skills, see:
- [What are skills?](https://support.claude.com/en/articles/12512176-what-are-skills)
- [Using skills in Claude](https://support.claude.com/en/articles/12512180-using-skills-in-claude)
- [How to create custom skills](https://support.claude.com/en/articles/12512198-creating-custom-skills)
