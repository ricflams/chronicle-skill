---
type: principles
created: YYYY-MM-DD
---

# Project Principles

Quick decisions and core principles that guide this project. Use this format for most decisions to keep context lightweight.

## Format

**Y-Statement:** In the context of [situation], facing [concern], we decided for [option], to achieve [benefit], accepting [tradeoff].

Optional detail bullets can be added below when elaboration is needed:
- Additional context or rationale
- Implementation notes
- Related considerations

---

## Principles

### Architecture & Design

**[Example]** In the context of choosing a database, facing scalability requirements, we decided for PostgreSQL, to achieve ACID compliance and proven scalability, accepting higher operational complexity than SQLite.

### Development Process

**[Example]** In the context of code review workflow, facing async team coordination, we decided for trunk-based development with feature flags, to achieve faster integration and reduced merge conflicts, accepting need for feature flag management.

### Technology Choices

**[Example]** In the context of frontend framework selection, facing team expertise and ecosystem maturity, we decided for React, to achieve strong ecosystem and hiring pool, accepting Facebook dependency and larger bundle size.

---

## When to Use Full ADR Instead

Use a full ADR (context/decisions/NNNN-name.md) when:
- Decision has significant long-term architectural impact
- Multiple complex alternatives need detailed comparison
- Decision requires stakeholder buy-in with full rationale
- Implementation strategy is non-trivial and needs documentation

For most decisions, Y-statements in this file are sufficient.

---

## Notes

- Keep principles terse and scannable
- Use detail bullets sparingly (only when really valuable)
- Link related principles: "See [principle above] regarding..."
- Archive outdated principles with ~~strikethrough~~ and "Superseded by: [new principle]"
