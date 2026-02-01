# Chronicle Skill - Development Repository

This repository contains the development of the **chronicle** Claude skill.

## Repository Structure

```
chronicle-skill-repo/
├── chronicle-skill/          ← THE SKILL (pristine source for distribution)
│   ├── SKILL.md              (skill definition)
│   └── USING-CHRONICLE.md    (user guide)
│
├── .chronicle/               ← Development chronicle
│   └── ...                   (documents building this skill)
│
├── README.md                 ← This file
├── CLAUDE.md                 ← Project context for AI collaboration
└── LICENSE
```

## About the Skill

**Chronicle** maintains project context in markdown files for AI-assisted collaboration. Define scope and constraints, manage active tasks, document decisions and learnings. Everything in `.chronicle/` becomes the source of truth.

## For Skill Users

See [`chronicle-skill/SKILL.md`](chronicle-skill/SKILL.md) for the skill definition and [`chronicle-skill/USING-CHRONICLE.md`](chronicle-skill/USING-CHRONICLE.md) for usage documentation.

Quick start in your project:
```
"Initialize chronicle"
```

## For Skill Developers

This repository uses chronicle to document its own development (meta!).

- **Skill source**: [`chronicle-skill/`](chronicle-skill/) directory
- **Development docs**: [`.chronicle/`](.chronicle/) directory
- **Project context**: [`CLAUDE.md`](CLAUDE.md)

### Development Principle

The `.chronicle/` folder is treated like any other project using the skill - it documents the work of building and maintaining the skill itself. The `chronicle-skill/` folder contains the clean, distributable skill source.

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

In AI-assisted development, the AI-context becomes a primary artifact.

Chronicle treats the _curated context_ and the _journey of understanding_ as just as valuable as the produced artifacts. Code can be regenerated; understanding cannot.

**From your chronicle alone, someone should be able to recreate functionally equivalent work.**

---

## Use Cases

**Software Development**
- Any projects that's built with AI assistance
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

## Documentation

- **USING-CHRONICLE.md** - User guide (created in your project)

---

## Contributing

Chronicle is currently in development. Contributions welcome after v1.0 release.

---

## License

MIT

---

## Author

Richard Flamsholt
richard@flamsholt.dk

---

## Acknowledgments

Inspired by:
- Nate B Jones' domain memory pattern video
- The concept of regenerative documentation
- Real frustration with losing context in long-running AI projects

---

**Chronicle: Never lose context in long-running projects**
