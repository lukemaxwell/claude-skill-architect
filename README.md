# claude-skill-architect

A starter Claude Code skill that **interviews you** through the right questions and produces a clean **skill-spec markdown file** — which Claude can then use to build the actual skill.

> **Status:** v0.1 in development.

## Why

Most skills get written one-shot, from a vague idea, in a single editor pass. They come out shallower than they could. The fix is upstream: elicit a structured spec *before* generating the skill.

`claude-skill-architect` runs the elicitation as a conversation, not a form. It asks for the role, the use-context, what good output looks like, what the skill refuses to do, and the inputs/outputs — then writes a spec markdown that Claude (Code, claude.ai, or your tool of choice) can build from.

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
