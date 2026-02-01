# Components Manifest

*Key components that make up the chronicle skill*

---

## Core Skill Definition

### SKILL.md
**Purpose:** Main skill file that Claude reads to understand chronicle initialization

**Key Elements:**
- Metadata (name, description, version)
- 4-phase initialization logic
- Adaptive questioning framework
- Bootstrap instructions
- Template references

**Dependencies:** None (self-contained)

**Location:** Root of skill directory

---

## Templates

### claude-protocols.md
**Purpose:** Complete protocol template that gets inserted into CLAUDE.md

**Key Elements:**
- File structure documentation (200+ lines)
- Task management workflows
- Session end protocol
- Decision recording guidelines
- Context management rules

**Dependencies:** None

**Location:** templates/claude-protocols.md

### project-truth-template.md
**Purpose:** Template for project-truth.md with placeholder sections

**Key Elements:**
- Executive summary structure
- Scope sections (objectives, requirements, constraints, non-goals)
- Context foundation
- Development journey placeholders
- Implementation guide structure

**Dependencies:** Populated from Phase 1-3 Q&A

**Location:** templates/project-truth-template.md

### active-tasks-template.md
**Purpose:** Empty task board structure

**Key Elements:**
- In Progress section
- Ready to Start section
- Blocked section
- Backlog section

**Dependencies:** None (starts empty)

**Location:** templates/active-tasks-template.md

### session-log-template.md
**Purpose:** Template for session entries

**Key Elements:**
- Session header format
- Accomplished/Decisions/Learnings/Next Steps structure
- Example entries

**Dependencies:** Updated at session end

**Location:** templates/session-log-template.md

### lessons-template.md
**Purpose:** Template for problems/experiments/insights

**Key Elements:**
- Problems Encountered format (quick and deep)
- Experiments & Approaches Tried format
- Key Insights format

**Dependencies:** Updated when problems occur or learnings emerge

**Location:** templates/lessons-template.md

### adr-template.md
**Purpose:** Architectural Decision Record format

**Key Elements:**
- ADR header (number, title, date, status)
- Context and Problem
- Decision
- Alternatives Considered
- Consequences
- Implementation Notes

**Dependencies:** Created when significant decisions are made

**Location:** templates/adr-template.md

### using-chronicle-template.md
**Purpose:** User-facing guide template

**Key Elements:**
- What is chronicle (3 purposes)
- Quick reference
- Common workflows
- Structure explanation
- Tips & best practices
- Cheat sheet

**Dependencies:** None (static guide)

**Location:** templates/using-chronicle-template.md

---

## Documentation

### README.md
**Purpose:** Public-facing skill documentation

**Key Elements:**
- What is chronicle
- Quick start
- Philosophy
- Use cases
- After initialization
- Examples

**Dependencies:** None

**Location:** Root of skill directory

### docs/philosophy.md
**Purpose:** Deep dive into regenerative documentation concept

**Dependencies:** None

**Location:** docs/philosophy.md

### docs/comparison.md
**Purpose:** Compare chronicle vs project-memory vs other approaches

**Dependencies:** None

**Location:** docs/comparison.md

### docs/best-practices.md
**Purpose:** Tips for effective chronicle usage

**Dependencies:** None

**Location:** docs/best-practices.md

---

## Examples

### examples/software-project/
**Purpose:** Fully populated chronicle for a software project

**Key Elements:**
- Complete .chronicle/ structure
- CLAUDE.md with protocols
- USING-CHRONICLE.md
- Example session logs, ADRs, tasks

**Dependencies:** None (reference implementation)

### examples/diy-project/
**Purpose:** Fully populated chronicle for DIY/physical project

**Key Elements:**
- Adapted terminology (materials instead of components)
- Photos in context/visuals/
- Physical validation checklist

**Dependencies:** None (reference implementation)

### examples/presentation-project/
**Purpose:** Fully populated chronicle for presentation/creative work

**Key Elements:**
- Slide breakdown in parts-manifest
- Narrative arc in context
- Rehearsal in validation-strategy

**Dependencies:** None (reference implementation)

---

## Initialization Logic

### Phase 1: Foundation Questions
**Purpose:** Gather core project context (10 questions)

**Outputs:** Initial data for project-truth.md

### Phase 2: Depth Visualization
**Purpose:** Show completeness, let user choose deep dives

**Outputs:** List of areas to explore deeper

### Phase 3: Targeted Deep Dives
**Purpose:** 3-4 questions per selected area

**Outputs:** Comprehensive context for project-truth.md

### Phase 4: File Generation
**Purpose:** Create all chronicle files and write protocols

**Outputs:** Complete .chronicle/ structure, CLAUDE.md, USING-CHRONICLE.md

---

## Auto-Detection

### Software Project Detection
**Triggers:** Files like *.cs, *.js, package.json, *.csproj, src/

**Actions:**
- Generate architecture diagrams (if mermaid-diagrams skill available)
- Rename parts-manifest.md → component-manifest.md
- Rename validation-strategy.md → testing-strategy.md
- Use software terminology in templates

---

## Integration Points

### mermaid-diagrams skill (optional)
**Purpose:** Generate architecture diagrams for software projects

**Usage:** Called during Phase 4 if software project detected

### writing-clearly-and-concisely skill (optional)
**Purpose:** Improve documentation quality

**Usage:** Available for refining project-truth.md content
