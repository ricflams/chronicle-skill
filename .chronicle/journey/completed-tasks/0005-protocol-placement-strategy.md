# Task: Create protocol placement strategy

**Created:** 2025-02-01 by Richard  
**Completed:** 2025-02-01 (Duration: 30min)

## Description

Decide where protocols should live: CLAUDE.md vs separate file.

## Outcomes

- Decision: Protocols in CLAUDE.md directly (ADR-002)
- Rejected: Separate .chronicle/protocols.md (unreliable indirection)
- Rationale: CLAUDE.md auto-loaded, separate file requires conscious tool call
