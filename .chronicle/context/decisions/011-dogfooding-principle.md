# ADR-011: Dogfooding Principle - Repository Structure Mirrors Chronicle Output

**Date:** 2026-02-01  
**Status:** Accepted  
**Context:** Repository structure alignment  
**Related:** ADR-009 (Skill/Development Separation)

---

## Context

When building a system that creates structure for others, the builder faces a fundamental question: should we use our own system to organize our work? This is the "eating your own dog food" principle.

For chronicle, we faced this choice:
1. Build chronicle using some other organizational system (ironic)
2. Use chronicle to document building chronicle (meta but honest)

We chose option 2, but this creates a subtle requirement: **our repository must actually follow chronicle's structure**. If `.chronicle/` in this repo doesn't match what chronicle creates for users, we're not truly dogfooding.

### The Problem

During validation, we discovered structural violations:
- `tasks/` was at project root instead of `.chronicle/tasks/`
- `USING-CHRONICLE.md` was missing from root (should be synced from chronicle-skill/)
- The repository didn't look like "a project that initialized with chronicle"

These violations meant:
- We weren't validating the actual structure users would receive
- Documentation referenced paths that didn't exist in our own codebase
- The skill's definition (SKILL.md) contradicted our implementation

## Decision

**Establish the Dogfooding Principle:**

1. **chronicle-skill/ must contain the complete pristine distributable**
   - All files users receive: SKILL.md, USING-CHRONICLE.md, README.md
   - No `.chronicle/` directory inside (keep it clean for packaging)
   - This is the canonical source of truth for structure

2. **The repository itself must appear as if chronicle initialized it**
   - `.chronicle/` at root follows exactly what SKILL.md defines
   - All paths in documentation match the actual structure
   - If chronicle creates `.chronicle/tasks/`, ours is there too

3. **Validation through dogfooding**
   - Any structural change to SKILL.md must be applied to our `.chronicle/`
   - If we can't follow our own structure, it needs redesign
   - The repository is both product and proof-of-concept

## Implementation

**Immediate corrections:**
- Move `tasks/` → `.chronicle/tasks/`
- Copy `chronicle-skill/USING-CHRONICLE.md` → root `USING-CHRONICLE.md`
- Update all documentation references to match actual structure

**Ongoing discipline:**
- When SKILL.md structure changes, update `.chronicle/` to match
- Sync USING-CHRONICLE.md from chronicle-skill/ to root
- Regular audits: "Does our structure match what we tell users to create?"

## Consequences

### Positive
- **True validation** - We're testing what users actually get
- **Honest documentation** - All examples come from real usage
- **Credibility** - "We use this ourselves" becomes literally true
- **Better design** - If we find our own structure awkward, users will too

### Negative
- **Meta-complexity** - Explaining "chronicle documents building chronicle"
- **Sync discipline** - Must keep chronicle-skill/ and .chronicle/ aligned
- **Cognitive overhead** - Need to think about two contexts simultaneously

### Neutral
- **No backward compatibility** - Old structure was wrong, clean break is fine
- **Documentation burden** - Must explain the meta-nature to contributors

## Alternatives Considered

**Alternative 1: Separate documentation system**
Build chronicle using standard GitHub practices (README, Issues, Wiki).

Rejected because:
- We wouldn't validate our own product
- Can't honestly say "we use this"
- Miss opportunities to discover UX problems

**Alternative 2: Loose dogfooding**
Use chronicle loosely without strict structural adherence.

Rejected because:
- Half-measures reduce validation value
- Users notice inconsistencies
- Undermines trust in the system

**Alternative 3: Two .chronicle/ instances**
One in chronicle-skill/ (demo), one at root (real work).

Rejected because:
- Doubles maintenance
- Demo diverges from reality over time
- Which one is "truth"?

## Related Decisions

- **ADR-009:** Established chronicle-skill/ as pristine distributable
- **ADR-010:** Individual task files (must be in correct location)
- **ADR-002:** CLAUDE.md protocols (now must reference correct paths)

## Notes

This decision codifies what should have been obvious from the start: if we're building a documentation system, our documentation should use that system. The repository structure violations were caught because a user (correctly) questioned why `tasks/` was at root when SKILL.md showed it in `.chronicle/`.

The dogfooding principle applies recursively: this very ADR exists in `.chronicle/context/decisions/` because that's where chronicle says decisions should live.
