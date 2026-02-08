# Calendar-Based Archival

## Context

Old sessions and lessons accumulate, bloating context. Need automatic archival that works for teams without coordination.

## Decision

Use deterministic calendar-based rules:
- Sessions: Every Monday OR files >21 days → archive files >14 days
- Lessons: 1st of month OR files >90 days → archive files >60 days
- Decisions: Never archive (timeless)

## Consequences

**Positive:** No coordination needed — every team member uses same rules. Predictable. Keeps context lean.

**Negative:** Less flexibility. Important sessions might archive "too soon" (can be un-archived manually).
