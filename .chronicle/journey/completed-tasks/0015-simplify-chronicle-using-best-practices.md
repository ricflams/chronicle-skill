---
type: task
created: 2026-02-01
status: completed
---

# Task: Simplify Chronicle Using Established Best Practices

**Created:** 2026-02-01 by Richard  
**Completed:** 2026-02-01  
**Status:** ✅ Complete

## Description

Chronicle has over-engineered ADRs (9 sections vs original 3-section format) and lacks token efficiency. Apply proven methodologies (original ADR format by Michael Nygard, PARA model by Tiago Forte, frontmatter metadata, conventional commits) to reduce token burden while preserving regenerative value and collaboration.

Research findings:
- Original ADR format is deliberately lightweight (3 sections: Context, Decision, Consequences)
- Chronicle's current 9-section template is heavier than industry standard
- PARA methodology (Purpose/Areas/Resources/Archives) provides clearer mental model
- Frontmatter metadata enables token-efficient scanning
- Two-tier context loading (Essential vs On-Demand) addresses token limits
- Estimated current token burden: 20K-40K for mature projects

## Steps

1. Replace verbose ADRs with two-tier system - Create context/principles.md template for quick decisions using Y-statement format ("In context of X, facing Y, we decided Z, accepting tradeoff"). Add optional indented bullet list below each principle for elaboration when needed. Archive existing 11 detailed ADRs to context/decisions-archive/ (excluded from context). For major decisions, create simplified 3-section ADR template (Context, Decision, Consequences) matching Nygard's original pattern. Update templates and SKILL.md to document both formats.

2. Add YAML frontmatter to all chronicle files - Update all templates (task-file-template.md, session-log.md, lessons.md, and new principles.md) to include structured metadata at top (created, status where relevant). Update SKILL.md to show frontmatter examples. Enables token-efficient scanning, better AI parsing, progressive disclosure pattern.

3. Compress session-log with conventional commit format - Restructure session-log.md template to use `type(scope): description` format (feat, fix, docs, refactor, chore). Add protocol: keep only last 2-3 sessions with 300-line threshold. Auto-archive older entries to journey/session-archive.md (excluded from context). Extract major learnings to lessons.md during compression. Update claude.md protocols with compression trigger.

4. Rename 4-layer architecture using PARA inspiration - Update SKILL.md to rename layers: Truth Layer → **Purpose Layer** (project-truth.md, tasks/), Context Layer → **Resources Layer** (context/decisions/, context/visuals/), Journey Layer → **Archive Layer** (journey/), Execution Layer → **System Layer** (execution/). Align with Tiago Forte's proven PARA methodology. Update all template references and directory descriptions.

5. Define two-tier context loading in protocols - Update claude.md "Before Starting Work" to specify **Essential context** (project-truth, tasks/*, principles.md, lessons.md, key-facts.md - estimated 5K tokens) vs **On-Demand context** (session-log, validation-strategy, parts-manifest when needed - estimated 15K tokens). Add token budget guidance to project-truth.md template with file size targets and compression triggers.

6. Update SKILL.md with methodology references - Add "Foundations" section crediting: Michael Nygard (ADRs), Tiago Forte (PARA model), Tom Preston-Werner (README-driven development), Simon Brown (just-enough architecture), Conventional Commits. Replace current 9-section ADR template documentation with simplified 3-section original format. Document token efficiency as explicit design goal. Add references to principles.md as primary decision format.

7. Dogfood the changes in this repository - Move .chronicle/context/decisions/000*.md files to .chronicle/context/decisions-archive/. Create .chronicle/context/principles.md using Y-statement format to consolidate the 11 existing decisions. Update .chronicle/journey/session-log.md to use conventional commit format for current session. Add frontmatter to active .chronicle files (project-truth.md, lessons.md, session-log.md).

8. Sync updated SKILL.md to root - Copy chronicle-skill/SKILL.md to root SKILL.md after all changes complete.

## Success Criteria

- ✅ principles.md template created with Y-statement format and optional detail bullets
- ✅ Simplified 3-section ADR template replaces 9-section version
- ✅ All templates have YAML frontmatter
- ✅ Session-log template uses conventional commit format with compression protocol
- ✅ 4 layers renamed to Purpose/Resources/Archive/System
- ✅ Two-tier context loading documented (Essential vs On-Demand)
- ✅ Foundations section added with methodology credits
- ✅ Token efficiency documented as design goal
- ✅ This repository's .chronicle/ dogfoods all changes
- ✅ Root SKILL.md synced

## Notes

This is a major architectural refinement grounded in research of established methodologies. The goal is to reduce token burden from estimated 20K-40K to under 10K for typical projects while maintaining Chronicle's regenerative value and collaborative workflows.
