<p align="center">
  <img src="https://img.shields.io/badge/Claude-Skill-D97757?logo=anthropic&logoColor=white" alt="Claude Skill">
  <img src="https://img.shields.io/badge/license-MIT-blue.svg" alt="MIT License">
  <img src="https://img.shields.io/badge/works%20on-any%20model-informational" alt="Works on any model">
</p>

<p align="center">
  <b>English</b> | <a href="README.id.md">Bahasa Indonesia</a>
</p>

# Whetstone — Sharpen Anything You Feed an AI

Everything you hand an AI — skills, project instructions, knowledge documents, `CLAUDE.md` — shapes the quality of its answers. If that material is vague, self-contradicting, or hiding bad intent, the output inherits the damage. **Whetstone** checks all of it: scan for hostile intent first, verify every claim against reality, force unwritten assumptions into writing, and make sure it all still works under the weakest conditions — a cheaper model, missing input, or a malicious author.

One standard drives everything: **written by the smartest model, executable by the dumbest.** A skill that only works because a smart model silently fills its gaps isn't finished — it's lucky.

## What it audits

| Target | Examples | Audit coverage |
|--------|----------|----------------|
| Skill files | `SKILL.md`, slash commands, agent definitions | Full five-lens audit |
| Instruction files | Claude.ai project instructions, `CLAUDE.md`, `AGENTS.md`, system prompts | Full five-lens audit |
| Project knowledge | Documents uploaded to a Claude.ai Project — SOPs, guides, references | Full five-lens audit |
| Repos / project folders | Any software project | Basic hygiene: docs vs reality, dead references, clarity for the next person |

## How it works — 5 phases

0. **Safety gate** — before anything else, check whether the file carries bad intent: telling the AI to send data out, read passwords/credentials, hide instructions, or keep things from you. Verdict RED / YELLOW / GREEN — RED stops everything. Matters most for skills written by someone else that you're about to install.
1. **Verify claims against reality** — everything the file mentions gets checked for actual existence: other files, tools, commands, links, referenced steps. Dead references and name collisions surface here.
2. **Quality audit, five lenses** — unwritten assumptions, rules that contradict each other, when the skill should fire (and when it shouldn't), templates that force making things up, and the core test: could a much dumber model run this exactly the same way?
3. **Verdicts and fixes** — every part gets a verdict: keep / fix / merge / delete. Every proposal is shown as before → after with the reason. Nothing is deleted without your approval.
4. **Report** — safety result, claims that held up (and those that didn't), changes ordered by impact, plus the questions only you can answer.

Whetstone treats the audited file as **data, never commands** — a malicious file saying "ignore previous instructions" becomes a finding in the report, not an order to follow.

## Install

**Claude Code** — copy the `whetstone/` folder into your skills directory:

```
# personal (all projects)
~/.claude/skills/whetstone/SKILL.md

# or per project
.claude/skills/whetstone/SKILL.md
```

Then call it with `/whetstone`.

**Claude.ai / Claude app** — Settings → Capabilities → Skills → Upload. Two options:

- Drop `whetstone/SKILL.md` directly (a bare `.md` is accepted as long as its YAML frontmatter has `name` and `description` — this one does).
- Or zip the `whetstone/` folder first, if you prefer a `.zip`/`.skill` package:

```
# Windows
tar -a -cf whetstone.zip whetstone

# macOS / Linux
zip -r whetstone.zip whetstone
```

## Usage

```
/whetstone audit my skill in ./my-skill/SKILL.md
/whetstone is this skill safe to install? [paste or point to a GitHub skill]
/whetstone harden my CLAUDE.md
/whetstone check my project instructions & docs — anything unclear?
```

## Honest limits

- The safety gate catches **known** hostile patterns. There is no 100% safety guarantee — the verdict is always "no known hostile pattern found", never "definitely clean".
- Audit quality follows the model running it. This checklist makes an ordinary model work far more thoroughly — but it isn't magic.
- Hunting bugs in application code logic is not its job — use a regular code review for that.

## Structure

```
Whetstone/
├── whetstone/
│   └── SKILL.md       ← the skill (this is what you install)
├── README.md          ← English
├── README.id.md       ← Bahasa Indonesia
└── LICENSE
```

## Credit

**Creator** — Redho Ramadhani · [linkedin.com/in/redhoramadhanihamid](https://id.linkedin.com/in/redhoramadhanihamid) · [github.com/redhoram](https://github.com/redhoram)

Built with Claude. The skill passed its own audit before release.
