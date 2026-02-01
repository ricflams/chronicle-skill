# Decision Log

Quick reference for all architectural decisions. See individual ADR files for details.

---

- 2025-02-01: **Skill bootstraps then exits** - Self-contained projects work without skill dependency (see 001-bootstrap-and-exit.md)
- 2025-02-01: **Protocols in CLAUDE.md** - More reliable than indirection via separate file (see 002-protocols-in-claude-md.md)
- 2025-02-01: **10-file consolidated structure** - Balance organization and simplicity (see 003-10-file-structure.md)
- 2025-02-01: **Name: "chronicle"** - Warm and evocative over technical "regenerative-memory" (see 004-chronicle-naming.md)
- 2025-02-01: **.chronicle/ directory** - Branded and semantic vs generic .ai/ (see 005-chronicle-directory.md)
- 2025-02-01: **completed-tasks.md excluded from AI context** - Human reference only (see 006-completed-tasks-exclusion.md)
- 2025-02-01: **active-tasks.md at top level** - Different time orientation warrants elevation (see 007-active-tasks-elevation.md) **[SUPERSEDED by ADR-010]**
- 2025-02-01: **Universal with auto-detection** - Adapts automatically vs explicit type selection (see 008-universal-auto-detect.md)
- 2025-02-01: **Skill/development separation** - chronicle-skill/ for source, .chronicle/ for dogfooding (see 009-skill-development-separation.md)
- 2025-02-01: **Individual task files** - tasks/ folder with atomic task files, team-collaboration friendly (see 010-individual-task-files.md)
- 2026-02-01: **Dogfooding principle** - Repository structure must mirror chronicle output exactly (see 011-dogfooding-principle.md)
