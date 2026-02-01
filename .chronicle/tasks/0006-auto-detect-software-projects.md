# Task: Add auto-detection for software projects

**Created:** 2025-02-01 by Richard

## Description

Detect software projects and adapt terminology automatically.

## Detection Signals

- Code files: *.cs, *.js, *.ts, *.py, *.java, *.go
- Config files: package.json, *.csproj, *.sln, pom.xml, go.mod
- Directories: src/, lib/, app/, components/

## Adaptations

- Rename parts-manifest.md → component-manifest.md
- Use software-specific terminology
- Add architecture diagram generation (if mermaid-diagrams available)
