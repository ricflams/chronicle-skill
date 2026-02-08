# Initial Over-Engineering

**Tags:** #design #architecture  
**Severity:** Medium — cost time but caught early

## What Happened

First Chronicle design had 18 files with heavy directory structure — felt overwhelming and hard to navigate.

## Root Cause

Tried to anticipate every possible use case upfront without validating complexity was needed.

## What We Learned

Start with minimum viable structure, add complexity only when justified by real use cases. Each round of file consolidation (18 → 11 → 10 → 4 core) made the system easier to understand without losing information.

## Prevention

Question every file: "Does this justify its existence?" If placement feels awkward in all locations, consider merging rather than adding.
