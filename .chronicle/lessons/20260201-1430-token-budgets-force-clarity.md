# Token Budgets Force Clarity

**Tags:** #llm #design  
**Severity:** Low — optimization insight

## What Happened

Adding explicit token targets ("truth.md: ~1500-2000 tokens", "always-load: ~2.5K") forced conscious decisions about what detail level to include.

## Root Cause

Without constraints, documentation grows unbounded.

## What We Learned

Token budgets make tradeoffs explicit. When you know truth.md should be ~2000 tokens, you actively decide what's essential vs nice-to-have. The constraint improves quality by forcing prioritization.

## Prevention

Set explicit size targets for any document that will be loaded into AI context.
