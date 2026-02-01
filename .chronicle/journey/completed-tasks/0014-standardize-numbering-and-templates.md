# Task: Standardize Chronicle Numbering and Template Names

**Created:** 2026-02-01 by Richard  
**Completed:** 2026-02-01  
**Status:** ✅ Complete

## Description

Chronicle uses 4-digit numbering for tasks but 3-digit for ADRs, and the claude template has awkward naming/content. Standardize everything to 4-digit numbering and fix template issues.

## Steps

1. Fix ADR file renaming - Rename all decision files to 4-digit format: 0000-bootstrap-and-exit.md→0001, 0000-protocols-in-claude-md.md→0002, through 0000-dogfooding-principle.md→0011

2. Update decision index - Change all references in .chronicle/context/decisions/index.md from 3-digit to 4-digit filenames

3. Update CLAUDE.md decision references - Change "DEC-001", "DEC-002", "DEC-010" → "DEC-0001", "DEC-0002", "DEC-0010"

4. Fix claude template name and content - Rename chronicle-skill/templates/claude-protocols.md → claude.md, remove wrapper/explanation text (keep only the actual protocol markdown ready to paste)

5. Update SKILL.md template references - Change `claude-protocols.md` → `claude.md` in chronicle-skill/SKILL.md (lines 131, 304)

6. Update ADR template format - Change `ADR-[NUMBER]` → `ADR-[NNNN]` in chronicle-skill/templates/adr-template.md

7. Add planning mode handoff prompt - Update SKILL.md and templates/claude.md to document that after presenting a plan in planning mode, Claude should say: "Ready to implement? Switch to agent mode and say 'add the task'"

8. Sync SKILL.md to root - Copy updated chronicle-skill/SKILL.md → SKILL.md
