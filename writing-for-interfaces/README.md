# Writing for Interfaces

A Claude Code skill for writing clear, purposeful interface copy for buttons, labels, errors, alerts, notifications, onboarding flows, empty states, tooltips, accessibility text, and any other text a person encounters when using a digital product.

Based on Apple's Human Interface Guidelines and principles for writing in interfaces and distilled from WWDC sessions on how to write for interfaces.

## What it does

The skill provides structured guidance for writing and reviewing user-facing copy across any digital interface such as apps, web, CLI, conversational AI, or email. It covers:

- **Core principles**: purpose, anticipation, context, and empathy
- **Voice and tone**: establishing a product voice and adapting tone to context
- **Writing craft**: removing filler, avoiding repetition, being specific, maintaining consistency
- **Pattern-specific guidance**: alerts, errors, destructive actions, empty states, onboarding, notifications, accessibility labels, buttons, and instructional copy

The skill also helps users define their product's voice if one hasn't been established, then uses it as a lens for all subsequent copy.

## Installation

Copy the `writing-for-interfaces` directory to your Claude Code skills folder:

```
cp -r writing-for-interfaces ~/.claude/skills/
```

## Structure

```
writing-for-interfaces/
├── SKILL.md              # Core principles, writing craft, voice & tone
└── references/
    └── patterns.md       # Detailed guidance for 9 common interface patterns
```

## Sources

The principles in this skill have been distilled from Apple's WWDC sessions on writing for interfaces and generalised to apply to any interface:

- [**WWDC 2017** — Writing Great Alerts](https://developer.apple.com/videos/play/wwdc2017/813/)
- [**WWDC 2019** — Writing Great Accessibility Labels](https://developer.apple.com/videos/play/wwdc2019/254/)
- [**WWDC 2022** — Writing for Interfaces](https://developer.apple.com/videos/play/wwdc2022/10037/)
- [**WWDC 2024** — Adding Personality to Your App Through UX Writing](https://developer.apple.com/videos/play/wwdc2024/10140/)
- [**WWDC 2025** — Small Writing Changes, Big Impact](https://developer.apple.com/videos/play/wwdc2025/404/)
