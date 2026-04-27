# claude-skill-architect

A starter Claude Code skill that **interviews you** through the right questions and produces a clean **skill-spec markdown file** — which Claude can then use to build the actual skill.

> **Status:** v0.1.

## Why

Most skills get written one-shot, from a vague idea, in a single editor pass. They come out shallower than they could. The fix is upstream: elicit a structured spec *before* generating the skill.

`claude-skill-architect` runs the elicitation as a short conversation — five core questions plus targeted multiple-choice probes — and produces a comprehensive spec that scopes not just *what the skill does* but the **build agent's full job**: research to perform, knowledge to codify into a reference layer, helper scripts/utilities to build, validation to run, setup and config required, and usability concerns to address.

It also provides 10x feedback — the architect proposes specific enhancements derived from your answers, you choose what's v1 vs parked vs declined. The user contributes intent; the architect contributes vision.

## Install

```bash
git clone git@github.com:lukemaxwell/claude-skill-architect.git ~/claude-skill-architect
ln -s ~/claude-skill-architect ~/.claude/skills/claude-skill-architect
```

The skill will auto-load in any Claude Code session.

## Usage

Trigger the skill with any of:

- `start a new skill`
- `architect a skill for X`
- `interview me to build a skill`
- `/claude-skill-architect`

The skill walks you through the spec questions one at a time, then writes `<your-skill-slug>-spec.md` you can hand to Claude.

## License

MIT — see [LICENSE](LICENSE).
