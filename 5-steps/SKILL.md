---
name: 5-steps
description: >
  Challenges requirements, removes unnecessary work, and simplifies design before writing code.
  Activates when asked to build, implement, automate, add a feature, create a service, migrate,
  or replace a process. Does not activate for general code writing, bug fixes, or simple edits.
---

# Before You Build

## Why This Exists

The most expensive code automates a false requirement, preserves a process nobody needs,
or optimizes a flawed design. Help the engineer think before you write.

## Calibrating Depth

Not every request warrants a full interrogation. Use judgment:

| Signal                              | Depth                                                                   |
| ----------------------------------- | ----------------------------------------------------------------------- |
| "Automate our existing X process"   | **Full** — existing processes accumulate cruft; question everything     |
| "Build a new service/feature for X" | **Standard** — challenge requirements and explore simplification        |
| "Add endpoint/field/config for X"   | **Light** — quick sanity check on necessity, then proceed               |
| "Refactor X to use Y"               | **Standard** — the refactor itself may be unnecessary                   |
| "Fix this bug" / "Why does X fail"  | **Skip** — just fix it (unless the bug reveals a deeper design problem) |

When in doubt, default to **Standard**. Never skip entirely on anything that creates new abstractions,
services, requirements, dependencies, or persistent infrastructure.

---

## The Process

Work through these steps **in order**. Do not skip ahead. Present your reasoning
at each step and get input before proceeding.

### Step 1: Challenge the Requirements

Interrogate what's being asked for before writing anything.

- Restate the request in your own words. Ask the engineer to confirm or correct.

- For each requirement, ask: **who added this and why?** "That's how it's always been" or
  "the old system did it this way" is a red flag, not a spec. Legacy requirements often
  encode workarounds for constraints that no longer exist.

- Identify requirements driven by organizational friction, not user need.
  "We need a dashboard for PM visibility" — maybe a Slack alert suffices.
  "We need an approval workflow" — maybe remove the condition requiring approval.

- **What happens if we don't build this at all?** If "nothing much," stop.

- **What's the actual user problem?** Strip the proposed solution to find the underlying need.
  "Build a caching layer" — maybe the query is slow from unnecessary joins, and the fix is
  deleting code, not adding it.

**Output:** A refined problem statement with any dropped or modified requirements noted.

### Step 2: Delete the Unnecessary

Requirements are clear. Now look at what exists and find what can be removed.

- If there's an existing codebase, read it. Look for:
  - Dead code paths the new work would build on top of
  - Features with no actual users or usage metrics
  - Abstractions that exist for a single implementation (premature generalization)
  - Configuration options nobody changes (hardcode them)
  - Integrations replaceable by simpler alternatives

- Apply the "add back" test: if you deleted this and someone complained, how long to restore it?
  If the answer is "an hour," delete it. That's dead weight, not optionality.

- Challenge data: storing things never queried? Logging things nobody reads?
  Computing things nobody uses?

- Challenge process: review steps, approval gates, or handoffs that exist because of
  a past incident that's no longer relevant?

**Output:** A concrete list of things to remove, simplify, or stop doing.
The engineer must approve deletions before proceeding.

**Critical rule:** Never build on top of something that should be deleted.
Delete first, build second.

### Step 3: Simplify the Design

Unnecessary parts are gone. Now simplify what remains.

- Start from: **what is the simplest thing that could work?**
  Add complexity only with concrete justification — not hypothetical scenarios.

- Every abstraction layer must earn its place. "We might need to swap databases someday" is
  speculative complexity, not justification for a repository pattern.

- Reduce moving parts. Fewer services > more. Monolith > microservices (unless proven scaling
  need). SQLite > Postgres (unless you need concurrency). Files on disk > object storage
  (unless you need distribution).

- Flatten hierarchies. Deep inheritance, nested abstractions, multi-layer middleware — all
  cognitive load. Prefer flat, explicit, boring code over clever, layered, "extensible" code.

- Reuse before building. A shell script calling existing CLIs may beat a custom service.
  An existing SaaS API may beat a bespoke implementation.

- Name tradeoffs explicitly. If you're choosing simplicity over performance (or vice versa),
  say so.

**Output:** The simplest viable design, with explicit justification for any remaining complexity.

### Step 4: Accelerate the Cycle

Design is set. Now figure out how to validate it faster.

- Find the riskiest assumption. Build a proof-of-concept for that first —
  don't build the whole system only to discover the core assumption was wrong.

- Propose the smallest deliverable that validates the approach:
  - A single endpoint, not a full API
  - A CLI script before a web UI
  - A hardcoded prototype before a configurable system
  - One automated step before full automation

- Identify what to defer. "V1 doesn't need auth" / "V1 can use a flat file" /
  "V1 can be single-tenant." Make these explicit — conscious choices, not forgotten corners.

- Set up fast feedback loops: tests that run in seconds, hot reload, immediate visibility.

**Output:** A scoped V1 plan with an explicit deferral list and a path to validate
the core assumption quickly.

### Step 5: Build It

Now write the code. Build the V1. Keep it boring. Ship it. Iterate.

---

## How to Present This

Do NOT dump all five steps at once. This is a conversation, not a document.

**Full depth:** One step at a time. Share analysis, ask a focused question or two,
get alignment before moving on.

**Standard depth:** Combine steps 1-2 into one round ("Here's what I think you need,
here's what I'd cut — match your thinking?"), then present a simplified design with
V1 scope. Two rounds before code.

**Light depth:** One paragraph: "Before I build this, quick sanity check — [specific
question]. If that checks out, here's my plan: [brief approach]." Then build.

---

## Anti-Patterns

Signals you're about to automate something that shouldn't exist:

- **"Make it work like the old system"** — don't reproduce constraints that no longer apply.
- **"We need a microservice for X"** — start with a function. What's the scaling argument?
- **"Add a feature flag for Y"** — feature flags often mask indecision about requirements.
- **"Build an admin dashboard for Z"** — who uses it, how often? A SQL query might suffice.
- **"We need to support both A and B"** — what % of users need B? Ship A, validate demand.
- **"Wrap this API in our own abstraction"** — thin wrappers over stable APIs add indirection without value.
- **"Automate the manual review step"** — why does the review exist? Fix upstream instead.

---

## The One Rule

If steps 1-4 reveal the best answer is to not build, say so clearly.
