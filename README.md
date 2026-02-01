# Chronicle Skill

**The complete record of your project's journey**

A Claude skill that creates comprehensive, self-contained documentation systems for long-running AI-assisted projects.

---

## What is Chronicle?

Chronicle enables seamless project continuity through three core capabilities:

**📋 Task Organization** — Never ask "what's next?"  
**🗺️ Journey Documentation** — Capture why, not just what  
**🤖 AI Context Preservation** — Enable seamless collaboration across sessions

From your chronicle alone, anyone - human or AI - should be able to understand your project well enough to continue building it effectively.

---

## Quick Start

```
Initialize chronicle in your project directory:
"Initialize chronicle"
```

The skill will:
1. Ask comprehensive questions about your project (15-28 min)
2. Create `.chronicle/` directory with organized documentation
3. Write complete operating protocols to `CLAUDE.md`
4. Create `USING-CHRONICLE.md` user guide
5. Exit - you're now self-contained!

---

## What You Get

```
.chronicle/
├── project-truth.md       # Compressed source of truth
├── active-tasks.md        # Your work queue
├── context/               # Architecture & decisions
│   ├── visuals/
│   └── decisions/
├── journey/               # Session logs & learnings
│   ├── session-log.md
│   ├── completed-tasks.md
│   └── lessons.md
└── execution/             # How you work
    ├── parts-manifest.md
    ├── key-patterns.md
    ├── key-facts.md
    └── validation-strategy.md
```

Plus:
- Complete protocols in `CLAUDE.md` (200+ lines)
- User guide in `USING-CHRONICLE.md`

---

## Philosophy

> "Code is what the computer executes. Documentation is what the team executes. In AI-assisted development, documentation becomes the primary artifact."

Chronicle treats the journey of understanding as more valuable than the artifact. Code can be regenerated; understanding cannot.

**From your chronicle alone, someone should be able to recreate functionally equivalent work.**

---

## Use Cases

**Software Development**
- Multi-month projects with AI assistance
- Experiments and prototypes you might revisit
- Learning new frameworks or languages

**DIY & Physical Projects**
- Home renovations and improvements
- Crafting and making projects
- Garden planning and execution

**Creative & Professional Work**
- Presentations and pitches
- Research projects
- Writing projects
- Learning journeys

---

## After Initialization

The skill is no longer needed. Everything operates from `CLAUDE.md`:

```
"What should I work on?"    → Shows active tasks
"Mark task complete: X"     → Updates chronicle automatically
"Update chronicle"          → Session end protocol
```

---

## Features

✅ **Self-contained** - Works forever, even without the skill  
✅ **Comprehensive** - Captures objectives, decisions, learnings, failures  
✅ **Navigable** - Organized structure, not just logs  
✅ **Regenerative** - Documentation sufficient to recreate the work  
✅ **Universal** - Works for software, DIY, presentations, any project  
✅ **Transparent** - All files are markdown, directly editable  

---

## Development Status

**Current version:** 1.0.0 (in development)

This repository is itself documented using chronicle - we're dogfooding the system.

See `.chronicle/` directory for:
- Complete design documentation
- All decisions and rationale
- Development session logs
- What worked and what didn't

---

## Installation

*(Installation instructions will be added when skill is ready for release)*

---

## Examples

See `examples/` directory for fully populated chronicles:
- `software-project/` - HTTP client library
- `diy-project/` - Garden shed build
- `presentation-project/` - Investor pitch

---

## Documentation

- **USING-CHRONICLE.md** - User guide (created in your project)
- **docs/philosophy.md** - Deep dive into regenerative documentation
- **docs/comparison.md** - Chronicle vs alternatives
- **docs/best-practices.md** - Tips for effective use

---

## Contributing

Chronicle is currently in development. Contributions welcome after v1.0 release.

---

## License

MIT (planned)

---

## Author

Richard

---

## Acknowledgments

Inspired by:
- Nate B Jones' domain memory pattern video
- SpillwaveSolutions' project-memory skill
- The concept of regenerative documentation
- Real frustration with losing context in long-running AI projects

---

**Chronicle: Never lose context in long-running projects**
