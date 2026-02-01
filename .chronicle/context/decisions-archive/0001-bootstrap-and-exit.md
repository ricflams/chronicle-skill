# ADR-001: Skill Bootstraps Then Exits

**Date:** 2025-02-01
**Status:** Accepted
**Context:** Chronicle system architecture

## Context and Problem

Chronicle aims to create self-contained, long-lasting project documentation. Should the skill remain active throughout the project lifecycle, or should it transfer knowledge and exit?

## Decision

The chronicle skill bootstraps the project by creating complete documentation structure and protocols, then exits. The project becomes fully self-contained and skill-independent.

## Alternatives Considered

**Option A: Keep skill active throughout project lifecycle**
- Pro: Can provide ongoing updates and improvements to protocols
- Pro: Centralized maintenance of documentation patterns
- **Con: Creates dependency** - Project breaks if skill unavailable
- **Con: Violates self-containment** - Users stuck if skill discontinued
- **Con: Version lock-in** - Hard to customize without breaking updates
- **Why rejected:** Dependency contradicts core regenerative principle

**Option B: Hybrid (skill for major updates, otherwise independent)**
- Pro: Balance between self-containment and maintainability
- **Con: Unclear when skill is "needed"** - Creates confusion
- **Con: Still has dependency** - Partial dependency is still dependency
- **Why rejected:** Doesn't solve fundamental problem

## Consequences

**Positive:**
- ✅ True self-containment - Works forever, even if skill disappears
- ✅ User customization - All protocols visible and editable in CLAUDE.md
- ✅ No version conflicts - Each project is independent
- ✅ Trust and transparency - Users see exactly how system works

**Negative:**
- ❌ No automatic protocol updates - Each project is frozen at initialization version
- ❌ Must be comprehensive upfront - Protocols can't rely on skill being present
- ❌ Higher initial complexity - Everything must be in CLAUDE.md from start

## Implementation

1. Skill runs comprehensive 3-phase initialization (15-28 min)
2. Creates complete `.chronicle/` directory structure (10 files)
3. Writes 200+ lines of protocols to CLAUDE.md
4. Creates user guide (USING-CHRONICLE.md)
5. Exits - never needed again

## Related Decisions

- ADR-002: Protocols must be in CLAUDE.md (consequence of this decision)
- ADR-008: Universal auto-detection happens during bootstrap
