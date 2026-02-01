# ADR-010: Individual Task Files

**Date:** 2025-02-01
**Status:** Accepted
**Context:** Task management and team collaboration

## Context and Problem

Chronicle's centralized `active-tasks.md` file creates problems for team collaboration:
- **Git conflicts**: Multiple people editing same file simultaneously
- **Cramped view**: N detailed task plans in single file becomes overwhelming
- **Poor diffs**: Hard to see what changed (task added vs modified vs moved)
- **Atomic operations**: Can't review/approve tasks individually
- **Archive bloat**: `completed-tasks.md` grows unbounded

Current structure:
```
.chronicle/
├── active-tasks.md           # All active tasks (can get large)
└── journey/
    └── completed-tasks.md    # All completed tasks (grows forever)
```

## Decision

**Replace centralized task files with individual task files:**

```
.chronicle/
├── tasks/                    # Active tasks (one file per task)
│   ├── 0001-task-name.md
│   ├── 0002-other-task.md
│   └── 0003-another-task.md
└── journey/
    └── completed-tasks/      # Completed tasks (moved here when done)
        ├── 0001-task-name.md
        └── 0004-old-task.md
```

**Task file format** (minimal):
```markdown
# Task: [Task name]

**Created:** YYYY-MM-DD by [Creator Name]

## Description

[Task description and plan details]

## [Optional sections]

Details, requirements, steps, etc.
```

**Numbering**:
- Four digits: 0001, 0002, 0003, etc.
- Sequential increment from highest existing number
- Collision-tolerant: Multiple tasks can have same number (different names)
  - Example: `0042-feature-a.md` and `0042-feature-b.md` both valid
  - Happens when two collaborators create tasks independently
  - System accepts duplicates - no conflict

**Workflows**:
- **List tasks**: "List tasks" / "Show tasks" → scan `tasks/` folder, display numbered overview
- **Create task**: Generate next number, create file with creator/timestamp
- **Complete task**: Move file from `tasks/` → `journey/completed-tasks/`
- **No status tracking**: All files in `tasks/` are "active" (any can be picked)

## Alternatives Considered

**Option A: Keep centralized active-tasks.md with sections**
- Pro: Single file to check
- **Con: Git conflicts in teams** - Major blocker
- **Con: Hard to review task changes** - Full file diff
- **Con: Grows large** - Harder to navigate
- **Why rejected:** Doesn't scale for collaboration

**Option B: Task subdirectories for status (tasks/ready/, tasks/in-progress/, tasks/blocked/)**
- Pro: Visual status organization
- **Con: Moving files between dirs for status changes** - Friction
- **Con: Git diffs unclear** - File moved or status changed?
- **Con: Over-engineered** - Status tracking beyond "pick and do"
- **Why rejected:** Unnecessary complexity

**Option C: Task files with frontmatter status metadata**
- Pro: Status in file itself
- **Con: Requires parsing** - Can't just list directory
- **Con: Still doesn't solve git conflicts** - Same file edited
- **Why rejected:** Doesn't solve core problem

**Option D: Individual task files (chosen)**
- **Pro: No git conflicts** - Each task is atomic unit
- **Pro: Clean diffs** - See exactly what changed per task
- **Pro: Individual review** - Can approve tasks independently
- **Pro: Simple** - Directory listing shows all tasks
- **Pro: Collision-tolerant** - Duplicate numbers acceptable
- **Con: One extra step** - Must list to see overview
- **Con: More files** - But that's the point (atomic units)

## Consequences

**Positive:**
- ✅ Team collaboration friendly - No merge conflicts on task creation
- ✅ Atomic git operations - One task = one file = one commit
- ✅ Clean diffs - Exactly what task was added/modified/completed
- ✅ Scalable - Works for 3 tasks or 300 tasks
- ✅ Simple discovery - `ls tasks/` shows active work
- ✅ Collision-tolerant - Duplicate numbers gracefully handled
- ✅ Focused view - Read one task at a time

**Negative:**
- ❌ Extra command for overview - Can't glance at single file
- ❌ More files in repo - But improves git history
- ❌ Numbering gaps possible - If tasks completed out of order

**Mitigation:**
- Add "list tasks" command to protocols
- Numbering gaps are fine (numbers are IDs, not priorities)

## Implementation

**Migration from old structure:**
1. Convert `active-tasks.md` entries → `tasks/NNNN-name.md` files
2. Convert `completed-tasks.md` entries → `journey/completed-tasks/NNNN-name.md` files
3. Delete old `active-tasks.md` and `completed-tasks.md`
4. Update all CLAUDE.md protocols
5. Update SKILL.md structure definition
6. Update USING-CHRONICLE.md workflows

**Task commands:**
- "List tasks" - Show all active tasks
- "Create task: [name]" - New numbered task file
- "Pick next task" - Suggest highest priority from tasks/
- "[Task] is complete" - Move to completed-tasks/

## Related Decisions

- Supersedes ADR-004 (active-tasks.md elevation - no longer exists)
- Complements ADR-006 (completed-tasks excluded from AI context - now a directory)
