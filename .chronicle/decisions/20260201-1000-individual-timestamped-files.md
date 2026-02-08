# Individual Timestamped Files

## Context

Centralized files (decisions.md, lessons.md, session-log.md) create git merge conflicts when multiple team members work simultaneously. Also makes diffs hard to read.

## Decision

Use individual files with YYYYMMDD-HHMM-slug.md naming for decisions, lessons, and sessions. Each gets its own file.

## Consequences

**Positive:** Conflict-free git collaboration. Atomic commits. Clear chronology. Easy to reference specific items.

**Negative:** More files to manage. Directory can grow large. Requires archival strategy.
