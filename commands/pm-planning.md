---
description: PM planning help — goals, vision, roadmap, strategy
argument-hint: [what you're planning]
---

Load the `planning-strategy` skill and follow its workflow.

If the user provided arguments, treat $ARGUMENTS as the initial description of their planning task and use that to pre-answer Question 1 in the AskUserQuestion workflow. Still ask the remaining questions before proceeding.

If no arguments were provided, start directly with the AskUserQuestion workflow from the skill.
