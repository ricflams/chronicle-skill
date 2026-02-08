# Natural Language Principles

## Context

Chronicle v1 used Y-statement format for principles (In the context of X, facing Y, we decided Z...). This format isn't widely recognized and felt formulaic.

## Decision

Use natural language for principles with explicit tradeoffs. Format: "We always [principle]. [Why it matters.] *Tradeoff: [what we accept].*"

## Consequences

**Positive:** Reads naturally. Tradeoffs make reasoning visible. No learning curve.

**Negative:** Less structured. Harder to parse programmatically (if that ever mattered).
