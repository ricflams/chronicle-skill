# Protocols in CLAUDE.md

## Context

Chronicle needs to provide complete operating instructions for Claude. Where should these ~90 lines of protocols live? The skill bootstraps and exits — it can't be relied upon for ongoing operation.

## Decision

Write complete chronicle protocols directly into CLAUDE.md during initialization, wrapped in HTML comment region markers.

## Consequences

**Positive:** Reliable — CLAUDE.md is always loaded automatically. Self-contained. Consistent behavior every session. Zero tool calls needed.

**Negative:** CLAUDE.md gets ~90 lines longer. Protocols not centrally updateable across projects.
