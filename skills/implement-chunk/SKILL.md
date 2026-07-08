---
name: implement-chunk
description: Implement a single roadmap chunk following TDD
metadata:
  author: Kirit Sælensminde
---

You are implementing a single chunk from a roadmap document produced by the `roadmap` skill.

Arguments: $ARGUMENTS

## Resolve the arguments

The arguments contain a **roadmap file path** (required) and an optional **chunk id** (e.g. `1.2`).

- A chunk id matches `N.N` — digits, a dot, digits. The path is the other argument (ends in `.md` or contains `/`). Occasionally a chunk that has been split will have a final letter, e.g. 1.1a and 1.1b would be two new chunks from a split 1.1 chunk.
- Order does not matter — identify each argument by its shape.

1. Read the roadmap file. If no path was given or the file does not exist, stop and report it — do not guess at a roadmap.
2. Select the target chunk:
   - If a chunk id was given, use that chunk. If it is not in the roadmap, stop and list the available chunk ids.
   - If no chunk id was given, use the first chunk (top to bottom) that still has any unchecked `* [ ]` boxes. If every chunk is fully checked, stop and say so.

## Implement the chunk

Work strictly within the scope of the selected chunk — do not begin any other chunk. If the chunk seems too large for a single commit then stop and ask.

Follow TDD order, exactly as the chunk lists it:

1. **Tests first.** Write each test under the chunk's **Tests:** list before touching implementation. Reference the real files and existing test patterns in the codebase.
2. **Implementation.** Write the code under the chunk's **Implementation:** list to make those tests pass. Reuse existing utilities and conventions rather than inventing new ones.
3. **Run the tests.** Use the project's own test command. Iterate until the chunk's tests pass and you have not broken any previously-passing tests — the codebase must be left in a working state.

## Rules

- Implement **only** the selected chunk. Leave the roadmap document untouched — do not check off its boxes.
- Do not commit. Stop once the tests are green and report the result.
- Match the surrounding code's style, naming, and structure. Do not introduce a new pattern where an existing one fits.
- If a chunk step is ambiguous or conflicts with the codebase, stop and ask for clarification.
- If you cannot get the tests to pass, stop and explain what is blocking — do not weaken assertions or skip tests to force a green run.

## When done

Report concisely:

- Which chunk you implemented (id and name).
- The files you created or changed.
- The test command you ran and its result (pass/fail counts).
- Any decisions or deviations the user should know about.

Begin now. Do not restate these instructions — resolve the arguments and start implementing.
