# Research Validates and Simplifies

**Tags:** #methodology #design  
**Severity:** Medium — would have shipped over-engineered

## What Happened

Chronicle had organically developed a 9-section ADR template, thinking thoroughness was better. Research into Michael Nygard's original ADR pattern revealed he deliberately used only 3 sections.

## Root Cause

Assumed more structure = more thorough. Didn't check established patterns first.

## What We Learned

Research pays off. Investigating established methodologies (Nygard's ADRs, PARA, conventional commits) provided both validation for what we got right and simplification paths for what we over-engineered. Building on prior art strengthens credibility while reducing complexity.

## Prevention

Before finalizing any pattern: "Is there established prior art? What did they learn that we can borrow?"
