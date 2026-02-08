# Token Efficiency as Design Goal

## Context

LLM context windows are limited. Chronicle v1 could load 15-20K tokens of project context. This crowds out room for actual work.

## Decision

Make token efficiency an explicit design goal:
- Always-load core (truth.md + principles.md) under 2.5K tokens
- Full selective load under 7K tokens
- Replace verbose formats with compact ones
- Archive older content automatically

## Consequences

**Positive:** More context window for actual work. Faster loading. Forces discipline in what's truly essential.

**Negative:** Some narrative richness lost. Less room for elaboration.
