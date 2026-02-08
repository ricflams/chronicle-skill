---
name: chronicle-skill
description: "Structured institutional memory for teams. Chronicle captures decisions, lessons, and project understanding in git-tracked markdown - providing what Claude Memory doesn't: team-shared, searchable decision history."
---

# Chronicle: Institutional Memory for Teams

## Overview

**Philosophy:** *Decisions are timeless, lessons fade, sessions are ephemeral.*

Chronicle provides structured, team-shared institutional memory through:
- **Decision Trail** - Searchable history of why choices were made (ADRs)
- **Lessons Learned** - Structured failure documentation to avoid repeating mistakes
- **Session Narrative** - Timeline of project evolution for team context
- **Project Truth** - Compressed DNA capturing purpose, scope, constraints, and risks

Everything lives in git-tracked markdown files that work independently of Claude - enabling team handoffs, onboarding, compliance trails, and decision archaeology.

**What Chronicle is NOT:**
- Not for AI context preservation (Claude Memory handles this)
- Not for task management (Claude Tasks handles this)
- Not a replacement for git commits (complements them with rationale)

## Design Foundations

Chronicle builds on established methodologies:

**Architecture Decision Records (Michael Nygard, 2011)**
- 3-section ADR format: Context, Decision, Consequences
- Lightweight, focused on capturing rationale

**README-Driven Development (Tom Preston-Werner)**
- Start with understanding before implementation
- truth.md serves as project DNA

**Token Efficiency as Design Goal:**
- Individual files stay small (~200-400 tokens each)
- Selective loading via frontmatter scanning
- Always-load core: ~2.5K tokens (truth.md + principles.md)
- Full selective load: ~7K tokens total

## When to Use

Chronicle shines for:
- **Team projects** - Shared decision history visible to all, not locked in personal Claude Memory
- **Long-running projects** - Git-tracked evolution over months/years
- **Compliance/audit needs** - Explicit decision trail with rationale
- **Team handoffs & onboarding** - New members read truth.md → principles.md → recent decisions
- **Learning from failures** - Structured lessons prevent repeated mistakes

Chronicle may NOT be needed for:
- Solo projects where personal Claude Memory suffices
- Short-lived prototypes without team collaboration
- Projects where decisions don't need documentation

## Initialization

When `.chronicle/` doesn't exist, Chronicle offers setup on first engagement.

### Quick-Start (30 seconds)

1. Create `.chronicle/` structure
2. Generate `truth.md` from discoverable info (README, package files, code analysis)
3. Add TBD placeholders for unknown sections
4. Create empty `principles.md` with header
5. Create folders: `decisions/`, `lessons/`, `sessions/`, `archive/`
6. Append protocols to `CLAUDE.md`

truth.md enriches organically as work progresses through opportunistic documentation.

### Optional Deep Discovery

User can trigger deeper exploration: *"help me think through this project"*

Claude runs conversational interrogation with concrete examples:
- What's explicitly out of scope? (Eg: mobile apps, real-time sync, or enterprise SSO)
- What constraints matter most? (Eg: must run offline, zero dependencies, or <100ms latency)
- What could derail this? (Eg: API changes, regulatory requirements, or team availability)

Questions adapt based on project analysis (tech stack, README content, existing code).

**Adaptive logic:**
- Software projects: Add technical architecture questions
- Solo projects: Skip team questions
- Deadline projects: Add milestone questions
- No deadline: Focus on quality/learning

**Handling uncertainty:**
- One reframe attempt per question
- If still uncertain → mark as TBD, move on
- Don't overuse 5 Whys technique

**Summary & Validation (2-3 min):**
Show comprehensive summary, wait for user confirmation before creating files.

### Phase 2: Bootstrap Structure

## Structure

```
.chronicle/
├── truth.md              # Project DNA (~1500-2000 tokens)
├── principles.md         # Enduring beliefs (~700-1000 tokens, 20-25 max)
├── decisions/            # YYYYMMDD-HHMM-slug.md (never archived)
├── lessons/              # YYYYMMDD-HHMM-slug.md (60-day retention)
├── sessions/             # YYYYMMDD-HHMM-slug.md (14-day retention)
└── archive/
    ├── lessons/          # Auto-archived monthly (files >60 days)
    └── sessions/         # Auto-archived weekly (files >14 days)
```

**File naming:** `YYYYMMDD-HHMM-slug.md` (date-time-descriptor)
- Example: `20260208-1430-postgres-indexing.md`
- Benefits: No collisions, chronological sort, self-documenting

**Retention policy (automatic):**
- **decisions/** - Timeless, never archived
- **lessons/** - Archived 1st of month (>60 days old) OR hard cap >90 days
- **sessions/** - Archived every Monday (>14 days old) OR hard cap >21 days

**Token budget:**
- Always-load (truth.md + principles.md): ~2.5K tokens
- Full selective-load: ~7K tokens total

## Protocols Added to CLAUDE.md

Chronicle appends ~60 lines to CLAUDE.md covering:

### Context Loading
- **Always load:** truth.md, principles.md
- **On session start:** Scan lessons/ and sessions/ directories  
- **Before code changes:** Load lessons matching current work (by tags)
- **When deciding:** Scan decisions/ for related ADRs

### Principle Recognition
- **Auto-capture:** "We always...", "We never...", "From now on...", "As a rule..."
- **Notify:** "Added principle: [X]. Say 'that's not a principle' to undo."
- **Propose:** When pattern detected across 2+ decisions/lessons

### Session Logging
- Maintain running session file for current day
- Auto-append significant events (decisions, problems, direction changes)
- New file on date change or 4+ hour gap

### Archival (Automatic)
- Before writing to sessions/ or lessons/: check if archival due
- **Monday OR files >21 days:** Archive sessions >14 days → archive/sessions/
- **1st of month OR files >90 days:** Archive lessons >60 days → archive/lessons/
- Notify: "Archived N sessions and M lessons. Undo: git checkout if needed."

### Document Creation Triggers
- **ADR:** Significant decisions with alternatives considered
- **Lesson:** Something fails, surprises, or teaches
- **Session entry:** After substantive work, prompt: "Log this session?"

## How Chronicle Works in Practice

**First engagement:** Chronicle detects no `.chronicle/` directory, offers 30-second setup

**During work:**
- Claude auto-logs significant events to current session file
- Claude recognizes principle-worthy moments and auto-adds (with undo option)
- Claude suggests ADRs when major decisions are made
- Claude captures lessons when failures or surprises occur

**Archival happens automatically:** Files move based on calendar rules when Claude creates new content

**Team collaboration:** Everyone's Chronicle follows same deterministic rules → no merge conflicts

## File Templates

Templates in `chronicle-skill/templates/`:
- **truth.md** - Project DNA with TBD placeholders
- **principles.md** - Natural language principles with tradeoffs
- **decision-template.md** - 3-section ADR (Context, Decision, Consequences)
- **lesson-template.md** - Structured failure documentation
- **session-template.md** - Minimal narrative format
- **claude.md** - Full CLAUDE.md protocol section

## Key Principles

**Progressive disclosure:** truth.md starts thin, enriches organically as gaps become relevant

**Opportunistic documentation:** Claude captures context as it becomes relevant, not upfront

**Automatic archival:** Calendar-based rules ensure bounded growth without manual intervention

**Team-first:** Git-tracked, human-readable, works without Claude

**Timeless vs temporal:** Decisions never expire, lessons fade, sessions are ephemeral

