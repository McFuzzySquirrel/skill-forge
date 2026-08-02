# skill-review-updater

> Part of the [skill-forge](../README.md) suite - tools for forging agent skills based on [agentskills.io](https://agentskills.io) best practices.

A Copilot skill that checks the latest agentskills.io best practices against the current `skill-review` rubric and produces a prioritized update plan for new or revised checks.

---

## What it does

1. Captures the current `skill-review` baseline checks
2. Collects latest guidance from agentskills.io with citations
3. Maps deltas between current rubric coverage and new guidance
4. Prioritizes proposals by confidence and impact
5. Produces an implementation-ready update plan
6. Validates traceability before handoff

---

## Install

```bash
cp -r skill-review-updater/ /path/to/your-project/.agents/skills/skill-review-updater/
```

For end-to-end workflow, also install:

```bash
cp -r skill-review/ /path/to/your-project/.agents/skills/skill-review/
```

---

## Usage

Ask your Copilot agent:

> "check for updates in agentskills.io for skill-review"

The skill will produce a plan with:
- recommended new checks
- conditional candidates
- watchlist items

---

## File structure

```
skill-review-updater/
├── SKILL.md
├── README.md
└── references/
    ├── quality-baseline.md
    ├── rubric-mapping.md
    ├── offline-fallback.md
    └── validation-checks.md
```
