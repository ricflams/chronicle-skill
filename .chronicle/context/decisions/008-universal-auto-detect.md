# ADR-008: Universal with Auto-Detection

**Date:** 2025-02-01
**Status:** Accepted
**Context:** Chronicle initialization and project type handling

## Context and Problem

Chronicle should work for software projects, DIY projects, creative work, etc. How should it handle different project types?

Options:
1. Ask user to explicitly choose project type
2. Universal base + auto-detect and adapt
3. Separate skills for each type

## Decision

Universal approach with automatic project type detection. All projects get same structure, but terminology and questions adapt based on detected context.

## Alternatives Considered

**Option A: Explicit project type selection**
- Pro: User controls categorization
- Pro: Clear which mode is active
- **Con: Extra friction** - Another decision in initialization
- **Con: What if hybrid?** - Software + hardware project, presentation about code
- **Con: User might choose wrong type** - Unclear boundaries
- **Why rejected:** Unnecessary friction, rigid categories

**Option B: Separate skills (chronicle-dev, chronicle-diy, chronicle-creative)**
- Pro: Each optimized for specific domain
- Pro: Cleaner code (no conditionals)
- **Con: Maintenance burden** - 3 skills to update
- **Con: Discovery problem** - Which skill do I need?
- **Con: Hybrid projects?** - User forced to choose
- **Why rejected:** Violates DRY, creates confusion

**Option C: Universal structure + auto-adaptation (chosen)**
- **Pro: Zero friction** - No explicit choice needed
- **Pro: Works for hybrid projects** - Adapts to multiple signals
- **Pro: Smart defaults** - Best UX
- **Con: More complex logic** - Detection code needed
- **Con: Might mis-detect** - Edge cases possible

## Auto-Detection Signals

**Software project detected if:**
- Code files present (`.js`, `.py`, `.ts`, `.java`, etc.)
- `package.json`, `requirements.txt`, `Cargo.toml`, etc.
- `.git` directory

**DIY/Physical project detected if:**
- Bill of materials mentioned
- Physical constraints discussed
- Tools/materials keywords

**Creative project detected if:**
- Slides, presentations, pitches mentioned
- Design deliverables discussed
- Creative brief present

## Terminology Adaptation

**parts-manifest.md:**
- Software → components-manifest.md (classes, modules, services)
- DIY → materials-manifest.md (parts, tools, supplies)
- Creative → deliverables-manifest.md (slides, assets, documents)
- Unknown → parts-manifest.md (neutral)

**validation-strategy.md:**
- Software → testing, CI/CD, acceptance criteria
- DIY → testing fit/function, safety checks, acceptance
- Creative → review criteria, feedback loops, approval gates

**Questions adapt:**
- Software: Ask about architecture, tech stack, deployment
- DIY: Ask about tools, space constraints, safety
- Creative: Ask about audience, format, deadlines

## Consequences

**Positive:**
- ✅ Zero friction - No explicit choice required
- ✅ Handles hybrid projects - Multiple types detected gracefully
- ✅ Smart UX - Feels personalized without effort
- ✅ One skill - Simpler for users to discover and use

**Negative:**
- ❌ Detection can fail - Edge cases where signals unclear
- ❌ More complex code - Conditional logic throughout
- ❌ Less explicit - User might not realize adaptation happened

**Mitigation:**
- Show detected type during initialization: "I detect this is a software project..."
- Allow user to correct: "Actually, this is a DIY project" → re-adapt
- Default to universal language when uncertain

## Implementation

```markdown
During initialization:
1. Scan workspace for detection signals
2. Display: "I detect this is a [software/DIY/creative] project"
3. Ask: "Is this correct?" (allow override)
4. Adapt terminology and questions accordingly
5. Use universal fallbacks when uncertain
```

## Related Decisions

- ADR-003: Universal 10-file structure works for all types
- ADR-001: Bootstrap-and-exit means adaptation happens once at init
