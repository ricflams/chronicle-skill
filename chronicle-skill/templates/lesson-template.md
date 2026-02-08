---
date: YYYY-MM-DD
tags: [performance, database, testing, architecture, tooling, process]
severity: blocker  # blocker | gotcha | insight
team-impact: high  # high | medium | low
---

# [Lesson Title]

## What Happened

[Clear description of the situation, problem, or experiment]

## Why It Mattered

[Impact on project, team, or users. Why is this worth remembering?]

## What We Learned

[Key insight, pattern, or understanding gained]

## Action

- [Changes to make based on this lesson]
- [Patterns to adopt or avoid going forward]
- [Related decisions or documentation to update]

---

## Examples

### PostgreSQL Requires Explicit Indexes on Foreign Keys

**What Happened:** Query on users table took 45s in production. Forgot to add index on foreign key `team_id`.

**Why It Mattered:** Brought down production. Users couldn't log in for 20 minutes.

**What We Learned:** PostgreSQL doesn't auto-index foreign keys (unlike MySQL). Always add explicit index on FK columns.

**Action:**
- Added to validation checklist: verify indexes on all foreign keys
- See decision 20260115-1200-indexing-strategy.md for full approach
