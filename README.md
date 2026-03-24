# PM Soft Skills Plugin

Practical guidance for the recurring tasks every product manager faces. Each skill distills the frameworks, principles, and hard-won lessons from Tapan Kamdar's writing — built to teach the *why* behind the move, not just the format.

**Source material:**
- *Building Blocks* newsletter (100+ posts, 2024–present)
- *That's What Makes a Great PM* series (2025)
- *AI Force Multiplier* series (2025)
- *Level Up: From Good Product Manager to Great Product Manager* (book, 2026)

---

## Installation

### Claude Cowork (recommended for non-developers)
1. Open **Customize** (bottom-left corner)
2. Go to **Browse plugins → Personal → +**
3. Select **Add marketplace from GitHub**
4. Enter: `tapankamdar/pm-soft-skills`

All 7 skills and commands install automatically.

### Claude Code (CLI)

```bash
# Step 1: Add the marketplace
claude plugin marketplace add tapankamdar/pm-soft-skills

# Step 2: Install the plugin
claude plugin install pm-soft-skills@pm-soft-skills
```

### Other AI assistants (skills only)

The `skills/*/SKILL.md` files follow the universal skill format and work with any tool that reads it. Commands (`/pm-writing`, `/pm-planning`, etc.) are Claude-specific.

| Tool | How to use | What works |
|---|---|---|
| GitHub Copilot | Copy `.github/` folder to your project root | Prompts + Instructions |
| Gemini CLI | Copy skill folders to `~/.gemini/skills/` | Skills only |
| OpenCode | Copy skill folders to `.opencode/skills/` | Skills only |
| Cursor | Copy skill folders to `.cursor/skills/` | Skills only |
| Kiro | Copy skill folders to `.kiro/skills/` | Skills only |

```bash
# Example: copy all skills for OpenCode (project-level)
cp -r skills/* .opencode/skills/

# Example: copy all skills for Gemini CLI (global)
cp -r skills/* ~/.gemini/skills/
```

### GitHub Copilot (VS Code / GitHub.com)

1. Copy the `.github/` folder into your project root
2. Open Copilot Chat in VS Code
3. Type `#` and select any `pm-*` prompt to start coaching

See [GITHUB-COPILOT-SETUP.md](GITHUB-COPILOT-SETUP.md) for full details.

---

## Skills & Commands

7 skills covering the recurring tasks every PM faces. Each skill can be triggered naturally in conversation or via a slash command.

---

### 1. Writing & Docs (`/pm-writing`)

For when you need to write something that lands — a status update your manager actually reads, a PRD that gets approved, or a message to leadership that builds trust.

**References:** Write a status update · Write a PRD · Manage up

**Natural language triggers:**
- "write a status update", "weekly update", "status report"
- "write a PRD", "feature spec", "product requirement"
- "manage up", "communicate with my manager", "my manager doesn't read my updates"

**Examples:**

> *"Help me write a status update for my engineering team. We hit our sprint goal but had a major production incident mid-week."*

> *"I need to write a PRD for a notification preferences feature. Users are complaining about too many emails."*

> `/pm-writing My manager never reads my updates and I need to change that`

---

### 2. Communication & Influence (`/pm-influence`)

For when you need to translate a complex idea for a non-technical audience, sell a roadmap change to skeptical stakeholders, or rebuild trust after something went wrong.

**References:** Translate across audiences · Simplify for clarity · Sell vision and ideas · Influence through storytelling · Earn trust under pressure

**Natural language triggers:**
- "how do I explain this to the CEO", "translate for executives"
- "how do I sell this idea", "get buy-in", "influence without authority"
- "we missed a deadline and I need to communicate it", "earn back trust"

**Examples:**

> *"I need to explain why we're pausing our mobile app rewrite to our CEO. She's not technical and will be frustrated."*

> *"Help me use storytelling to get my eng team excited about a compliance project nobody wants to work on."*

> `/pm-influence I need to convince the VP of Sales to deprioritize a feature their top customer is asking for`

---

### 3. Planning & Strategy (`/pm-planning`)

For when you need to set goals, build a product vision, prioritize the roadmap, or figure out why your team keeps missing.

**References:** Set quarterly goals · Build a product vision · Prioritize the roadmap · Craft a product narrative · Fix the system

**Natural language triggers:**
- "set goals", "OKRs", "quarterly planning"
- "product vision", "vision doc", "strategy pitch"
- "prioritize", "say no", "roadmap debate", "too many priorities"
- "team keeps missing goals", "fix our process"

**Examples:**

> *"Help me set OKRs for Q2. Our company goal is to improve retention, and my team owns the onboarding experience."*

> *"I need to build a product narrative for a feature nobody on the leadership team is excited about."*

> `/pm-planning We have 40 things on our roadmap and need to cut it in half before planning week`

---

### 4. Meetings & Decisions (`/pm-meetings`)

For when a decision needs to happen and a meeting is involved — running it well, aligning people before it, or making the call when the team is stuck.

**References:** Run a productive meeting · Pre-align stakeholders · Facilitate team decisions · Make a product decision

**Natural language triggers:**
- "run a meeting", "meeting keeps going in circles"
- "stakeholder alignment", "pre-align", "get buy-in before the meeting"
- "team can't agree", "facilitate a decision", "help the team decide"
- "make a product decision", "build vs. buy"

**Examples:**

> *"I have a roadmap review with 8 stakeholders on Friday and I want it to be decisive, not a debate."*

> *"My team has been going back and forth on whether to build our own auth system or use a third-party. Help me make the call."*

> `/pm-meetings I need to pre-align my VP before a big meeting where I'm proposing we kill a feature`

---

### 5. People & Feedback (`/pm-people`)

For the people work: running effective 1:1s, delivering hard feedback, writing performance reviews, and giving your team real ownership.

**References:** Run 1:1s · Give feedback · Write a performance review · Delegate with ownership

**Natural language triggers:**
- "prepare for a 1:1", "1:1 isn't working", "what to talk about in 1:1"
- "give feedback", "difficult feedback", "how to deliver hard feedback"
- "write a perf review", "performance review", "calibration"
- "delegate", "team doesn't take ownership", "stop being the bottleneck"

**Examples:**

> *"I need to give feedback to a designer who keeps missing deadlines and gets defensive when I bring it up."*

> *"Help me write a strong performance review for an engineer who's technically great but struggles with cross-functional communication."*

> `/pm-people I want to give my PM more ownership over sprint planning but I'm not sure how to hand it off`

---

### 6. Team Leadership (`/pm-leadership`)

For when the issue is with the team itself — energy is low, urgency is missing, you need to show up with executive presence, or you're hiring and onboarding.

**References:** Sustain team energy · Build executive presence · Hire and onboard

**Natural language triggers:**
- "team is slow", "team lacks urgency", "team energy is low", "team is burned out"
- "executive presence", "show up with confidence", "calm under pressure"
- "hire a PM", "onboard a new PM", "attract great people"

**Examples:**

> *"My team has been heads-down on a long infrastructure project for 3 months and morale is tanking. What do I do?"*

> *"I have a presentation to the board next week and I want to show up with more executive presence."*

> `/pm-leadership I'm onboarding a new senior PM who's joining from a startup and I want to set them up well`

---

### 7. Research & Discovery (`/pm-research`)

For when you have research and need to know what it means — synthesizing interviews, finding patterns in feedback, or asking better questions in the first place.

**References:** Synthesize research · Ask better questions

**Natural language triggers:**
- "synthesize research", "user interviews", "make sense of feedback"
- "what do users actually want", "themes in feedback"
- "how to ask better questions", "lead with curiosity"

**Examples:**

> *"I have notes from 8 user interviews about why people churn in month 2. Help me find the real patterns."*

> *"I'm running discovery interviews next week for a new B2B feature. What questions should I be asking?"*

> `/pm-research Here are my interview notes from 6 enterprise customers — synthesize the key themes and what we should do`

---

## How to extend this plugin

**Add a skill to an existing theme:**
1. Create a new `.md` file in the theme's `references/` folder using the same structure as existing files.
2. Add a row to the skills table in that theme's `SKILL.md`.

**Add a new theme:**
1. Create a new folder under `skills/` (e.g., `skills/hiring-onboarding/`).
2. Add a `SKILL.md` and a `references/` subfolder.
3. Add skill files to `references/` and update the table in `SKILL.md`.
4. Add the theme to this README.

---

## About the author

Tapan Kamdar is a product leader with 15+ years at Meta, Mozilla, GoDaddy, eBay, and Yahoo. He writes the *Building Blocks* newsletter at [linkedin.com/newsletters/7167660111300157440](https://www.linkedin.com/newsletters/7167660111300157440/) and is the author of *Level Up: From Good Product Manager to Great Product Manager* ([a.co/d/0dxmUyJJ](https://a.co/d/0dxmUyJJ)).
