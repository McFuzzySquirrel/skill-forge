# Context
We need a reusable skill that helps users turn a rough idea into a well-structured, validated coptlot sk111. The workflow should be more than a simple scaffold: It should gather context, apply quality heuristics, gulde the user through explicit decisions, and then verify the output with the existing skill-review tool.
The implementation must be practical for real-world usage in this repository:
int should work as stone without Introducing separate orchestrator agent unless the user explicitly.esks for one.
      ⁃     ﻿﻿It should be adaptive: simple ideas should use a flat structure, while more complex ideas should use a modular structure with 'references/.
      ⁃     ﻿﻿It must integrate tightly with skill-review because the quality bar should be enforced during creation, not only as a post-hoc audit.
# Decision 1: Implement this as a skill-only capability
## Decision
Implement zac-skill-create
as a skill only. It will guide the agent through the workflow directly from "SKILL.nd and supporting references.
## Rationale
      ⁃     ﻿﻿**Lower overhead.** The CLI agent already has the tools it needs; no extra agent file is required for the core use case.
      ⁃     ﻿﻿**Easier to adopt.** Users can copy a single skill package into
-agents/skills/" and use it immediately.
-**Keeps the workflow focused.** The skill itself can orchestrate the interview, scaffold, and validation flow without introducing a second abstraction layer.
##* Trade-offs

A separate agent file could be useful for multi-agent orchestration later, but that would add complexity and is not required for the Inftial workflow.

** Decision 2: Use the "skill-review rubric as the guiding framework throughout creation
# Peciston
The workflow is built around the six "skill-review quality axes:
      ⁃     ﻿Context economy
      ⁃     ﻿﻿Gotchas coverage
      ⁃     ﻿﻿Procedural clarity
      ⁃     ﻿﻿Progressive disclosure
      ⁃     ﻿﻿Calibration
      ⁃     ﻿﻿Validation
The skill uses those axes in three places:
1. During the Intervletenterather.the right, information
2. During scaffolding,
to build each section of the new skill intentionally
3. During validation, to run a pre-flight self-check and then the formal skill-review audit


• ADR-0801: zac-sk111-create Architecture
# Decision 2: Use the skill-review rubric as the guiding framework throughout ereation
特料# Decision
3. During validation,
to run a pre-flight self-check and then the formal skill-revlew audit
Rationale
This makes the new skill more than a generte template generator. It ensures the created skil1 is shaped around the same quality rules that the repository already uses to assess skill
*** Trade-offs
The workflow becomes more structured and slightly longer, but the resulting output is significantly more consistent and easier to review.

## Decision 3: Use adaptive scaffolding templates
*# Decision
The skill will choose between a flat template and a modular template based on signals gathered during the interview:
Siuple allster ndetemel ererence mterial)uenthe flat teuelate.
- More complex skalls (& 4 steps, branching, or supporting material) use the modular template with references/" and explicit load triggers.
熱，Ratlooale
This keeps the output lean for simple stalls while still supporting larger, more structured skill packages where progressive disclosure is important:
wrade-ofs
The logic for template selection is slightly more complex, but it avoids over-engineering simple skills.
## Decision 4: Treat "skill-review as a required prerequisite for the validation phase the Decision
世t.Bat onale
## Consequences
---
The skill assumes that the skill-review package is present in the workspace or repository and installed locally before the formal validation phase runs.
The validation Loop is a key part of the workflow, Without skill-review", the protocol would not be able to verify the generated skill against the repo's standards.
The skill should document this prerequisite clearly and should fail gracefully when skill-review is unavallable.
#* Decision 5: Make the workflow explicit and reviewable
熱.Decdsdon
The workflow is split into numbered steps with decision points, a pre-flight micro-check, and a formal audit hoop, 

## Decision 5: Make the workflow explicit and reviewable
### Decision
The workflow is split into numbered steps with decision points, a pre-flight micro-check, and a formal audit loop.

Rationale
READMEmd,
Find
This makes the skill easier for another agent or a human reviewer to follow. It also aligns with the "skill-review rubric's emphasis on procedural clarity and val #* Trade-offs
The skill is more prescriptive than a simple scaffold, but that is intentional - the goal is quality and consistency, not convenience alone.
n 

## Alternatives Considered
/ Alternative 1
Reason rejected |
A separate agent + skill pair | More moving parts than needed for the initial use case | I A single monolithic template for every skill | Too rigid for simple vs complex workflows I
I No formal skill-review dependency | Would weaken the quality bar and make the workflow less aligned with the repo's conventions |
===
懋
*Consequences
This design produces a skill that is:
      ⁃     ﻿casy,to use
      ⁃     ﻿﻿tightly integrated with the repository's existing quality tooling
      ⁃     ﻿﻿adaptive to the complexity of the idea being created
      ⁃     ﻿﻿explicit about prerequisites and validation expectations
It also makes the "zac-skill-create" skill itself easier to maintain, because its architecture is grounded in the same rubric it is meant to enforce.
