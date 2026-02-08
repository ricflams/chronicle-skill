# Indirection Fails with AI

**Tags:** #architecture #ai-patterns  
**Severity:** High — would have caused ongoing failures

## What Happened

Considered putting protocols in separate .chronicle/protocols.md file with pointer from CLAUDE.md to keep it "clean."

## Root Cause

Prioritized aesthetics (shorter CLAUDE.md) over reliability.

## What We Learned

Indirection is dangerous with AI. Claude might forget to read the separate file. If something is essential, put it where it's guaranteed to be seen. CLAUDE.md is automatically loaded; separate files require conscious tool calls.

## Prevention

When tempted by indirection for "cleanliness," test whether the extra step is actually reliable. For AI systems: if it must be read, it must be automatic.
