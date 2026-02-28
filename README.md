# Agent Skills

Agent Skills by [Michael Samoylov](https://www.linkedin.com/in/msamoylov/). For information about the Agent Skills standard, see [agentskills.io](http://agentskills.io).

## Available skills

| Skill | Description |
|-------|-------------|
| [zero-assumptions](skills/zero-assumptions/SKILL.md) | Makes Claude ask clarifying questions before writing code, eliminating assumptions and building exactly what you want on the first try. |

## Installation

```shell
claude plugin marketplace add msamoylov/skills
claude plugin install zero-assumptions@msamoylov-agent-skills
```

## Creating a new skill

1. Create a directory under `skills/`: `mkdir skills/your-skill-name`
2. Copy the template and customize it: `cp template/SKILL.md skills/your-skill-name/SKILL.md`
3. Add the skill path to `.claude-plugin/marketplace.json`.
