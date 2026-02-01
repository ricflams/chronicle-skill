# Task: Fix Chronicle Dogfooding Structure

**Created:** 2026-02-01 by Richard

## Description

The repository violates its own chronicle principles. The tasks/ folder is at project root instead of `.chronicle/tasks/`, and USING-CHRONICLE.md is missing from root. Fix the structure so `.chronicle/` looks exactly like a project that was initialized with chronicle.

## Steps

1. Move tasks/ → .chronicle/tasks/ (11 task files)
2. Copy chronicle-skill/USING-CHRONICLE.md → root USING-CHRONICLE.md
3. Update CLAUDE.md path references (6 locations: lines 64, 71, 87, 96, 98, 112)
4. Update .chronicle/project-truth.md path references
5. Create .chronicle/context/decisions/011-dogfooding-principle.md
6. Update .chronicle/context/decisions/index.md

## Principle

chronicle-skill/ must contain the full pristine distributable skill, and the repo itself should appear as if the skill had initialized it.
