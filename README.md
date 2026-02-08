# Chronicle


Chronicle captures the **context gems** — truths, decisions, lessons — from each Claude session and tucks them into **markdown files** right in your repo.

This means every new conversation starts with everything you've already figured out. Claude's built-in memory eventually scrolls out of the context window while Chronicle's markdown-captured context sticks around.

What's in it for you? First, **context that keeps building** — Claude gets genuinely smarter about your project over time. Second, a living record of your project's journey stored in your repo: the truths you've nailed down, the decisions you've made, the lessons you've learned. It grows organically as you work.

And don't worry about **bloat** — Chronicle is smart about tokens. It only passes in the most relevant parts of your journey, archiving the rest as time goes by. Your context stays lean even as your project history grows.

Think of Chronicle as **Claude's sidekick for context** — it keeps tabs on the important project-stuff and feeds it back into your conversations, making Claude smarter about your project with every session. All just stored as markdown-files in a `.chronicle` folder.

---

## Quick Start

**Install:**
```bash
claude skill add https://github.com/ricflams/chronicle-skill
```

**Use:**
```bash
cd ~/my-project
claude
```
```
You: "use Chronicle"
```

That's it. Chronicle initializes, then runs automatically — prompting you when decisions, lessons, or sessions are worth capturing.

You can invoke Chronicle in fresh projects or in existing projects. Either works just fine.

---

## What You Get

```
.chronicle/
├── truth.md              # Project DNA (purpose, scope, constraints)
├── principles.md         # Enduring beliefs that guide decisions
├── decisions/            # YYYYMMDD-HHMM-slug.md (ADRs, never archived)
├── lessons/              # YYYYMMDD-HHMM-slug.md (failures & insights, 60-day retention)
├── sessions/             # YYYYMMDD-HHMM-slug.md (timeline, 14-day retention)
└── archive/
    ├── lessons/          # Auto-archived monthly
    └── sessions/         # Auto-archived weekly
```

Plus:
- Protocols in `CLAUDE.md` (~90 lines)
- User guide in `USING-CHRONICLE.md`
- All files git-tracked and human-readable

---

## What Chronicle Does

✅ **Decision trail** - ADRs with rationale preserved  
✅ **Lessons learned** - Structured failure documentation  
✅ **Session narrative** - Timeline of project evolution  
✅ **Project truth** - Purpose, scope, constraints, risks  

## What Chronicle Does NOT Do

❌ **Task management** → Use Claude Tasks  
❌ **AI context preservation** → Use Claude Memory  
❌ **Replace git commits** → Complements with rationale

---

## Use Cases

**Team Projects**
- Shared decision history visible to all
- Onboarding new members
- Enriched project context from your coworkers

**Long-Running Projects**
- Git-tracked evolution over months/years
- Decision archaeology ("why did we choose X?")
- Learning from documented failures

**Solo Projects** *(when useful)*
- Future you needs context after 6 months
- Want git-trackable decision history
- Planning to hand off eventually

---

## How It Works

Chronicle runs automatically once initialized:

- **Decisions captured** when significant choices are made
- **Lessons logged** when failures or surprises occur
- **Principles added** when patterns emerge across decisions
- **Sessions archived** weekly, lessons monthly (deterministic, conflict-free)
- **Everything** git-tracked and human-readable

---

## Philosophy

Chronicle treats *understanding the journey* as just as valuable than the actual produced code and artifacts. 

Code can be regenerated from good context. Let's keep that around.

**From `.chronicle/` alone, a new team member should be able to:**
1. Understand what you're building and why
2. Know what's been tried and what worked
3. See what principles guide decisions
4. Continue effectively without repeating past mistakes

This is **institutional memory** - knowledge that outlives individual contributors and persists across team changes.

---

## Features

✅ **Team-first** - Git-tracked, human-readable, works without Claude  
✅ **Structured** - ADRs for decisions, lessons for failures, principles for patterns  
✅ **Automatic** - Calendar-based archival, no manual intervention  
✅ **Conflict-free** - Timestamped files (YYYYMMDD-HHMM-slug.md), deterministic rules  
✅ **Token-efficient** - Always-load core ~2.5K tokens, selective ~7K total  
✅ **Transparent** - All markdown files, directly editable

---

## Skill Structure

```
chronicle-skill/
├── SKILL.md                    # Skill definition for Claude CLI
├── USING-CHRONICLE.md          # User guide (also created in projects)
└── templates/
    ├── truth-template.md       # Project DNA template
    ├── principles-template.md  # Principles format
    ├── decision-template.md    # ADR template
    ├── lesson-template.md      # Lesson format
    ├── session-template.md     # Session log format
    └── claude-template.md      # CLAUDE.md protocols
```

---

## Epilogue

### Documentation

- **[SKILL.md](chronicle-skill/SKILL.md)** - Complete skill definition
- **[USING-CHRONICLE.md](chronicle-skill/USING-CHRONICLE.md)** - Detailed usage guide

### Contributing

Contributions welcome! Please open an issue to discuss proposed changes.


### License

MIT

### Author

Richard Flamsholt
richard@flamsholt.dk
