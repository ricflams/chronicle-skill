# Task: Sync SKILL.md with Implementation Reality

**Created:** 2026-02-01 by Richard

## Description

SKILL.md is the canonical source of truth for chronicle workflows, but significant implementation details have been added to CLAUDE.md and actual `.chronicle/` files that don't exist in SKILL.md. Additionally, SKILL.md references a `templates/` directory with 7 template files that don't exist.

## Changes Required

### 1. Update SKILL.md Task Architecture
- Replace all `active-tasks.md` references with `tasks/` folder approach (4 locations: lines 179-203, 224, 247)
- Add "List tasks" command documentation
- Add task file format specification (NNNN-task-name.md with creator/timestamp)
- Add task numbering system explanation
- Update Context Management section (line 224) to reference `tasks/*` and `completed-tasks/*`

### 2. Add Planning Mode Workflow to SKILL.md
- Insert new section documenting planning vs agent mode distinction
- Document "add the task" workflow
- Document queue vs start immediately pattern
- Include user phrases for task acceptance

### 3. Expand Protocol Definitions in SKILL.md
- Expand "Before Starting Work" from name-only to full checklist
- Update Session End Protocol to 8 detailed steps (currently 7 generic)
- Add detailed task management commands

### 4. Create templates/ Directory
Create `chronicle-skill/templates/` with 7 template files based on actual `.chronicle/` implementation:
- `claude-protocols.md` - Extract from current CLAUDE.md
- `project-truth.md` - Template from .chronicle/project-truth.md
- `task-file-template.md` - Individual task file format (replaces active-tasks.md)
- `session-log.md` - Template from .chronicle/journey/session-log.md
- `lessons.md` - Template from .chronicle/journey/lessons.md
- `using-chronicle.md` - Copy from root USING-CHRONICLE.md
- `adr-template.md` - Template from actual ADR files

### 5. Update SKILL.md Template References
- Update line 247 to reference `task-file-template.md` instead of `active-tasks.md`
- Verify all template references point to existing files

## Scope
- SKILL.md: ~15-20 edits across multiple sections
- Templates: 7 new files to create
- Ensures SKILL.md is the true source of truth
