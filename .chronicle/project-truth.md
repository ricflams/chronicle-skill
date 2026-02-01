---
type: project-truth
created: 2026-02-01
updated: 2026-02-01
---

# Chronicle Skill: Regenerative Source of Truth

*Last Updated: 2025-02-01*
*Status: Active Development*

---

## Executive Summary

**What:** A Claude skill that initializes comprehensive project documentation systems enabling long-term AI-assisted collaboration through task organization, journey documentation, and context preservation.

**Why:** Long-running AI-assisted projects fail when context is lost between sessions. Chronicle solves this by treating documentation as the source of truth - comprehensive enough that anyone (human or AI) can pick up exactly where work left off, even after extended breaks.

**Who:** Developers and creators working on complex projects with AI assistance, especially those spanning multiple sessions, requiring team handoffs, or benefiting from explicit decision/failure documentation.

---

## Scope

### Objectives

1. **Enable seamless project continuity** across extended time gaps
   - Success: User returns after 3 months, reads 45min of docs, resumes productively
   - Success: Claude picks up context without 20min of "what is this project?" questions

2. **Capture why, not just what** through comprehensive journey documentation
   - Success: New team member understands not just code but reasoning behind decisions
   - Success: Failed approaches are documented to prevent repeating mistakes

3. **Provide practical task organization** integrated with AI collaboration
   - Success: Never ask "what should I work on next?"
   - Success: Tasks automatically tracked through completion

4. **Create self-contained, skill-independent documentation**
   - Success: After initialization, skill can be removed - project still works
   - Success: All protocols visible and customizable in CLAUDE.md

### Requirements

**Functional:**
- Initialize `.chronicle/` directory structure (10 files across 4 subdirectories)
- Conduct adaptive 3-phase questioning (15-28min) to populate initial context
- Write complete operating protocols to CLAUDE.md (200+ lines)
- Create user-facing guide (USING-CHRONICLE.md)
- Auto-detect project type (software/DIY/creative) and adapt accordingly
- Manage task workflow (detection, completion, archiving)
- Support quick and deep entry modes for problems/decisions
- Enable weekly compression of session logs into project-truth.md

**Non-Functional:**
- Bootstrap time: 15-30 minutes (acceptable for long-term value)
- Documentation should be readable by humans and navigable by AI
- All files must be plain markdown (no proprietary formats)
- System must work without internet/external dependencies after init

### Constraints

**Technical:**
- Claude skills framework (markdown-based, no code execution)
- Must work across different Claude instances/sessions
- Cannot rely on Claude's memory features
- File-based only (no databases, no external services)

**Design:**
- Universal applicability (software, DIY, presentations, creative projects)
- Self-documenting (clear file names, obvious purposes)
- Low friction (natural language commands, minimal ceremony)

**Business:**
- Publishable as open-source skill
- Must compete with simpler alternatives (project-memory skill exists)
- Value prop must justify 15-30min setup time

### Non-Goals

- **Not a project management system** - No sprints, no burndown charts, no time tracking beyond basic duration
- **Not a knowledge base** - Focused on single project context, not cross-project learning
- **Not a git replacement** - Complements git, doesn't replace it
- **Not prescriptive about methodologies** - Works with any dev approach
- **Not automatic** - Requires user to "update chronicle" at session end (intentional)

---

## Context Foundation

### System Overview

Chronicle creates a `.chronicle/` directory with individual task files and organized documentation across 4 conceptual layers:

**Truth Layer** (what/why):
- `project-truth.md` - Compressed source of truth with scope, context, evolution
- `.chronicle/tasks/` - Individual task files (one per task, numbered NNNN-name.md)

**Context Layer** (structure/decisions):
- `context/visuals/` - Diagrams, sketches, mood boards (format varies by project type)
- `context/decisions/` - ADRs (Architectural Decision Records) with index

**Journey Layer** (history/learnings):
- `journey/session-log.md` - Detailed chronicle of what happened each session
- `journey/completed-tasks/` - Completed task files (moved from tasks/ when done, excluded from AI context)
- `journey/lessons.md` - Problems + experiments + insights (merged from 3 files)

**Execution Layer** (how we work):
- `execution/parts-manifest.md` - Components/materials/slides (adaptive terminology)
- `execution/key-patterns.md` - Recurring techniques and approaches
- `execution/key-facts.md` - Config, URLs, ports (non-sensitive reference data)
- `execution/validation-strategy.md` - Testing/acceptance criteria

**Core Parts:**
- **Skill (SKILL.md)**: Bootstrap mechanism that transfers knowledge and exits
- **Protocols (in CLAUDE.md)**: Complete operating instructions for Claude
- **User Guide (USING-CHRONICLE.md)**: Human-readable usage documentation
- **Templates**: Reference implementations for all file formats

### Key Design Decisions

**DEC-001: Skill bootstraps then exits**
- Rationale: Self-contained projects must work without skill dependency
- Alternative: Keep skill active throughout - rejected (breaks if skill unavailable)
- Consequence: Protocols must be comprehensive and in CLAUDE.md

**DEC-002: Protocols in CLAUDE.md, not separate .chronicle/protocols.md**
- Rationale: CLAUDE.md is automatically loaded, separate file requires conscious tool call
- Alternative: Indirection via separate protocols file - rejected (unreliable, Claude forgets)
- Consequence: CLAUDE.md gets 200+ lines longer, but reliability is worth it

**DEC-003: 10-file structure (consolidated from 18)**
- Rationale: Balance between organization and simplicity
- Eliminated: context/overview.md, protocols/, split scope files, split failure-tracking files
- Merged: scope → project-truth.md, problems+learnings+experiments → lessons.md
- Consequence: Fewer concepts to track, related information together

**DEC-004: active-tasks.md at .chronicle/ top level**
- Rationale: Different time orientation (future) than journey/ (past)
- Alternative: Keep in journey/ - rejected (conceptual mismatch)
- Consequence: Very visible, signals importance, clear separation present/past

**DEC-005: completed-tasks.md excluded from AI context**
- Rationale: session-log.md has detailed completion info; archive is for human progress tracking
- Alternative: Include in context - rejected (context pollution)
- Consequence: Humans get progress view, AI gets narrative from session-log

**DEC-006: Name change from "regenerative-memory" to "chronicle"**
- Rationale: "Regenerative-memory" felt cold/technical, "chronicle" is warm/evocative
- Considered: 20 alternatives (memory-trail, project-memoir, living-history, etc.)
- Consequence: Better marketing, clearer purpose (recording the journey)

**DEC-007: .chronicle/ not .ai/**
- Rationale: Branded, semantic, memorable
- Alternative: .ai/ - rejected (generic, not descriptive)
- Consequence: Immediately clear what the folder contains

**DEC-008: Universal with auto-detection, not project-type selection**
- Rationale: Lower friction, adapts naturally
- Alternative: Explicit "software/DIY/presentation" choice - rejected (extra step)
- Consequence: Smart defaults, software projects get enhanced features automatically

---

## Regeneration Instructions

**To recreate this skill from scratch:**

1. **Read this file** (`project-truth.md`) completely - understand philosophy and decisions
2. **Review conversation transcript** (if available) - see how design evolved
3. **Study decisions** in `.chronicle/context/decisions/` - understand why choices were made
4. **Read session log** - see implementation sequence and challenges
5. **Create SKILL.md** following chronicle skill patterns from this doc
6. **Generate templates** for all file types (use examples from this chronicle)
7. **Write bootstrap logic** implementing 4-phase initialization
8. **Test** with software/DIY/creative projects to verify universality

**Key principle:** From this chronicle, the skill should be recreatable even if all code is lost.

---

## Quick Start for New Team Members

**"I just found this skill project, what do I need to know?"**

1. **Read:** This file (project-truth.md) - 25 min
2. **Skim:** Recent session log entries - 10 min  
3. **Check:** Active tasks to see what's in progress - 2 min
4. **Browse:** Decision records to understand key choices - 10 min

**Total onboarding time:** ~45 minutes to productive contribution

**The skill's job:** Initialize comprehensive documentation for long-running AI-assisted projects.

**Current status:** Design complete, ready for implementation.

**Next steps:** Implement SKILL.md, create all templates, test with multiple project types.

---

## Metadata

**Created:** 2025-02-01
**Last Major Revision:** 2025-02-01
**Primary Contributors:** Richard, Claude (Sonnet 4.5)
**Current Maintainer:** Richard
**Related Documentation:** See `.chronicle/` directory for complete context
