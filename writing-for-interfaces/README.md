# Writing for Interfaces Skill

## Install

```bash
npx skills add andrewgleave/skills --skill writing-for-interfaces --global
```

## Example Prompt

```text
/writing-for-interfaces Rewrite these onboarding, empty state, and error messages for a budgeting app
```

## Skill Structure

This repository follows the **Agent Skills** open standard. Each skill is self-contained with its own logic, workflow, and reference materials.

```text
writing-for-interfaces/
├── SKILL.md              — Core instructions, principles, and voice/tone guidance
├── references/
│   └── patterns.md       — Detailed guidance for common interface patterns
└── README.md             — This file
```

## How it Works

When activated, the agent applies a structured interface-writing workflow:

1. **Read**: Review the relevant screens, flows, or copy the user wants to write or improve.
2. **Check voice**: Look for an existing product voice or help define one if none exists.
3. **Match patterns**: Identify the relevant UI patterns such as errors, alerts, onboarding, or empty states.
4. **Rewrite**: Provide concrete rewrites inline, prioritizing clarity and user progress over polish.
5. **Align**: Flag terminology drift and suggest consistent word choices across the interface.

## Sources

The principles in this skill are distilled from Apple's interface writing guidance and generalized for product interfaces more broadly:

- [**WWDC 2017** — Writing Great Alerts](https://developer.apple.com/videos/play/wwdc2017/813/)
- [**WWDC 2019** — Writing Great Accessibility Labels](https://developer.apple.com/videos/play/wwdc2019/254/)
- [**WWDC 2022** — Writing for Interfaces](https://developer.apple.com/videos/play/wwdc2022/10037/)
- [**WWDC 2024** — Adding Personality to Your App Through UX Writing](https://developer.apple.com/videos/play/wwdc2024/10140/)
- [**WWDC 2025** — Small Writing Changes, Big Impact](https://developer.apple.com/videos/play/wwdc2025/404/)
