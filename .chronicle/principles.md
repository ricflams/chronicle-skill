# Principles

Enduring beliefs that guide Chronicle's design. Each principle includes the tradeoff accepted.

---

**We always bootstrap and exit.** Chronicle transfers knowledge to CLAUDE.md and the .chronicle/ folder, then becomes unnecessary. Projects work forever even if the skill disappears. *Tradeoff: No automatic protocol updates — each project is frozen at initialization version.*

**We put protocols directly in CLAUDE.md.** Indirection via separate files is unreliable — Claude might forget to read them. CLAUDE.md is automatically loaded. *Tradeoff: CLAUDE.md gets ~90 lines longer.*

**We use individual timestamped files.** Decisions, lessons, and sessions each get their own file with YYYYMMDD-HHMM-slug naming. This enables conflict-free git collaboration for teams. *Tradeoff: More files to manage; directory can grow large.*

**We archive automatically on calendar rules.** Sessions archive every Monday (files >14 days). Lessons archive on the 1st of each month (files >60 days). Decisions never archive. *Tradeoff: Less manual control; deterministic beats flexible.*

**We stay token-efficient.** Always-load core (truth.md + principles.md) stays under 2.5K tokens. Full selective load under 7K. Old content archives rather than accumulates. *Tradeoff: Some narrative richness is lost to compression.*

**We build on prior art.** Chronicle uses Michael Nygard's ADR pattern (3 sections, not 9), calendar-based archival, and progressive disclosure. We're not claiming originality — we're curating what works. *Tradeoff: Less "unique" positioning; more credibility.*

**We initialize through progressive disclosure.** First session: create structure in ~5 minutes. Subsequent sessions: Claude prompts when decisions/lessons/sessions are worth capturing. No elaborate interview. *Tradeoff: Initial truth.md has gaps; fills in organically.*

**We complement, not compete.** Chronicle adds structure and team visibility to Claude's built-in memory. We don't duplicate what Claude already does well. *Tradeoff: Narrower scope; fewer features.*
