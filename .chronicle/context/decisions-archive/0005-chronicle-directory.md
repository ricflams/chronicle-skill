# ADR-005: .chronicle/ Directory Name

**Date:** 2025-02-01
**Status:** Accepted
**Context:** Project directory structure

## Context and Problem

What should the documentation directory be named? Need something that:
- Clearly indicates purpose
- Is memorable and discoverable
- Follows conventions (hidden directory with `.` prefix)
- Isn't too generic

## Decision

Use `.chronicle/` as the directory name for all project documentation.

## Alternatives Considered

**Option A: `.ai/` directory**
- Pro: Short and memorable
- Pro: Clearly AI-related context
- **Con: Too generic** - Could contain anything AI-related
- **Con: Not descriptive** - Doesn't indicate it's a chronicle/journal
- **Con: Confusing** - Is this for AI code? AI prompts? AI docs?
- **Why rejected:** Not semantic enough

**Option B: `.context/` directory**
- Pro: Describes what it contains
- Pro: Generic enough for any project type
- **Con: Too vague** - Many things are "context"
- **Con: Doesn't convey chronicle/journey aspect**
- **Why rejected:** Misses the narrative dimension

**Option C: `.memory/` directory**
- Pro: Relates to memory/continuity concept
- Pro: Shorter than chronicle
- **Con: Feels like cache/temp** - Memory gets cleared
- **Con: Doesn't convey permanence** - Chronicles are lasting
- **Why rejected:** Wrong connotations

**Option D: `.docs/` or `.documentation/`**
- Pro: Familiar pattern
- **Con: Already used for public docs** - Confusion with published documentation
- **Con: Static feel** - Doesn't convey living/evolving nature
- **Why rejected:** Too conventional, wrong semantics

## Consequences

**Positive:**
- ✅ Branded and semantic - Immediately clear what it contains
- ✅ Memorable - Distinctive name
- ✅ Follows convention - Hidden directory (`.` prefix)
- ✅ Beautiful - `.chronicle/` is elegant
- ✅ Self-documenting - Name explains purpose

**Negative:**
- ❌ Longer than alternatives - 10 characters vs `.ai/` (3 chars)
- ❌ Unique pattern - Not a standard convention (like `.git/`)
- ❌ Requires explanation - First-time users might wonder what it is

**Trade-off:** Accepted slightly longer name for much better semantics and branding.

## Implementation

All chronicle documentation lives in `.chronicle/` directory at project root:

```
.chronicle/
├── project-truth.md
├── active-tasks.md
├── context/
├── journey/
└── execution/
```

## Related Decisions

- ADR-004: Name follows from "chronicle" branding decision
- ADR-003: Directory contains 10-file consolidated structure
