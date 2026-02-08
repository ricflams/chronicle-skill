# Complement Don't Compete

## Context

Claude has built-in Memory and Tasks features. Chronicle v1 overlapped significantly with these (~60% redundant by analysis).

## Decision

Slim Chronicle to focus only on what Claude Memory doesn't provide:
- Team-visible, git-tracked artifacts
- Structured decision history (ADRs)
- Searchable lessons learned
- Session narratives for project timeline

Drop task management entirely. Don't claim to preserve AI context (Claude Memory does that).

## Consequences

**Positive:** Clear value proposition. No redundant features. Honest positioning.

**Negative:** Narrower scope. Fewer features to market. Depends on users understanding the distinction.
