# ADR-009: Clean Skill/Development Separation

**Date:** 2025-02-01
**Status:** Accepted
**Context:** Repository structure for meta-project

## Context and Problem

This repository both DEFINES the chronicle skill and USES chronicle to document its own development. This creates confusion:
- Which files are "the skill" vs "documenting building the skill"?
- How to package the skill cleanly without development artifacts?
- How to avoid bidirectional sync complexity?

Initial structure had SKILL.md at root with .chronicle/ also at root, making it unclear what gets distributed vs what's for development.

## Decision

**Unidirectional structure with clean separation:**

```
chronicle-skill-repo/              ← Git repository
├── chronicle-skill/               ← THE SKILL (pristine, distributable)
│   ├── SKILL.md
│   ├── USING-CHRONICLE.md
│   └── README.md
│
├── .chronicle/                    ← Development chronicle (at root)
│   └── ...                        (standard chronicle structure)
│
├── README.md                      ← Repository README
├── CLAUDE.md                      ← Project context
└── LICENSE
```

**Mental model:**
- `chronicle-skill/` = The product we're building (clean source)
- `.chronicle/` = How we're building it (dogfooding)
- `.chronicle/` treats this like any other project using chronicle

**Sync rule:** SKILL.md → .chronicle/ (one direction)
- When chronicle-skill/SKILL.md structure changes
- Think: "Re-run the skill on this project"
- Update .chronicle/ to match what skill would create

## Alternatives Considered

**Option A: Everything at root (original)**
- SKILL.md, USING-CHRONICLE.md, .chronicle/ all at root
- **Con: Unclear what's skill vs development**
- **Con: Can't cleanly package skill**
- **Why rejected:** Mental model confusion

**Option B: Bidirectional sync**
- .chronicle/ is source for templates
- Copy from .chronicle/ to skill definition
- **Con: Complex** - Two sources of truth
- **Con: Easy to forget sync**
- **Why rejected:** Unnecessary complexity

**Option C: No dogfooding**
- Build skill without using it
- **Con: Misses whole point** - Can't validate design
- **Con: No real usage examples**
- **Why rejected:** Dogfooding is valuable

**Option D: Skill in subfolder (chosen)**
- **Pro: Clean packaging** - chronicle-skill/ is distributable as-is
- **Pro: Clear separation** - Product vs development docs
- **Pro: Unidirectional** - SKILL.md is source of truth
- **Pro: Standard pattern** - Like src/ for code

## Consequences

**Positive:**
- ✅ Clean packaging - chronicle-skill/ can be published as-is
- ✅ Clear mental model - Product vs development separation
- ✅ Unidirectional sync - SKILL.md → .chronicle/ (simpler)
- ✅ No pollution - Skill source stays pristine
- ✅ Standard structure - Familiar to developers

**Negative:**
- ❌ One extra directory level - chronicle-skill/SKILL.md vs SKILL.md
- ❌ Must remember sync - When SKILL.md structure changes
- ❌ Two READMEs - Root and chronicle-skill/ (but different purposes)

## Implementation

**Files moved:**
1. SKILL.md → chronicle-skill/SKILL.md
2. USING-CHRONICLE.md → chronicle-skill/USING-CHRONICLE.md
3. Created chronicle-skill/README.md (skill marketing)
4. Updated root README.md (repository explanation)
5. Updated CLAUDE.md with structure note

**Sync checklist (add to session end):**
- If chronicle-skill/SKILL.md structure changed: sync to .chronicle/

## Related Decisions

- ADR-001: Bootstrap-and-exit pattern
- ADR-003: 10-file structure (what SKILL.md defines)
