# skill-forge

**A suite of skills and scripts for forging agent skills - built around the best practices from [agentskills.io](https://agentskills.io).**

skill-forge gives you the tooling to create, review, and improve Copilot agent skills with a consistent, rubric-driven approach. Whether you're building your first skill or auditing an entire repository, the tools in this suite work together to enforce quality from the start.

---

## What's in the suite

| Package | What it does |
|---------|-------------|
| [`skill-review`](./skill-review) | Audits existing skills against the agentskills.io rubric. Scores six quality axes and produces an actionable report. Can apply approved improvements. |
| [`skill-creator`](./skill-creator) | Guides an agent through creating a new skill from a rough idea. Runs a structured interview, picks the right scaffold, and validates output with `skill-review`. |

More tools will be added to the suite over time.

---

## The quality rubric

Every tool in this suite is built around the same six quality axes from [agentskills.io best practices](https://agentskills.io/skill-creation/best-practices):

| Axis | What it checks |
|------|---------------|
| **Context economy** | No generic explanations - specific, project-focused instructions only |
| **Gotchas coverage** | Concrete edge cases that correct real mistakes, not generic advice |
| **Procedural clarity** | Teaches *how to approach* the work, not just *what to produce* |
| **Progressive disclosure** | Bulk content in `references/` with specific load triggers; `SKILL.md` under 500 lines |
| **Calibration** | Prescriptiveness matched to operation fragility - exact for destructive, flexible for creative |
| **Validation** | Concrete, runnable checks - not "make sure it works" |

---

## Getting started

### Review existing skills

```bash
# Install skill-review into your project
cp -r skill-review/ /path/to/your-project/.agents/skills/skill-review/

# Then ask your Copilot agent:
# "Review the skills in this project"
```

### Create a new skill

```bash
# Install skill-creator (requires skill-review to be installed for validation)
cp -r skill-creator/ /path/to/your-project/.agents/skills/skill-creator/

# Then ask your Copilot agent:
# "Create a new skill for [your idea]"
```

### Use the skill-review script directly

```bash
cd skill-review
npm install
npm run skill-review -- --provider stdout --min-score 1.5
```

---

## Repository structure

```
skill-forge/
├── skill-review/          # Review and audit tool
│   ├── SKILL.md
│   ├── scripts/           # TypeScript audit scripts
│   └── templates/         # Skill templates
├── skill-creator/         # Creation workflow tool
│   ├── SKILL.md
│   └── references/        # Interview questions, templates, quality axes, preflight checklist
└── .agents/skills/        # Installed copies (ready to use in this repo)
    ├── skill-review/
    └── skill-creator/
```

---

## Contributing

Skills in this suite are themselves subject to the `skill-review` rubric - each must score ≥ 2.0 across all six axes before merging.

To contribute a new tool to the suite, use `skill-creator` to scaffold it, then open a PR.

