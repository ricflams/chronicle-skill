---
name: chronicle
description: "Initialize a comprehensive project documentation system where your project's history becomes its memory. Chronicle maintains task organization, journey documentation, and AI context preservation for seamless long-term collaboration."
version: 1.0.0
---

# Chronicle: The Complete Record of Your Project's Journey

## Overview

Chronicle creates a self-contained documentation system that enables:
- **Task Organization** - Never ask "what's next?"
- **Journey Documentation** - Capture why, not just what  
- **AI Context Preservation** - Enable seamless collaboration across sessions
- **Token Efficiency** - Lightweight, scannable formats optimized for LLM context

From the chronicle alone, someone - human or AI - should be able to understand your project well enough to continue building it effectively.

## Design Foundations

Chronicle builds on established methodologies:

**Architecture Decision Records (Michael Nygard, 2011)**
- Original 3-section ADR format: Context, Decision, Consequences
- Chronicle adds two-tier system: quick Y-statements + full ADRs for major decisions

**PARA Method (Tiago Forte)**
- Purpose, Areas, Resources, Archives organization model
- Chronicle's 4-layer structure aligns: Purpose (project-truth + tasks), Resources (context), Archives (journey), System (execution)

**README-Driven Development (Tom Preston-Werner)**
- Start with the story before implementation
- Chronicle's project-truth.md serves this role

**Just-Enough Architecture (Simon Brown)**
- Document what matters, skip what doesn't
- Chronicle balances comprehensive context with token efficiency

**Conventional Commits**
- Structured commit format for semantic meaning
- Chronicle applies to session logs: `feat(scope): description`

**Token Efficiency as Design Goal:**
Chronicle is optimized for LLM collaboration with two-tier context loading, compressed formats, and explicit token budgets (typical project ~10K tokens vs traditional documentation ~40K+).

## When to Use

Use chronicle for:
- Long-running AI-assisted projects
- Projects with extended breaks between sessions
- Complex builds (software, DIY, presentations, creative work)
- Team handoffs and onboarding
- Learning from past decisions and failures

## Initialization Command

```
"Initialize chronicle"
"Set up chronicle for this project"
```

## How It Works

### Phase 1: Comprehensive Questioning (15-28 minutes)

**Foundation Questions (3-5 min):**
Ask 10 core questions with compressed examples:

1. What is this project? (1 sentence)
2. Why does it exist? What job is it hired to do?
3. Who will use/benefit from it?
4. What does success look like? (concrete outcomes)
5. What should this NOT do? (non-goals)
6. Key constraints? (technical, time, budget)
7. Timeline and urgency?
8. Solo, team, or organization?
9. Similar to anything you've built? (analogies)
10. Riskiest assumption or biggest worry?

**Depth Visualization (2-3 min):**
Show completeness with progress bars:
```
📊 Project Context Completeness
Objectives          ████████░░  80%  Good depth
Constraints         ███░░░░░░░  30%  Needs exploration
Non-goals           ██████████ 100%  Clear

🎯 Recommended deep dives:
1. Constraints (30% - critical gap)
2. Risks (10% - helps prevent issues)
```

User chooses areas for deeper exploration.

**Targeted Deep Dives (10-20 min):**
3-4 questions per selected area from different angles:
- Outcome focus
- User job (Jobs-to-be-Done)
- Trade-offs and boundaries
- Measurable criteria

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

Create directory structure following PARA-inspired model:
```
.chronicle/
├── project-truth.md           # PURPOSE: Why we exist (populated from Q&A)
├── tasks/                     # PURPOSE: Active work (one file per task)
│   └── (empty initially)
├── context/                   # RESOURCES: Reference material
│   ├── visuals/
│   ├── decisions/
│   │   └── (ADRs when needed)
│   └── principles.md          # Quick decisions (Y-statements)
├── journey/                   # ARCHIVE: What happened
│   ├── session-log.md         # Last 2-3 sessions only
│   ├── session-archive.md     # Older sessions (excluded from AI context)
│   ├── completed-tasks/       # Completed task files moved here
│   └── lessons.md             # Accumulated wisdom
└── execution/                 # SYSTEM: How we work
    ├── parts-manifest.md      # Components/materials
    ├── key-patterns.md        # Recurring techniques
    ├── key-facts.md           # Configuration & references
    └── validation-strategy.md # Testing criteria
```

**Layer model:**
- **Purpose Layer:** project-truth.md + tasks/ (what we're building and why)
- **Resources Layer:** context/* (reference material for decisions and architecture)
- **Archive Layer:** journey/* (project history and learnings)
- **System Layer:** execution/* (operational knowledge)

**Auto-detection for software projects:**
If code files exist (*.cs, *.js, package.json, *.csproj, src/):
- Generate architecture diagrams (using mermaid-diagrams skill if available)
- Rename parts-manifest.md → component-manifest.md
- Rename validation-strategy.md → testing-strategy.md
- Add software-specific terminology

### Phase 3: Write Protocols to CLAUDE.md

Append complete chronicle protocols to CLAUDE.md:

```markdown
<!-- ============================================================ -->
<!-- CHRONICLE SYSTEM PROTOCOLS                                   -->
<!-- Generated by: chronicle skill v1.0.0                         -->
<!-- Initialized: [DATE]                                          -->
<!-- ============================================================ -->

## Chronicle System

[Complete 200-line protocol - see templates/claude.md]

<!-- ============================================================ -->
<!-- END CHRONICLE SYSTEM PROTOCOLS                               -->
<!-- ============================================================ -->
```

**Protocol sections:**
- File structure documentation
- **Before starting work checklist:**
  1. Read `.chronicle/project-truth.md` for complete context (25 min)
  2. Use "List tasks" / "Show tasks" to see current work
  3. Review `.chronicle/journey/session-log.md` for recent progress
- **Task management workflow:**
  - List tasks command
  - Create new task (with numbering system)
  - Mark task complete (move to completed-tasks/)
  - Task file format specification
- **Session end protocol** (8 steps):
  1. Summarize session (key accomplishments, decisions, learnings)
  2. Update `.chronicle/journey/session-log.md` with detailed narrative
  3. Ensure completed tasks moved to `.chronicle/journey/completed-tasks/`
  4. Create ADRs in `.chronicle/context/decisions/` if significant decisions made
  5. Update diagrams in `.chronicle/context/visuals/` if structure changed
  6. Document problems/learnings in `.chronicle/journey/lessons.md`
  7. Weekly check: If >7 days of logs, suggest compressing into `.chronicle/project-truth.md`
  8. Update check: Ensure protocols stay current with skill evolution
- Decision recording (ADRs)
- Problem logging (lessons.md)
- Context management rules
- Task detection during planning
- Regeneration principle

### Phase 4: Create User Guide

Create `USING-CHRONICLE.md` at project root with:
- What is chronicle (3 purposes)
- Quick reference
- Common workflows
- Understanding the structure
- Tips & best practices
- Troubleshooting
- Phrases cheat sheet

### Phase 5: Completion

```
✓ Chronicle initialized!

Your project now has:
- .chronicle/ directory with complete structure
- CLAUDE.md with operating protocols
- USING-CHRONICLE.md for your reference

To get started:
- Read USING-CHRONICLE.md for usage guide
- Read .chronicle/project-truth.md for project context
- Say "what should I work on?" to begin

The skill is no longer needed - everything is self-contained.
```

## Planning Mode Integration

Chronicle works seamlessly with planning mode for task creation:

**Planning mode workflow:**
1. User and Claude collaborate on task plan in planning mode (no file edits)
2. When plan is finalized, Claude says: **"Ready to implement? Switch to agent mode and say 'add the task'"**
3. User manually switches to agent mode
4. User signals task creation: "Add the task" / "Create the task" / "Task accepted", or similar to that effect
5. Chronicle creates task file in `.chronicle/tasks/NNNN-task-name.md`
6. Chronicle asks: "Should I start working on this task now?"
7. User responds:
   - "Yes" / "Start" → Chronicle begins implementation
   - "No" / "Just queue it" → Task queued for later

**Starting queued tasks:**
```
User: "Start working on [task name]" / "Work on task 0004"

Chronicle: [Begins implementation]
```

**Key phrases for task acceptance:**
- "Add the task"
- "Create the task"  
- "Task accepted"
- "Queue this"

## Task Management

Chronicle automatically manages tasks:

**List all tasks:**
```
User: "List tasks" / "Show tasks" / "What are the tasks?"

Chronicle: [Scans .chronicle/tasks/ directory]
            "Current tasks:
            0001: Complete feature X (created 2026-01-15)
            0002: Add component Y (created 2026-01-20)
            0003: Create tests for Z (created 2026-01-22)"
```

**Create new task:**
```
User: "Add the task" (after planning in agent mode)

Chronicle: [Creates .chronicle/tasks/NNNN-task-name.md]
           "Task created: 0004-implement-new-feature.md
           Should I start working on this task now?"
```

**Task file format:**
Each task is a separate file: `.chronicle/tasks/NNNN-task-name.md`
```markdown
# Task: [Task Name]

**Created:** YYYY-MM-DD by [Creator Name]

## Description

[Task details and context]
```

Numbers are sequential (0001, 0002, etc.). Duplicates are acceptable for team collaboration - files differentiate by name.

**On task completion:**
```
User: "Mark task complete: implement X" / "Task 0004 is complete"

Chronicle: [Automatically:]
1. Move file from .chronicle/tasks/0004-implement-x.md → .chronicle/journey/completed-tasks/
2. Add completion metadata: "**Completed:** YYYY-MM-DD (Duration: Xh)" after Created line
3. Add entry to .chronicle/journey/session-log.md
4. List remaining tasks and suggest next one
```

## Session End Protocol

```
User: "Update chronicle"

Chronicle: [Walks through 8 steps:]
1. Summarize session (key accomplishments, decisions, learnings)
2. Update .chronicle/journey/session-log.md with detailed narrative
3. Move completed tasks to .chronicle/journey/completed-tasks/ (check if any missed)
4. Create ADRs in .chronicle/context/decisions/ if significant decisions made
5. Update diagrams in .chronicle/context/visuals/ if structure changed
6. Document problems/learnings in .chronicle/journey/lessons.md
7. Weekly check: If >7 days of logs, suggest compressing into .chronicle/project-truth.md
8. Update check: Ensure protocols stay current with skill evolution
```

## Context Management

**Context loading (two-tier approach):**

**Essential context** (always load first - ~5K tokens):
- .chronicle/project-truth.md
- .chronicle/tasks/* (all active task files)
- .chronicle/context/principles.md
- .chronicle/journey/lessons.md
- .chronicle/execution/key-facts.md

**On-demand context** (load when relevant - ~15K additional tokens):
- .chronicle/journey/session-log.md (last 2-3 sessions)
- .chronicle/context/decisions/* (full ADRs when deep dive needed)
- .chronicle/context/visuals/* (diagrams when architecture questions arise)
- .chronicle/execution/parts-manifest.md (component details)
- .chronicle/execution/key-patterns.md (technique reference)
- .chronicle/execution/validation-strategy.md (testing criteria)

**Excluded from AI context:**
- .chronicle/journey/completed-tasks/* (human reference only)
- .chronicle/journey/session-archive.md (archived sessions)
- .chronicle/context/decisions-archive/* (superseded decisions)
- USING-CHRONICLE.md (user guide only)

**Token budget guidance:**
- project-truth.md: Target 2-4 pages (1K-2K tokens), max 6 pages
- principles.md: Terse Y-statements, ~500-1K tokens
- session-log.md: 300 lines max (~2K tokens), compress beyond that
- Individual task files: Varies, aim for clarity over brevity
- Full ADRs: Use sparingly, only for major architectural decisions

## Optional: Update Protocols

```
User: "Update chronicle protocols"

Chronicle: [Updates CLAUDE.md with latest version while preserving customizations]
```

## File Templates

See templates/ directory for:
- **claude.md** - Full CLAUDE.md protocol section with two-tier context loading
- **project-truth.md** - Populated from Q&A, token budget guidance included
- **principles.md** - Quick decisions using Y-statement format
- **task-file-template.md** - Individual task file format (NNNN-task-name.md) with frontmatter
- **session-log.md** - Conventional commit format, 300-line compression trigger
- **lessons.md** - Problems/learnings with frontmatter
- **using-chronicle.md** - User guide
- **adr-template.md** - Simplified 3-section format (Context, Decision, Consequences)

## Decision Documentation Formats

**Quick decisions (most common):**
Use Y-statements in `context/principles.md`:
```
In the context of [situation], facing [concern], we decided for [option], 
to achieve [benefit], accepting [tradeoff].
```
Optional detail bullets below when elaboration needed.

**Major architectural decisions:**
Use full ADR in `context/decisions/NNNN-name.md`:
- Section 1: Context (problem and constraints)
- Section 2: Decision (what was chosen, why, alternatives rejected)
- Section 3: Consequences (what becomes easier/harder, implementation notes)

Based on Michael Nygard's original ADR format, simplified from verbose enterprise templates.

## Key Principles

**Self-contained:** After initialization, skill is not needed. Everything operates from CLAUDE.md.

**Regenerative:** From chronicle alone, work should be recreatable by anyone (human or AI).

**Comprehensive:** Captures not just what was built, but why decisions were made and what failed.

**Universal:** Works for software, DIY, presentations, creative projects - any long-running work.

**Transparent:** All files are markdown, directly editable, no magic.

## Philosophy

> "Code is what the computer executes. Documentation is what the team executes. In AI-assisted development, documentation becomes the primary artifact."

Chronicle treats the journey of understanding as more valuable than the artifact. Code can be regenerated; understanding cannot.
