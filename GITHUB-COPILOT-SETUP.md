# Adding GitHub Copilot Support to PM Soft Skills

## Overview

Your `pm-soft-skills` plugin currently supports Claude Code, Gemini CLI, OpenCode, Cursor, and Kiro. This guide explains how to add **native GitHub Copilot** support so your skills work seamlessly in VS Code, GitHub.com, and other Copilot-enabled environments.

GitHub Copilot uses two mechanisms:
1. **Custom Instructions** (`.github/copilot-instructions.md`) — global behavior rules applied to all Copilot interactions in a repo
2. **Prompt Files** (`.github/prompts/*.prompt.md`) — reusable prompt templates users can invoke in Copilot Chat

## Architecture Mapping

| Claude Code Concept | GitHub Copilot Equivalent | Location |
|---|---|---|
| `skills/*/SKILL.md` | Prompt files (`.prompt.md`) | `.github/prompts/` |
| `commands/*.md` | Same prompt files (entry points) | `.github/prompts/` |
| `.claude-plugin/` | Not needed | N/A |
| `references/*.md` | Embedded in prompt files or stored as separate files | `.github/prompts/` or repo root |

## Step-by-Step Implementation

### Step 1: Create the `.github/prompts/` directory

```bash
mkdir -p .github/prompts
```

### Step 2: Create prompt files for each skill

Create one `.prompt.md` file per skill. Each file has:
- YAML frontmatter with a `description` field
- The full coaching instructions, context questions, and frameworks

**Example: `.github/prompts/pm-writing.prompt.md`**

```markdown
---
description: "PM writing coach — status updates, PRDs, managing up"
---

# PM Writing & Documents

You are a PM writing coach. Your guidance draws on Tapan Kamdar's Building Blocks newsletter and Level Up book.

## Core Principle
Great PMs write documents that drive decisions — not just awareness.

## Before You Start — Gather Context
Ask these questions:
1. What are you trying to write? (Status update, PRD, Message to leadership)
2. Who is the primary reader?
3. What's the main challenge?

## Frameworks
[Embed the content from your references/*.md files here]

---
*Based on [PM Soft Skills](https://github.com/tapankamdar/pm-soft-skills) by Tapan Kamdar*
```

Repeat for all 7 skills: pm-writing, pm-influence, pm-planning, pm-meetings, pm-people, pm-leadership, pm-research.

### Step 3: Create global instructions (optional)

Create `.github/copilot-instructions.md` with:
- An overview of available prompts
- General PM coaching principles that apply across all skills

### Step 4: Update README.md

Add a GitHub Copilot section to your installation table:

```markdown
| GitHub Copilot | Clone repo or copy `.github/` folder to your project | Prompts + Instructions |
```

And add installation instructions:

```markdown
### GitHub Copilot (VS Code / GitHub.com)

1. Copy the `.github/` folder into your project root
2. Open Copilot Chat in VS Code
3. Type `#` and select any `pm-*` prompt to start coaching

Or clone this repo and use it directly:

```bash
git clone https://github.com/tapankamdar/pm-soft-skills.git
cd pm-soft-skills
# Open in VS Code — prompts are available immediately in Copilot Chat
```
```

### Step 5: Prompt file design tips

**Self-contained vs. referencing files:**
- GitHub Copilot prompt files work best when they are self-contained
- Unlike Claude Code where skills can reference separate files at runtime, Copilot prompt files should embed the framework content directly
- You can use `#file:path` syntax in prompt files to reference other files, but embedding is more reliable

**Size considerations:**
- Each prompt file can be quite large (4-8KB is fine)
- The total content of all referenced files plus the prompt itself should stay under ~32K tokens for best results

**Frontmatter fields:**
- `description` (required): Short description shown in the prompt picker
- `mode` (optional): Can be `agent` for agentic behavior or omitted for standard chat

## File Structure After Changes

```
pm-soft-skills/
├── .github/
│   ├── copilot-instructions.md          # Global Copilot instructions
│   └── prompts/
│       ├── pm-writing.prompt.md         # Writing & Docs
│       ├── pm-influence.prompt.md       # Communication & Influence
│       ├── pm-planning.prompt.md        # Planning & Strategy
│       ├── pm-meetings.prompt.md        # Meetings & Decisions
│       ├── pm-people.prompt.md          # People & Feedback
│       ├── pm-leadership.prompt.md      # Team Leadership
│       └── pm-research.prompt.md        # Research & Discovery
├── .claude-plugin/                      # Existing Claude support
├── skills/                              # Existing skills (shared source)
├── commands/                            # Existing Claude commands
└── README.md                            # Updated with Copilot instructions
```

## How Users Will Experience It

1. User opens their project in VS Code with the `.github/` folder present
2. Opens Copilot Chat (Ctrl+Shift+I or click the Copilot icon)
3. Types `#` to see available prompts
4. Selects `pm-writing` (or any other prompt)
5. Types their question: "Help me write a status update for my engineering team"
6. Copilot applies the full coaching framework automatically

## Converting Your Existing Skills

For each skill, the conversion process is:
1. Take the `SKILL.md` content (core principle, context questions, how to help)
2. Take all `references/*.md` content (frameworks, templates, examples)
3. Combine them into a single `.prompt.md` file
4. Add YAML frontmatter with a description

The key difference from Claude Code: in Copilot, everything needs to be in one file (or explicitly referenced with `#file:`), rather than dynamically loaded at runtime.

## Testing

1. Open VS Code with the repo
2. Open Copilot Chat
3. Type `#pm-writing` and ask: "Help me write a status update"
4. Verify the coaching framework is applied correctly
5. Repeat for all 7 prompts

---

*This guide was generated to help bring PM Soft Skills to the GitHub Copilot ecosystem. For questions, see the [GitHub Copilot custom instructions docs](https://docs.github.com/en/copilot/customizing-copilot/adding-repository-custom-instructions-for-github-copilot).*
