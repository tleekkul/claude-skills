---
name: review-chunk
description: Review the work done for a single roadmap chunk
metadata:
  author: Kirit Sælensminde
---

You are reviewing the work done for a single chunk from a roadmap document produced by the `roadmap` skill — typically the chunk just built by the `implement-chunk` skill.

Arguments: $ARGUMENTS

## Resolve the arguments

The arguments contain a **roadmap file path** and a **chunk id** (e.g. `1.2`). Both are required.

- A chunk id matches `N.N` — digits, a dot, digits. The path is the other argument (ends in `.md` or contains `/`). Occasionally a chunk that has been split will have a final letter, e.g. 1.1a and 1.1b would be two new chunks from a split 1.1 chunk.
- Order does not matter — identify each argument by its shape.

1. Read the roadmap file. If no path was given or the file does not exist, stop and report it — do not guess at a roadmap.
2. Find the chunk by its id. If no chunk id was given, stop and ask for one. If the id is not in the roadmap, stop and list the available chunk ids.

## Review the work

You are reviewing, not implementing — **do not edit, write, or commit any code.** Only read the codebase, run the tests, and inspect the changes.

First identify what changed. The chunk is normally left uncommitted by `implement-chunk`, so `git diff` (and `git status`) against the working tree shows the work under review. If the working tree is clean stop and ask.

Check the work against the chunk's own **Tests:** and **Implementation:** lists:

1. **Completeness.** Was every Tests and Implementation item actually done? Flag anything listed but missing.
2. **Test quality.** Do the tests genuinely verify the behaviour described, or are they weakened, skipped, or asserting trivia? A passing-but-meaningless test is a finding.
3. **Correctness.** Does the implementation do what the chunk intends? Look for bugs, edge cases, and broken assumptions.
4. **Scope.** Did the work stay within this chunk? Flag changes that belong to a different chunk or that were not called for.
5. **Conventions.** Does the code match the surrounding style, naming, and existing utilities — or does it reinvent things the codebase already has?
6. **Reuse.** Does the implementation re-implement anything that is already available as a library function or elsewhere? Is there anything that should be lifted into a suitable library?
7. **Working state.** Run the project's own test command. Confirm the chunk's tests pass and that no previously-passing tests were broken.

## Output

Lead with a one-line **verdict**: `Pass`, `Pass with concerns`, or `Needs work`.

Then report:

- **Chunk:** id and name.
- **Findings:** each as a short bullet, ordered most to least important, with a `file:line` reference where relevant. Separate must-fix issues from optional suggestions.
- **Tests:** the command you ran and its result (pass/fail counts).

Be specific and concise. Do not restate the chunk back to the user, and do not pad the review with praise. If the work is clean, say so briefly and stop.

When the work passes without concerns (or the user overrides your concerns and asks you to commit anyway), then mark the checkboxes in the plan as done, and commit the work (with the plan if it's in the same repo) with a message which does not reference the plan document (e.g. do not use "Implements chunk 2.3").

Begin now. Do not restate these instructions — resolve the arguments and start reviewing.
