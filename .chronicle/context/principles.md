---
type: principles
created: 2026-02-01
---

# Project Principles

Quick decisions and core principles that guide chronicle-skill development.

## Format

**Y-Statement:** In the context of [situation], facing [concern], we decided for [option], to achieve [benefit], accepting [tradeoff].

---

## Principles

### Bootstrap & Initialization

**Bootstrap-and-exit pattern:** In the context of skill initialization workflows, facing the need for skills to remain available post-init, we decided for complete self-contained bootstrap that exits after setup, to achieve skill independence and clean handoff to CLAUDE.md protocols, accepting that skill cannot assist post-initialization.

**Protocols in CLAUDE.md:** In the context of AI collaboration patterns, facing fragmentation of instructions across multiple skill files, we decided for centralizing all operating protocols in CLAUDE.md, to achieve single source of truth and consistent AI behavior, accepting that CLAUDE.md becomes large (~200 lines).

### Documentation Structure

**Individual task files:** In the context of task management, facing merge conflicts and poor git collaboration with monolithic active-tasks.md, we decided for individual task files using 4-digit numbering (NNNN-task-name.md), to achieve atomic git operations and parallel task creation, accepting directory clutter with many active tasks.

**Dogfooding principle:** In the context of building documentation system, facing drift between what skill creates vs what repo actually uses, we decided for chronicle-skill repository to dogfood its own chronicle system, to achieve alignment and credible examples, accepting overhead of maintaining both pristine skill and working chronicle.

**Token efficiency as design goal:** In the context of LLM context limits, facing 20K-40K token burden from verbose ADRs and session logs, we decided for two-tier context loading with compressed formats, to achieve <10K typical project context, accepting loss of some narrative richness.
- Replaced 9-section ADR template with 3-section original format
- Created Y-statement format for quick decisions (principles.md)
- Added YAML frontmatter for scannable metadata
- Session log compression at 300 lines
- Essential vs on-demand context tiers

**PARA-inspired layer naming:** In the context of chronicle architecture, facing unclear purpose of 4-layer structure, we decided for Purpose/Resources/Archive/System naming aligned with PARA methodology, to achieve familiar mental model and clearer intent, accepting deviation from original Truth/Context/Journey/Execution names.

### Development Workflow

**Planning mode integration:** In the context of task creation workflow, facing manual mode switching friction, we decided for explicit handoff prompt ("Ready to implement? Switch to agent mode and say 'add the task'"), to achieve clear transition guidance, accepting extra step in workflow.

**Standardized numbering:** In the context of file identification, facing inconsistency between 3-digit ADRs and 4-digit tasks, we decided for universal 4-digit numbering (0001-9999), to achieve consistency and larger namespace, accepting need to rename existing files.

### Methodology Grounding

**Building on prior art:** In the context of system credibility, facing perception as "yet another custom framework", we decided for explicitly crediting established methodologies (Nygard's ADRs, Forte's PARA, Preston-Werner's README-driven, Brown's just-enough architecture), to achieve grounding in proven patterns, accepting that we're no longer claiming full originality.

---

## Notes

See `.chronicle/context/decisions-archive/` for historical detailed ADRs (0001-0011) that informed these principles.
