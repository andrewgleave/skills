---
name: cleanse
description: >
  Review code for readability, then simplify it to be easy to follow and understand.
  Use this skill when the user wants to simplify code, improve readability, clean up
  for handoff, make code skimmable, reduce complexity, refactor for clarity, strip
  boilerplate, prepare code for future maintainers, or make a codebase easier to pick
  up. Trigger liberally — any request touching readability, simplification, cleanup,
  or "make this easier to understand" should use this skill. Also trigger when the user
  says things like "review this", "clean this up", "tidy this", "make this simpler",
  "reduce complexity", "flatten this", "strip the noise", or "I want to understand
  this code quickly next time I open it".
---

**Important** — Spawn a sub-agent to perform this review. Pass it only these instructions and the target files. The review is most effective when the agent starts with a clean context window.

## Scope

If the user specified files or directories, pass those to the sub-agent. If not, ask what they'd like you to review before proceeding.

## Goal

Make this code trivially easy to pick up cold. Someone opening this file in six months should understand what it does in seconds.
All changes should preserve the original functionality and behavior.

## What to look for

Read the target code carefully, then apply these passes in order. Make changes directly — don't list suggestions.

### 1. Flatten control flow

Nested conditionals are the single biggest readability killer. Flatten them.

- Convert if/else chains to early returns and guard clauses. Put the bail-out condition at the top, happy path below.
- When a function has a single meaningful path wrapped in a conditional, invert the condition and return early.
- If an else block just returns or continues, remove the else — the early return already handles it.

### 2. Strip noise

Remove anything that doesn't help the reader understand the code:

- **Comments that restate the code** — `// increment counter` above `counter += 1` is noise. Delete.
- **Redundant type annotations** — if the type is obvious from the right-hand side and the language supports inference, remove the annotation.
- **Unnecessary intermediate variables** — if a variable is used once on the next line, inline it (unless the name adds genuine clarity).

Only keep comments that explain _why_ — workarounds, constraints, non-obvious business rules. These are valuable. Remove everything else.

### 3. Simplify logic

- Collapse trivial if/else into a single expression where the language supports it (ternary, nil-coalescing, pattern matching).
- Replace boolean flags that track state across a loop with early exits or functional transforms (map, filter, first).
- Inline one-use helpers that are short enough to read in place. Don't extract helpers for one-time operations — three similar lines is better than a premature abstraction.

### 4. Improve naming

- Rename vague variables: `data`, `result`, `temp`, `info`, `val`, `obj` — these tell the reader nothing. Use names that say what the thing _is_.
- But keep names short for tightly-scoped temps (loop indices, short closures) and when a single word is enough. `i` is fine in a 3-line loop.
- Follow the language's naming conventions. camelCase in JS/Swift, snake_case in Python/Rust, etc.
- Method names should describe what they do without needing a comment. If you need a comment to explain what a method does, rename the method.

### 5. Move declarations close to usage

Variables defined at the top of a function but not used until line 40 force the reader to hold them in mental memory. Move declarations to just before first use. This makes extraction easier later.

### 6. Break up long functions

If a function is doing multiple distinct things sequentially, split it — each piece should do one thing and be readable on its own. Apply the same passes above to each extracted function. If extracting would require threading many parameters or the logic is deeply interleaved, don't force it — flag it as a readability concern instead.

## How to apply changes

1. Read the target files thoroughly.
2. Make all changes directly. Be efficient — batch related edits.
3. After editing, verify the code still compiles/parses if possible (run the project's lint or build command if one exists).
4. List changes briefly — the diff tells the full story.

## What NOT to do

- Don't add comments, docstrings, or type annotations that weren't there before (unless renaming made something ambiguous).
- Don't refactor architecture or move files between modules. This is a clarity pass, not a redesign.
- Don't change public API signatures unless the name is actively misleading.
- Don't be clever. The goal is code so boring and obvious that it is self-documenting and can be read cold.
