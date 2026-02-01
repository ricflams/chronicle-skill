# Key Facts

*Configuration, references, and non-sensitive project data*

---

## Skill Metadata

**Name:** chronicle
**Version:** 1.0.0
**Type:** Claude skill (markdown-based)
**Repository:** (To be determined)
**License:** MIT (planned)

---

## File Structure

**Root directory:** chronicle-skill/
**Main skill file:** SKILL.md
**Templates directory:** templates/
**Examples directory:** examples/
**Documentation directory:** docs/

---

## Target Platforms

**Primary:** Claude.ai web interface
**Secondary:** Claude desktop app
**Compatibility:** Any Claude interface that supports skills

---

## Chronicle Directory Structure

**Directory name:** `.chronicle/` (hidden directory, branded)
**File count:** 10 core files
**Total directories:** 4 (context, context/decisions, context/visuals, journey, execution)

---

## Key File Sizes (Target)

**project-truth.md:** 2-4 pages (target), 6 pages max
**active-tasks.md:** 10-30 tasks (target), 50 tasks max
**session-log.md:** Growing (compress weekly), no limit
**completed-tasks.md:** Growing (human reference), no limit
**CLAUDE.md protocols:** ~200-250 lines
**USING-CHRONICLE.md:** ~1,400 words (~7 min read)

---

## Initialization Time

**Phase 1 (Foundation):** 3-5 minutes (10 questions)
**Phase 2 (Depth viz):** 2-3 minutes (progress bars + selection)
**Phase 3 (Deep dives):** 10-20 minutes (adaptive)
**Phase 4 (Summary):** 2-3 minutes (validation)

**Total:** 15-28 minutes (varies by project complexity)

---

## Protocol Sections

1. File structure documentation
2. Before starting work checklist
3. Task management workflow
4. Session end protocol (7 steps)
5. Decision recording (ADR format)
6. Problem logging (quick/deep modes)
7. Context management rules
8. Task detection during planning
9. Regeneration principle

**Total lines:** ~200-250 in CLAUDE.md

---

## Dependencies

**Required:** None (fully self-contained)

**Optional integrations:**
- mermaid-diagrams skill (for architecture diagrams)
- writing-clearly-and-concisely skill (for doc quality)
- csharp-architecture skill (for .NET projects)

---

## Context Management

**Always in AI context:**
- project-truth.md
- active-tasks.md
- context/* (all subdirectories)
- journey/session-log.md
- journey/lessons.md
- execution/* (all files)

**Never in AI context:**
- journey/completed-tasks.md
- USING-CHRONICLE.md

---

## Project Type Detection

**Software project triggers:**
- Files: *.cs, *.js, *.ts, *.py, *.java, *.go
- Config: package.json, *.csproj, *.sln, pom.xml, go.mod
- Directories: src/, lib/, app/, components/

**Actions when detected:**
- Generate architecture diagrams (if mermaid-diagrams available)
- Rename parts-manifest.md → component-manifest.md
- Rename validation-strategy.md → testing-strategy.md
- Use software-specific terminology

---

## Terminology Adaptations

| Universal | Software | DIY | Presentation |
|-----------|----------|-----|--------------|
| Parts | Components | Materials | Slides |
| Validation | Testing | Inspection | Rehearsal |
| Problems | Bugs | Issues | Roadblocks |
| Context | Architecture | Layout | Narrative |

---

## Session End Steps

1. Summarize session
2. Update session-log.md
3. Move completed tasks
4. Create ADRs (if significant decisions)
5. Update diagrams (if structure changed)
6. Document problems in lessons.md
7. Weekly: Compress into project-truth.md (>7 days check)

---

## File Extensions

**All chronicle files:** .md (markdown)
**Diagrams:** .mmd (Mermaid) or .jpg/.png (photos/sketches)
**No proprietary formats** - everything plain text and images

---

## Design Constraints

**Technical:**
- Must work offline after initialization
- No external API dependencies
- No database required
- Claude skills framework only

**User Experience:**
- Setup time must be <30 minutes
- Natural language commands
- No complex syntax to learn
- Files directly editable

---

## Comparison to Alternatives

**vs project-memory skill:**
- Chronicle: Strategic, comprehensive, regenerative
- project-memory: Tactical, quick-reference, day-to-day
- **Don't use both** (75% overlap, confusing)

**vs Git commit messages:**
- Chronicle: Why decisions were made, what failed, comprehensive context
- Git: What changed, code-level details
- **Complementary** (use both)

**vs Documentation tools:**
- Chronicle: Integrated with AI workflow, living documentation
- Tools: External systems, often stale
- **Chronicle better** for AI-assisted projects

---

## Success Metrics

**Onboarding time:** New team member productive in <45 minutes of reading
**Context rebuild:** User returns after 3-month break, resumes in <20 minutes
**Self-sufficiency:** Project works without skill after initialization
**Regeneration:** From chronicle alone, functionally equivalent work is recreatable

---

## Known Limitations

- Not automatic (requires "update chronicle" at session end)
- No cross-project knowledge sharing
- No time tracking beyond basic task duration
- No integration with external PM tools
- Requires discipline to maintain

---

## Related Skills

**Complementary (use together):**
- mermaid-diagrams (for visualizations)
- brainstorming (for design exploration)
- critical-thinking (for decision analysis)
- writing-clearly-and-concisely (for doc quality)
- csharp-architecture (for .NET projects)

**Incompatible (don't use together):**
- project-memory (overlaps, causes confusion)

---

## Tagline Options

**Primary:** "The complete record of your project's journey"

**Alternatives:**
- "Never lose context in long-running projects"
- "Your project's history becomes its memory"
- "Document once, remember forever"
