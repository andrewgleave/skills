# Critical Reasoning Skill

## Install

```bash
npx skills add andrewgleave/skills --skill critical-reasoning --global
```

## Example Prompt

```text
/critical-reasoning I think we should rewrite this service in Rust because it's faster
```

## Skill Structure

This repository follows the **Agent Skills** open standard. Each skill is self-contained with its own logic, workflow, and reference materials.

```text
critical-reasoning/
├── SKILL.md           — Core instructions & workflow
├── references/        — Epistemological foundations
│   ├── popper.md      — Core Popperian concepts
│   ├── deutsch.md     — Deutsch's refinements
│   └── error-patterns.md — Common fallacies through a CR lens
└── README.md          — This file
```

## How it Works

When activated, the agent applies Popperian critical rationalism:

1. **Clarify**: Identify the exact claim or problem being examined.
2. **Steel-man**: Construct the strongest version of the argument before criticizing.
3. **Test**: Check falsifiability - what would refute this?
4. **Evaluate**: Assess explanation quality - is it hard to vary?
5. **Compare**: Consider alternatives and why this explanation should be preferred.
6. **Surface**: Identify errors that matter, connecting to epistemological principles.
