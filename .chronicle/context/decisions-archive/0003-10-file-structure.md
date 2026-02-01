# ADR-003: 10-File Consolidated Structure

**Date:** 2025-02-01
**Status:** Accepted
**Context:** Chronicle directory organization

## Context and Problem

How many files and what structure provides the best balance between organization and simplicity? Initial design had 18 files across many subdirectories - felt overwhelming.

## Decision

Consolidate to 10 core files organized in 4 conceptual layers:
- Truth Layer: project-truth.md, active-tasks.md
- Context Layer: visuals/, decisions/
- Journey Layer: session-log.md, completed-tasks.md, lessons.md
- Execution Layer: parts-manifest.md, key-patterns.md, key-facts.md, validation-strategy.md

## Evolution

**V1 (18 files):**
- Separate scope/, context/overview.md, protocols/
- Split: objectives.md, requirements.md, constraints.md, non-goals.md
- Split: problems.md, experiments.md, learnings.md
- Result: Too many small files, hard to navigate

**V2 (11 files):**
- Merged scope files → project-truth.md
- Eliminated context/overview.md (content into project-truth.md)
- Kept active-tasks.md separate
- Result: Better, but still felt fragmented

**V3 (10 files - current):**
- Merged problems + experiments + learnings → lessons.md
- Eliminated protocols/ (moved to CLAUDE.md per ADR-002)
- Result: Sweet spot between organization and simplicity

## Alternatives Considered

**Option A: Fewer files (5-6 large files)**
- Pro: Less navigation overhead
- **Con: Large files become hard to navigate** - Loses focus
- **Con: Harder for AI to find relevant context** - More to scan
- **Why rejected:** Too coarse-grained

**Option B: More files (15-20+ files)**
- Pro: Very granular organization
- Pro: Each concept in its own file
- **Con: Overwhelming** - Too many files to track
- **Con: Where does this go?** - Decision paralysis
- **Why rejected:** Complexity burden outweighs benefits

**Option C: Subdirectory per layer**
- Pro: Clean separation
- **Con: Active-tasks.md buried** - Less visible
- **Con: More directory navigation** - Friction
- **Why rejected:** Flat is better than nested (within reason)

## Files Eliminated

1. **context/overview.md** → Merged into project-truth.md
2. **scope/objectives.md** → Merged into project-truth.md
3. **scope/requirements.md** → Merged into project-truth.md
4. **scope/constraints.md** → Merged into project-truth.md
5. **scope/non-goals.md** → Merged into project-truth.md
6. **journey/problems.md** → Merged into lessons.md
7. **journey/experiments.md** → Merged into lessons.md
8. **protocols/** directory → Content moved to CLAUDE.md (ADR-002)

## Consequences

**Positive:**
- ✅ Easier to navigate - Clear purpose for each file
- ✅ Related information together - Less jumping between files
- ✅ Fewer concepts to track - Reduced cognitive load
- ✅ Still organized - 4 layers provide clear mental model

**Negative:**
- ❌ Some files moderately long - project-truth.md can be 200+ lines
- ❌ Multiple concerns per file - lessons.md has problems + experiments + learnings

## Related Decisions

- ADR-002: Eliminating protocols/ directory required protocols in CLAUDE.md
- ADR-004: active-tasks.md elevated to top level
