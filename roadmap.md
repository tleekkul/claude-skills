---
description: Plan a feature as phases and commit-sized chunks
argument-hint: [goal description]
model: opus
allowed-tools: Read, Glob, Grep, Bash(git:*)
---

You are producing a structured implementation roadmap for the following goal:

> $ARGUMENTS

## Instructions

First, explore the codebase to understand:
- Relevant existing code, patterns, and conventions
- What already exists that can be reused
- Where new code will need to live

Then produce a roadmap document in the exact format below.

## Output Format

Produce a markdown document with this structure:

---

# Roadmap: [concise goal title]

## Context
[1-3 sentences: the problem or need, and the intended outcome]

## Phase 1: [Name] — [one-line description of what is deliverable and working at the end]

### Chunk 1.1: [Name]

**Tests:**
* [ ] [test description — what behaviour is being verified]
* [ ] [...]

**Implementation:**
* [ ] [specific step with file path where relevant]
* [ ] [...]

---

### Chunk 1.2: [Name]
[same structure]

---

## Phase 2: [Name] — [deliverable description]
[same structure]

---

## Notes
[Any cross-cutting concerns, risks, or sequencing constraints]

---

## Rules for the output

- Phases are numbered from 1.
- Chunks are numbered as Phase.Chunk (e.g. 1.1, 1.2, 2.1).
- All bullet points within chunks use `* [ ]` so they can be checked off as work progresses.
- Every chunk must be small enough to be a single focused commit, and must leave all tests passing — the codebase is always in a working state after each chunk.
- Tests come before implementation in each chunk (TDD order).
- Phases represent a complete deliverable: a meaningful, usable increment where development could pause indefinitely before continuing to the next phase.
- Reference real file paths from the codebase, not hypothetical ones.
- Reuse existing utilities and patterns — note them explicitly.
- Do not include implementation details that belong in code comments.

Write the roadmap document now. Do not summarise what you are about to do — output the document directly.
