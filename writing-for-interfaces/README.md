# Writing for Interfaces Skill

## Install

```bash
npx skills add andrewgleave/skills --skill writing-for-interfaces --global
```

## Example Prompt

```text
/writing-for-interfaces Review and evaluate all UI copy for clarity, purpose, and consistency.
```

## Skill Structure

This repository follows the **Agent Skills** open standard. Each skill is self-contained with its own logic, workflow, and reference materials.

```text
writing-for-interfaces/
├── SKILL.md              — Core instructions, principles, and voice/tone guidance
├── references/
│   └── patterns.md       — Detailed guidance for common interface patterns
└── README.md
```

## How it Works

When activated, the agent applies a voice-first workflow:

1. **Establish voice**: Search for an existing voice definition in project files (`CLAUDE.md / AGENTS.md`, style guides, design docs). If none exists or the existing copy is inconsistent, walk the user through defining one — what the product does, who it's for, where it's used, and what personality traits define it. An established and consistent voice is the foundation for all copy decisions.
2. **Evaluate the request**: Determine whether the task is new copy, a review, a rewrite, or terminology work and identify which interface patterns apply.
3. **Apply voice and principles**: Check that copy sounds like the defined voice. Dial tone qualities up or down for the situation and then apply the core principles.
4. **Evaluate**: Consult the patterns reference for situation-specific guidance on structure, tone, and common pitfalls.
5. **Apply changes**: Rewrite existing copy inline or draft from scratch. Show original → rewrite with a brief rationale tied to voice and principles. Prioritise changes that confuse or block users before polish.
6. **Update terminology reference**: Flag terminology drift and suggest word list entries to keep voice and phrasing consistent across the interface. The user should be able to review the changes and approve or reject them.

## Sources

Many principles are distilled from Apple's interface writing guidance and generalised for product interfaces more broadly:

- [**Human Interface Guidelines** — Writing](https://developer.apple.com/design/human-interface-guidelines/writing/)
- [**Human Interface Guidelines** — Alerts](https://developer.apple.com/design/human-interface-guidelines/alerts/)
- [**Human Interface Guidelines** — Accessibility](https://developer.apple.com/design/human-interface-guidelines/accessibility/)
- [**WWDC 2019** — Writing Great Accessibility Labels](https://developer.apple.com/videos/play/wwdc2019/254/)
- [**WWDC 2022** — Writing for Interfaces](https://developer.apple.com/videos/play/wwdc2022/10037/)
- [**WWDC 2024** — Adding Personality to Your App Through UX Writing](https://developer.apple.com/videos/play/wwdc2024/10140/)
- [**WWDC 2025** — Make a Big Impact with Small Writing Changes](https://developer.apple.com/videos/play/wwdc2025/404/)
- [**Apple Style Guide**](https://help.apple.com/applestyleguide/)
