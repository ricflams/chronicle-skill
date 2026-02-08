# Using Chronicle

**Team-shared institutional memory for your project**

---

## What is Chronicle?

Chronicle captures your project's decision history, learned lessons, and evolution in git-tracked markdown files. It provides what Claude Memory doesn't: **structured, searchable, team-shared** understanding that works independently of any individual developer or AI session.

**Philosophy:** *Decisions are timeless, lessons fade, sessions are ephemeral.*

---

## What Chronicle is NOT

- **Not for task management** → Use Claude Tasks for this
- **Not for AI context preservation** → Claude Memory handles personal continuity
- **Not a replacement for git** → Complements commits with rationale and understanding

---

## File Structure

```
.chronicle/
├── truth.md              # Project DNA (purpose, scope, constraints)
├── principles.md         # Enduring beliefs that guide decisions
├── decisions/            # YYYYMMDD-HHMM-slug.md (ADRs, never archived)
├── lessons/              # YYYYMMDD-HHMM-slug.md (failures & insights, 60-day retention)
├── sessions/             # YYYYMMDD-HHMM-slug.md (narrative timeline, 14-day retention)
└── archive/
    ├── lessons/          # Old lessons (auto-archived monthly)
    └── sessions/         # Old sessions (auto-archived weekly)
```

**All files named:** `YYYYMMDD-HHMM-slug.md` (example: `20260208-1430-postgres-indexing.md`)

---

## Common Workflows

### Team Onboarding (New Member Joins)

**Reading order:**
1. `truth.md` - What is this project? (~5 min)
2. `principles.md` - How do we make decisions? (~3 min)
3. Recent `decisions/` - What have we chosen? (scan directory, ~5 min)
4. Recent `lessons/` - What should we avoid? (scan directory, ~5 min)

**Total: ~20 minutes to understand project context**

### During Work

**When making a significant decision:**
```
You: "We're going with PostgreSQL instead of MongoDB"
Claude: "This seems significant. Should I create an ADR?"
You: "Yes"
Claude: [Creates .chronicle/decisions/20260208-1430-database-choice.md]
```

**When something fails or surprises:**
```
You: "This approach didn't work - got circular dependency"
Claude: "Should I log this as a lesson?"
You: "Yes"
Claude: [Creates .chronicle/lessons/20260208-1430-circular-dependency.md]
```

**When a principle emerges:**
```
You: "We always choose simplicity over configurability"
Claude: "Added principle: 'Choose simplicity over configurability'. 
         Say 'that's not a principle' to undo."
```

### At Session End

```
You: "Let's wrap up"
Claude: "Should I log this session?"
You: "Yes"
Claude: [Creates .chronicle/sessions/20260208-1430-component-refactor.md
         with summary of work, changes, and next steps]
```

### Returning After Time Away

```
You: "I haven't touched this in 2 months, what's the status?"
Claude: [Reads truth.md, principles.md, recent sessions/]
        "This is [project description]. Recent work: [summary from sessions].
         Latest principle: [X]. Ready to continue?"
```

---

## How Archival Works (Automatic)

Chronicle automatically keeps folders bounded:

**Every Monday (or when files >21 days exist):**
- Sessions older than 14 days → moved to `archive/sessions/`

**1st of each month (or when files >90 days exist):**
- Lessons older than 60 days → moved to `archive/lessons/`

**Decisions never archive** (they're timeless).

You'll see: "Archived 3 sessions and 1 lesson. Undo: git checkout if needed."

---

## When to Create Each Type

| Type | When | Example |
|------|------|---------|
| **ADR** (decision) | Significant choice with alternatives considered | Database selection, architecture approach, tech stack choice |
| **Lesson** | Something fails, surprises, or teaches | Performance gotcha, deployment issue, experiment result |
| **Principle** | Pattern emerges across multiple decisions | "We prefer composition over inheritance" (after 3rd instance) |
| **Session** | After substantive work (Claude prompts) | Daily/weekly work summary for team context |

---

## Best Practices

### 1. Let Claude Capture Organically
Don't force documentation. Claude suggests ADRs/lessons when appropriate. Confirm or skip.

### 2. Keep truth.md Current
When scope changes, constraints shift, or risks emerge, update truth.md. It's the starting point for anyone (human or AI) engaging with the project.

### 3. Articulate Tradeoffs
Every principle should state what you accept by following it.  
Every decision should state what becomes harder.

### 4. Trust Archival
Let old sessions/lessons move to archive/. They're still in git if you need them. Active folders stay scannable.

### 5. Scan Before Deep Work
Before tackling a complex area, ask: "Are there lessons about [database/performance/deployment]?" Claude will check tags and load relevant context.

---

## Team Collaboration

**Multiple people working same day?**
- Timestamped files avoid collisions: `20260208-0930-alice-api-work.md` vs `20260208-1400-bob-ui-refactor.md`

**Archival conflicts?**
- Deterministic calendar-based rules mean everyone archives at same times
- If both Alice and Bob work on March 1st, both move same February files → no conflicts

**Shared principles?**
- principles.md is git-tracked
- Changes go through normal PR review
- Keeps team aligned on values

---

## Token Efficiency

Chronicle is designed for minimal token overhead:

**Always loaded (~2.5K tokens):**
- truth.md (~1500-2000 tokens)
- principles.md (~700-1000 tokens)

**Selectively loaded (~4K tokens):**
- Recent lesson frontmatter (scan to find relevant)
- Recent session frontmatter (scan for context)
- Full ADRs/lessons only when relevant

**Total: ~7K tokens for full selective context** (vs loading all files)

---

## Common Questions

**"Where should I document [X]?"**
Ask Claude. It knows the structure.

**"Can I edit these files manually?"**
Yes! They're just markdown. Edit in any text editor.

**"What if I want to undo an auto-added principle?"**
Say "that's not a principle" immediately, or just delete it from principles.md.

**"Do I need to compress anything?"**
No. Archival is automatic. truth.md and principles.md grow slowly and compress when needed.

---

## Philosophy

Chronicle treats **understanding as more valuable than artifacts**. Code can be regenerated from good context. Context cannot be regenerated from code alone.

From `.chronicle/` alone, a new team member (or future you) should be able to:
1. Understand what you're building and why
2. Know what's been tried and what worked
3. See what principles guide decisions
4. Continue effectively without repeating past mistakes

This is **institutional memory** - knowledge that outlives individual contributors and persists across team changes.

---

## Getting Help

**During work:**
- "How should I document this decision?"
- "Is there a lesson about [X]?"
- "Show me recent decisions"

**For team handoffs:**
- "Help me onboard to this project" → Claude guides through truth.md, principles, recent work

---

## Next Steps

1. **Read truth.md** - Understand the project
2. **Skim principles.md** - Know how decisions are made
3. **Check recent lessons** - Avoid known pitfalls  
4. **Start working** - Chronicle captures as you go

Chronicle gets more valuable with use. The earlier your team adopts it, the richer your institutional memory becomes.

---

*This guide is for humans. CLAUDE.md contains the protocols that Claude follows automatically.*
