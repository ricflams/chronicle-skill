# ADR-007: Active Tasks at Top Level

**Date:** 2025-02-01
**Status:** Accepted
**Context:** Chronicle directory structure and task management

## Context and Problem

Where should `active-tasks.md` live? Options:
- `.chronicle/` top level (elevated)
- `.chronicle/journey/` (grouped with other task/time files)
- `.chronicle/execution/` (it's about work to do)

## Decision

Place `active-tasks.md` at `.chronicle/` top level, not in a subdirectory.

## Alternatives Considered

**Option A: Keep in journey/ directory**
- Pro: Grouped with completed-tasks.md
- Pro: Both are task-related files
- **Con: Conceptual mismatch** - Journey is PAST, active tasks are FUTURE
- **Con: Less visible** - Buried in subdirectory
- **Con: Wrong time orientation** - journey/ is history, not present/future
- **Why rejected:** Semantically incorrect grouping

**Option B: Place in execution/ directory**
- Pro: Execution layer is about "how we work"
- Pro: Tasks are execution artifacts
- **Con: Still buried** - Less visible than top level
- **Con: execution/ is patterns/facts** - Not dynamic work queue
- **Why rejected:** execution/ is for reference, not active state

**Option C: Top level (chosen)**
- **Pro: Very visible** - First-level file in `.chronicle/`
- **Pro: Signals importance** - Tasks are central to workflow
- **Pro: Clear separation** - Present/future vs past (journey/)
- **Pro: Easier access** - No subdirectory navigation
- **Con: One more file at top level** - Less grouped

## Conceptual Model

**Time Orientation:**
- `active-tasks.md` - PRESENT & FUTURE (what we're doing, what's next)
- `journey/` - PAST (what happened, what we learned)
- `project-truth.md` - TIMELESS (scope, context, principles)

**Active tasks don't belong in journey because they haven't happened yet.**

## Consequences

**Positive:**
- ✅ Maximum visibility - Can't be overlooked
- ✅ Clear mental model - Present/future vs past separation
- ✅ Easier workflow - "Check active-tasks" is straightforward
- ✅ Signals importance - Top-level placement shows priority

**Negative:**
- ❌ Flatter structure - One more file at `.chronicle/` root
- ❌ Less grouping - Task files split between levels

**Trade-off:** Accepted less grouping for better semantics and visibility.

## Implementation

```
.chronicle/
├── project-truth.md      (timeless)
├── active-tasks.md       (present/future) ← elevated
├── context/              (structure)
├── journey/              (past)
│   ├── completed-tasks.md  ← archived history
│   └── ...
└── execution/            (how we work)
```

## Related Decisions

- ADR-006: completed-tasks.md excluded from AI context (journey/ is for humans)
- ADR-003: 10-file structure accommodates this elevation
