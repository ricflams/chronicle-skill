# Using Chronicle

**Keep AI collaboration alive across weeks, months, and team handoffs**

---

## What is Chronicle?

Chronicle is a documentation system that makes AI-assisted projects remember their own story. It's not just another folder of docs - it's the **source of truth** that lets you (or anyone else) pick up where you left off, even months later.

Think of it as a project journal that Claude actually reads and understands.

---

## Three Purposes in Action

### 1. Organize Tasks

**Before chronicle:**
- "Uh, what was I working on again?"
- Scattered TODOs in code comments and scratch files
- No clear priority or blocking relationships

**With chronicle:**
- Check `.chronicle/active-tasks.md` - instant work queue
- Tasks organized: In Progress, Ready, Blocked, Backlog
- Clear what to work on next, what's blocking what

### 2. Document the Journey

**Before chronicle:**
- "Why did we decide to use X instead of Y?"
- "Did we try this approach already? What happened?"
- Lost context between sessions, repeated mistakes

**With chronicle:**
- `.chronicle/context/decisions/` - Every major decision documented
- `.chronicle/journey/lessons.md` - What failed, what worked, what we learned
- `.chronicle/journey/session-log.md` - Detailed narrative of progress

### 3. Preserve AI Context

**Before chronicle:**
- Every session starts: "So this is a web app that does X..."
- 20 minutes explaining before productive work begins
- Claude forgets important constraints and decisions

**With chronicle:**
- Claude reads `.chronicle/` automatically
- Immediately knows project scope, constraints, recent work
- Starts productive work in minutes, not hours

---

## Common Workflows

### Starting Your Day

```
You: "List tasks" or "What should I work on?"
Claude: [Scans tasks/ folder]
        "You have 11 active tasks:
         0001: Complete SKILL.md implementation (Richard)
         0002: Create template files (Richard)
         ..."
        "Suggest starting with 0001?"
```

### During Work

When you make a significant decision:
```
You: "We're going with PostgreSQL instead of MongoDB"
Claude: "I'll document that decision. What was the rationale?"
        [Creates ADR in .chronicle/context/decisions/]
```

When something fails:
```
You: "This approach didn't work - circular dependency issue"
Claude: [Logs in .chronicle/journey/lessons.md]
        "Documented. Want to try a different approach?"
```

### Ending Your Session

```
You: "Update chronicle"
Claude: [Runs 7-step session end protocol]
        1. Summarizes what we accomplished
        2. Updates session-log.md with details
        3. Moves completed tasks to archive
        4. Creates ADRs for decisions made
        5. Updates diagrams if needed
        6. Documents problems/learnings
        7. Checks if compression needed (weekly)
```

### Returning After a Break

```
You: "I haven't touched this in 2 months, what's the status?"
Claude: [Reads .chronicle/project-truth.md and recent session-log]
        "This is [project description]. Last session you completed X and Y.
         Active tasks: [lists from tasks/ folder]. Most recent decision was [summary].
         Ready to continue?"
```

### Team Handoff

```
New person: "I'm taking over this project"
Claude: "Read .chronicle/project-truth.md (25min), then list tasks
         to see current work. Come back with questions."
         
[45 minutes later]
New person: "Okay, I understand the scope and current state"
Claude: "Great! Let's continue with the highest priority task..."
```

---

## File Structure Quick Reference

```
.chronicle/
├── project-truth.md       # WHAT & WHY: Scope, context, key decisions
├── tasks/                 # WHAT'S NEXT: Active tasks (one file per task)
│   ├── 0001-task-name.md
│   └── 0002-other-task.md
├── context/
│   ├── visuals/          # Diagrams, sketches, photos
│   └── decisions/        # ADRs (Architectural Decision Records)
├── journey/
│   ├── session-log.md    # WHAT HAPPENED: Detailed narrative
│   ├── completed-tasks/  # Completed task files (archive, not in AI context)
│   └── lessons.md        # Problems, experiments, learnings
└── execution/
    ├── parts-manifest.md # Components/materials/deliverables
    ├── key-patterns.md   # Recurring techniques
    ├── key-facts.md      # Config, URLs, reference data
    └── validation-strategy.md # Testing/acceptance criteria
```

---

## Common Phrases (Cheat Sheet)

**Task Management:**
- "List tasks" / "Show tasks"
- "What should I work on?"
- "Create task: [description]" (from planning mode: "Add this task")
- "Mark [task name] complete" / "[Task] is complete"

**Documentation:**
- "Document this decision"
- "Log this problem"
- "Update chronicle" (session end)

**Context:**
- "What's the current status?"
- "Why did we choose X?"
- "Have we tried this before?"
- "Show me recent progress"

**Navigation:**
- "Show me active tasks"
- "What decisions were made?"
- "What problems have we encountered?"

---

## When Chronicle Shines

✅ **Long-running projects** (weeks to months)
✅ **Complex decision-making** (need to remember why)
✅ **Team handoffs** (onboard new people quickly)
✅ **Learning from failures** (don't repeat mistakes)
✅ **AI-assisted development** (preserve context across sessions)

---

## When Chronicle is Overkill

❌ **Quick scripts** (< 1 day of work)
❌ **Throwaway prototypes** (not meant to last)
❌ **Solo one-off tasks** (no continuity needed)

---

## Best Practices

### 1. Update at Session End
Don't wait! Say "update chronicle" when you stop working. Fresh memory = better documentation.

### 2. Document Decisions When Made
Not later. Capture rationale while it's clear. Use: "Document this decision: [what] because [why]"

### 3. Log Failures Immediately
When something doesn't work, log it: "Log problem: [approach] failed because [reason]"

### 4. Keep active-tasks.md Current
Review weekly. Archive completed tasks. Add new ones as they emerge.

### 5. Compress Session Log Weekly
After 7+ days, say "compress session log". Moves key info to project-truth.md, archives details.

---

## Tips & Tricks

**Reading time optimization:**
- project-truth.md: 25 min (comprehensive context)
- active-tasks.md: 2 min (current state)
- Recent session-log: 10 min (what happened lately)
- **Total onboarding: ~45 minutes** (vs hours of code diving)

**Context window efficiency:**
- completed-tasks.md is excluded from AI context (humans only)
- Keeps Claude focused on relevant information
- Weekly compression prevents session-log bloat

**Decision records are searchable:**
```
You: "Why did we choose MongoDB?"
Claude: [Searches .chronicle/context/decisions/]
        "See ADR-004: We chose MongoDB because [rationale]"
```

---

## Troubleshooting

**"Claude isn't reading chronicle files"**
→ Check that CLAUDE.md lists files correctly in "Always in context" section

**"Too much duplication between files"**
→ Each fact should live in ONE place. Use references/links to avoid copying.

**"session-log.md is getting huge"**
→ Run weekly compression: "compress session log"

**"Don't know where to document something"**
→ Ask: "Where should I document [X]?" Claude knows the structure.

---

## Philosophy

In AI-assisted development, **documentation becomes the primary artifact**. Code can be regenerated from good context. Context cannot be regenerated from code alone.

Chronicle treats documentation as the source of truth. From `.chronicle/` alone, someone should be able to:
1. Understand what you're building and why
2. See what's been tried and what worked
3. Know what to work on next
4. Continue building effectively

**This is regenerative documentation** - it grows with your project and preserves what matters.

---

## Getting Help

**Within a session:**
- "How do I [task] using chronicle?"
- "Show me an example of [workflow]"

**For complex questions:**
- Read the relevant file in `.chronicle/` first
- Check recent session-log for similar situations
- Ask Claude with context: "In our chronicle system, how should I..."

---

## Next Steps

1. **Start using it** - Say "What should I work on?"
2. **End sessions properly** - Say "Update chronicle" when you stop
3. **Document as you go** - Decisions, problems, learnings - capture them fresh
4. **Review weekly** - Check active-tasks.md, compress session-log if needed

Chronicle gets more valuable the more you use it. The earlier you start, the better your project's memory becomes.

---

*This guide lives at project root alongside CLAUDE.md. It's for humans - CLAUDE.md is for AI.*
