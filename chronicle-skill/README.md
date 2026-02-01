# Chronicle Skill

**The complete record of your project's journey**

A Claude skill that maintains project context in markdown files for AI-assisted collaboration.

---

## What is Chronicle?

Chronicle enables seamless project continuity through four core capabilities:

- Define the **project** — Helps you define the shape of what your building
- Organize **tasks** — Identify and keep track of individual tasks, to be tackled one by one
- Document the **journey** — Capture what happened - decisions, what worked or not, etc
- Preserve the **AI Context** — All of the above express your project and its state to an AI, across sessions

From your chronicle alone, anyone - human or AI - should be able to understand your project well enough to continue building it effectively.

---

## Quick Start

```
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

Plus 200+ lines of protocols in `CLAUDE.md` so Claude knows how to maintain it.

---

## Documentation

- **[SKILL.md](SKILL.md)** - Complete skill definition
- **[USING-CHRONICLE.md](USING-CHRONICLE.md)** - User guide with workflows and examples

---

## License

MIT
