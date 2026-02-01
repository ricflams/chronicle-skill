# ADR-006: Completed Tasks Excluded from AI Context

**Date:** 2025-02-01
**Status:** Accepted
**Context:** AI context management and file inclusion strategy

## Context and Problem

`completed-tasks.md` archives finished tasks. Should it be included in AI context (so Claude reads it automatically), or excluded?

## Decision

Exclude `completed-tasks.md` from AI context. File serves as human-readable progress tracking archive only. Claude gets completion details from `session-log.md` narrative instead.

## Alternatives Considered

**Option A: Include in AI context**
- Pro: Claude can see all completed work
- Pro: Provides historical task reference
- **Con: Context pollution** - Long list of completed tasks rarely relevant
- **Con: Duplicates session-log** - Completion details already in narrative
- **Con: Grows unbounded** - Every completed task adds to context load
- **Why rejected:** Cost outweighs benefit

**Option B: Archive with weekly compression**
- Pro: Keeps context manageable
- Pro: Preserves history
- **Con: Extra maintenance** - Another compression workflow
- **Con: Still duplicates session-log** - Info is already there
- **Why rejected:** Unnecessary complexity

**Option C: Don't create completed-tasks.md at all**
- Pro: Simplest - one less file
- Pro: session-log has everything
- **Con: Humans lose progress view** - No quick "what have we accomplished?"
- **Con: No simple completion list** - Would need to parse session-log
- **Why rejected:** Human UX matters

## Consequences

**Positive:**
- ✅ Cleaner AI context - Only relevant information included
- ✅ No duplication - Completion details live in one place (session-log)
- ✅ Better performance - Smaller context = faster processing
- ✅ Human progress view - File still valuable for users

**Negative:**
- ❌ Claude can't directly reference completed tasks - Must check session-log
- ❌ Two sources of truth - Task completions in both files (different formats)

## Implementation

**In session-log.md:**
- Detailed narrative: "Completed Task-123: Implementation details, duration 2h 15m, challenges encountered..."

**In completed-tasks.md (human archive):**
- Simple list: `- [2025-02-01] Implement initialization logic (2h 15m)`

**In CLAUDE.md protocols:**
- Explicit instruction to update session-log with details AND completed-tasks with simple entry
- completed-tasks.md NOT in "files Claude should read" list

## Related Decisions

- ADR-007: active-tasks.md at top level (different time orientation)
- Session-log.md becomes single source of truth for completion details
