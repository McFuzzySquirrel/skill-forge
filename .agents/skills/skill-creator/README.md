# skill-creator

A Copilot skill that guides an agent through creating a new, well-structured Copilot skill from a rough idea.

The workflow is more than a scaffold. It runs a structured interview, applies the [skill-review](../skill-review) quality rubric during scaffolding, performs a pre-flight self-check, and validates the output with a formal `skill-review` audit.

---

## What it does

1. **Interviews** the user to gather name, purpose, trigger, complexity signals, gotchas, and validation approach
2. **Selects** a flat or modular scaffold template based on complexity signals
3. **Scaffolds** the skill files, building each section intentionally against the six quality axes
4. **Pre-flight checks** the generated skill before formal validation
5. **Validates** with `skill-review` and loops until all axes score ≥ 2.0

---

## Prerequisites

- `skill-review` must be installed at `.agents/skills/skill-review/` for the validation phase (Step 5)
- Without `skill-review`, the skill scaffolds and pre-flight checks the output but cannot run the formal audit

---

## Install

Copy the skill package to your agent skills directory:

```bash
cp -r skill-creator/ .agents/skills/skill-creator/
```

Or install just the installed copy if you are working from within this repository:

```bash
# From the repo root
cp -r .agents/skills/skill-creator/ /path/to/your-project/.agents/skills/skill-creator/
```

---

## Usage

Invoke the skill by asking your Copilot agent:

> "Create a new skill for [your idea]"

or

> "Help me build a skill that [does something]"

The agent will load `skill-creator` and begin the structured interview.

---

## File Structure

```
skill-creator/
├── SKILL.md                        # Main skill — process steps and load triggers
├── README.md                       # This file
├── CHANGELOG.md
└── references/
    ├── interview-questions.md      # Full question bank for Step 1
    ├── flat-template.md            # Flat scaffold template (simple skills)
    ├── modular-template.md         # Modular scaffold template (complex skills)
    ├── quality-axes.md             # Six quality axes reframed for creation
    └── preflight-checklist.md      # Pre-flight self-check for Step 4
```

---

## Quality Axes

The skill is built around — and enforces — the same six axes used by `skill-review`:

| Axis | What it checks |
|------|---------------|
| Context economy | No generic explanations; specific and project-focused |
| Gotchas coverage | Concrete, specific edge cases — not generic advice |
| Procedural clarity | *How to approach* the work, not just *what to produce* |
| Progressive disclosure | Bulk content in `references/`; specific load triggers |
| Calibration | Prescriptiveness matched to operation fragility |
| Validation | Concrete, runnable checks — not "make sure it works" |

---

## Changelog

See [CHANGELOG.md](./CHANGELOG.md).
