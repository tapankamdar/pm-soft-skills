---
description: PM meetings help — run meetings, decisions, stakeholder alignment
argument-hint: [meeting or decision you're preparing for]
---

Load the `meetings-decisions` skill and follow its workflow.

If the user provided arguments, treat $ARGUMENTS as the initial description of the meeting or decision situation and use that to pre-answer Question 1 in the AskUserQuestion workflow. Still ask the remaining questions before proceeding.

If no arguments were provided, start directly with the AskUserQuestion workflow from the skill.
