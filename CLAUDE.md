# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository purpose

A skills repository for Claude Code, following the [anthropics/skills](https://github.com/anthropics/skills) pattern. Each skill lives under `skills/` as a self-contained folder with a `SKILL.md` file.

## Structure

- `.claude-plugin/marketplace.json` — marketplace registry
- `skills/<name>/SKILL.md` — skill definition with YAML frontmatter and markdown instructions
- `skills/<name>/LICENSE` — per-skill license
- `template/SKILL.md` — starter template for new skills

## Adding a new skill

1. Create `skills/<skill-name>/` directory
2. Create `skills/<skill-name>/SKILL.md` — set `name`, `description` in YAML frontmatter, write instructions in markdown
3. Add a LICENSE file to `skills/<skill-name>/`
4. Add the skill path to the `skills` array in `.claude-plugin/marketplace.json`

## Conventions

- Skill names use kebab-case
- Each skill is self-contained in its own directory under `skills/`
- Descriptions live in SKILL.md frontmatter, not separate README files
