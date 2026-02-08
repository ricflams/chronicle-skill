# Progressive Disclosure Initialization

## Context

Chronicle v1 had a 15-28 minute "interview" for initialization. This felt heavy and deterred casual adoption.

## Decision

Replace elaborate interview with progressive disclosure:
- First session: Create structure in ~5 minutes with minimal questions
- Subsequent sessions: Claude prompts when decisions/lessons/sessions are worth capturing
- truth.md starts sparse, fills in organically

## Consequences

**Positive:** Low barrier to entry. Natural flow. Less upfront commitment.

**Negative:** Initial documentation has gaps. Requires discipline to fill in over time.
