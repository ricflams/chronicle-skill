---
type: task
created: 2026-02-01
status: completed
---

# Task: Clarify Planning Mode Handoff Protocol

**Created:** 2026-02-01 by Richard  
**Completed:** 2026-02-01  
**Status:** ✅ Complete

## Description

The planning mode handoff prompt ("Ready to implement? Switch to agent mode and say 'add the task'") is currently only specified for "finalized plans" but should apply to ANY implementation guidance. Update protocol language to make this explicit and prevent omissions like the installation documentation example where the handoff was forgotten.

## Steps

1. Update SKILL.md Planning Mode section - Change "When plan is finalized" to "When presenting any plan or implementation guidance" in the planning mode workflow. Add explicit note that handoff applies to documentation plans, code suggestions, configuration guidance - anything with potential implementation.

2. Update templates/claude.md Planning Mode section - Mirror the SKILL.md change. Emphasize that even simple guidance (like "add this section to README") should trigger the handoff prompt if there's something to implement.

3. Add examples to protocol - Include examples of when to use handoff:
   - "Update README installation section" (YES - use handoff)
   - "Here's how the feature works" (NO - pure explanation)
   - "Add these 3 functions" (YES - use handoff)
   - "The error means X" (NO - diagnosis only)

4. Sync SKILL.md to root - Copy updated chronicle-skill/SKILL.md to root after changes.

## Success Criteria

- ✅ SKILL.md Planning Mode section updated with broader trigger language
- ✅ templates/claude.md Planning Mode section updated
- ✅ Examples added showing when handoff applies vs doesn't
- ✅ Root SKILL.md synced

## Notes

This addresses a real omission that just happened: installation documentation plan was provided without the handoff prompt, violating the protocol we just created.
