# Chronicle Skill: Project Truth

## Purpose

Chronicle is a Claude skill that captures decisions, lessons, and project context from AI conversations and stores them in git-tracked markdown files. It supplements Claude's built-in memory with structured, searchable, team-visible records.

## Scope

**What it does:**
- Initializes `.chronicle/` directory with truth.md, principles.md, and folders for decisions/lessons/sessions
- Writes operating protocols to CLAUDE.md (~90 lines)
- Captures ADRs when significant decisions are made
- Logs lessons when failures or surprises occur
- Records session narratives for project timeline
- Auto-archives old sessions weekly, old lessons monthly

**What it doesn't do:**
- Task management (use Claude Tasks)
- AI context preservation (use Claude Memory)
- Replace git commits (complements with rationale)
- Sprint planning or time tracking

## Constraints

- Claude skills framework (markdown-based, no code execution)
- Must work across different Claude instances/sessions
- File-based only (no databases, no external services)
- Token budget: ~2.5K always-load, ~7K total selective

## Risks

1. **Overlap with Claude Memory** — Chronicle focuses on team-visible, git-tracked artifacts
2. **Adoption friction** — Mitigated by 30-second progressive disclosure initialization
3. **Merge conflicts** — Solved by timestamped individual files (YYYYMMDD-HHMM-slug.md)

## Current State

- **Status:** v2.0 complete — slimmed to decision-trail focus
- **Next:** Publish to GitHub, test with real projects

## Team

- **Creator:** Richard Flamsholt (richard@flamsholt.dk)
- **AI Partner:** Claude
