<p align="center">
  <img src="https://img.shields.io/badge/Claude-Skill-D97757?logo=anthropic&logoColor=white" alt="Claude Skill">
  <img src="https://img.shields.io/badge/license-MIT-blue.svg" alt="MIT License">
  <img src="https://img.shields.io/badge/works%20on-any%20model-informational" alt="Works on any model">
</p>

<p align="center">
  <b>English</b> | <a href="README.id.md">Bahasa Indonesia</a>
</p>

# Whetstone — Sharpen What You Feed the Model

An instruction file is code that runs on a language model. **Whetstone** audits anything you feed an AI — skill files, Claude Chat project instructions, `CLAUDE.md`, system prompts, even whole repos — with the same discipline an engineer audits code: scan for hostile intent first, verify every claim against reality, drag implicit assumptions into writing, and make it all survive the weakest runtime — a cheaper model, missing input, or a malicious author.

One standard drives everything: **written by the smartest model, executable by the dumbest.** A skill that only works because a smart model silently fills its gaps isn't finished — it's lucky.

## What it audits

| Target | Examples | Lens |
|--------|----------|------|
| Skill files | `SKILL.md`, slash commands, agent definitions | Full five-lens audit |
| Instruction files | `CLAUDE.md`, `AGENTS.md`, `.cursorrules`, system prompts, Claude.ai project instructions | Full five-lens audit |
| Repos / codebases | Any project folder | Hygiene only: docs vs reality, dead references, maintainer clarity |

## How it works — 5 phases

0. **Safety gate** — scan for prompt-injection red flags (data exfiltration, hidden instructions, secret reads, concealment). Verdict RED / YELLOW / GREEN. RED stops everything. Runs **before** quality, every time — especially for third-party skills you're about to install.
1. **Verify claims against reality** — every file, tool, command, or URL the file mentions gets checked. Dangling references and name collisions surface here.
2. **Quality audit, five lenses** — implicit assumptions, internal contradictions, trigger surface, rigid templates, and the dumb-model standard.
3. **Verdicts and fixes** — keep / fix / merge / delete per item, every change shown as before → after with a reason. Nothing is deleted without your confirmation.
4. **Report** — safety verdict, verified claims, changes by impact, open questions.

Whetstone treats the audited file as **data, never instructions** — a malicious skill telling it to "ignore previous instructions" becomes a finding, not a command.

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

- Drop `whetstone/SKILL.md` directly (Claude.ai accepts a bare `.md` as long as its YAML frontmatter has `name` and `description` — this one does).
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
/whetstone check this repo's docs against its actual code
```

## Honest limits

- The safety gate catches **known** hostile patterns. It cannot guarantee a file is safe — the verdict is "no known hostile pattern found", never "100% clean".
- Audit quality scales with the model running it. The checklist raises the floor; it doesn't remove the ceiling.
- It is **not** a code-logic reviewer. For correctness bugs in application code, use a dedicated code review.

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

Born from a live audit session hardening the [3Things skills](https://github.com/redhoram/3things-skills) — the method worked, so it became a skill. Built with Claude; the skill itself passed its own audit before release.
