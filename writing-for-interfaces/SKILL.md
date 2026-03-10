---
name: writing-for-interfaces
description: >
  Use when someone asks to write, rewrite, review, or improve text that appears inside a
  product or interface. Examples: "review the UX", "is there a better way to phrase this",
  "rewrite this error message", "write copy for this screen/flow/page", reviewing button
  labels, improving CLI output messages, writing onboarding copy, settings descriptions, or
  confirmation dialogs. Trigger whenever the request involves wording shown to end users
  inside software — apps, web, CLI, email notifications, modals, tooltips, empty states, or
  alerts. Also trigger for vague requests like "review the UX" where interface copy review is
  implied. Do NOT trigger for content marketing, blog posts, app store listings, API docs,
  brand guides, cover letters, or interview questions - this is a technical writing skill.
---

# Writing for Interfaces

## When triggered

1. Read the relevant files or copy the user is asking about.
2. Check if the project has a defined voice (CLAUDE.md, style guide, design docs). If none
   exists, offer to help establish one before writing.
3. Identify which patterns apply (alerts, errors, empty states, etc.) and consult
   `references/patterns.md` for the relevant sections.
4. Provide specific rewrites inline — show the original, then the rewrite, with a brief
   rationale tied to the principles below. Prioritize changes that confuse or block users
   before polish.
5. When reviewing copy across multiple screens or files, flag terminology inconsistencies and
   suggest word list entries.

---

Good interface writing is invisible. When words work seamlessly with design, people don't
notice them — they just do what they came to do. When the words fail, people get stuck,
confused, or frustrated. Every piece of text in an interface is a small act of communication:
it should respect the person's time, meet them where they are, and help them move forward.

These principles apply universally — mobile apps, web apps, CLI tools, conversational agents,
notifications, emails, or any surface where a product speaks to a human.

Writing should be part of the design process from the start, not something filled in at the
end. When words are considered alongside layout, interaction, and visual design, the result
feels seamless. When they're an afterthought, you get placeholder text that never gets
replaced, screens that fight their own copy, and experiences that feel stitched together.

## Core principles

### 1. Have a purpose for every word

Every screen, every message, every label exists to help someone do something or understand
something. Before writing, answer: **what is the single most important thing the person needs
to know right now?** That's your purpose. Everything on the screen should serve it.

- Use information hierarchy to signal what matters most. Headlines and buttons carry the
  primary message; supporting text fills in detail.
- Know what to leave out. If a piece of information doesn't serve the purpose of this moment,
  move it elsewhere or cut it.
- If you're struggling to find the right words, go back to the purpose of the screen.

### 2. Anticipate what comes next

Think of the interface as a conversation. In any good conversation there's a natural back and
forth — you listen, respond, and anticipate what the other person needs to hear next.

- After telling someone about a problem, tell them how to fix it.
- After asking someone to do something, make it obvious how to do it.
- After someone completes something, acknowledge it and point forward.
- Lead with the "why" — put the benefit or reason before the instruction.
  `To get reservation updates, enter your phone number` is stronger than
  `Enter your phone number to get reservation updates`.

### 3. Respect the context

People use products in wildly different circumstances — on a busy train, mid-conversation,
one-handed, in a crisis, at 2am. The context shapes everything about how you write.

- Consider the physical and emotional situation. Someone getting a health alert needs calm
  clarity; someone hitting a milestone can handle some warmth.
- Match the density of information to the person's available attention. Mid-task text should
  be ultra-brief. Setup flows can afford a bit more.
- Timing matters. Show information when it's relevant, not before.

### 4. Write with empathy

You're writing for everyone who might use this product — different abilities, languages,
cultures, levels of technical fluency, and emotional states.

- Use plain, direct language. Avoid jargon, idioms, and culturally specific references that
  may not translate.
- Design for accessibility from the start. Labels, descriptions, and alt text aren't
  afterthoughts — for some people, they're the entire experience.
- Avoid unnecessary references to gender, age, or ability. Use inclusive, neutral language.
- Consider localization: text expands and contracts across languages, some languages read
  right-to-left, abbreviations work differently.

## Writing craft

### Remove filler words

Interface text has no minimum word count. Every word must earn its place.

- **Adverbs and adjectives**: "Simply enter your license plate" → "Enter your license plate."
  Words like "simply," "quickly," "easily," "just" make promises about the person's experience
  that you can't guarantee — and they add nothing to clarity. However, a descriptive word that
  genuinely clarifies behaviour earns its place: "Feed your pets automatically" tells you
  something "Feed your pets" doesn't. The test is whether the word adds meaning, not whether
  it's a modifier.
- **Interjections**: "Uh oh!", "Oops!", "Oh no!" in error messages can sound like you're not
  taking the problem seriously. Cut them.
- **Pleasantries**: "Sorry" and "please" can sound insincere in automated messages. Use them
  only when they genuinely add warmth, not as reflex padding.
- **Unnecessary punctuation**: Exclamation marks should be rare. If everything is exciting,
  nothing is.

The test: read the sentence without the word. If the meaning is unchanged, remove it.

### Avoid repetition

Saying the same thing twice in different words is filler. Combine overlapping ideas into one
clear statement.

`"We're running late. Your delivery driver won't make it on time. They'll be there in 10
minutes."` → `"Delivery delayed 10 minutes. Check the app for your driver's location."`

### Be specific, not vague

- Name the thing: "Can't open 'Quarterly Report.pdf'" not "Can't open this file."
- Name the action: "Cancel Subscription" / "Keep Subscription" not "Yes" / "No."
- Give real information: "Your card ending in 4242 was declined" not "There was a payment
  error."

### Keep a word list

Decide what you call things and stick to it. If you call it an "alias" on one screen, don't
call it a "username" on another. A simple two-column table (use / don't use) with brief
definitions prevents drift and helps anyone working on the product write consistently.

Button labels are especially good word list entries — if "Next" advances through a flow, use
"Next" everywhere, not "Continue" on one screen and "Proceed" on another.

When reviewing copy across multiple screens, check for terminology drift. Flag inconsistencies
and suggest word list entries the team can adopt.

### Sweat the details

Correct spelling, grammar, and punctuation go a long way toward making a product feel polished
and trustworthy. Inconsistent capitalisation, stray punctuation, or typos erode confidence —
especially in moments where trust matters (payments, permissions, health data).

Write for the space available. Buttons, notification titles, tooltips, and labels all have
limited screen real estate. If copy needs to be short, make it short — don't compress a long
sentence, write a short one.

## Patterns

For detailed guidance on specific interface patterns — alerts, error messages, empty states,
onboarding flows, notifications, accessibility labels, and destructive actions — see
`references/patterns.md`.

## Voice and tone

Before writing any copy, check whether the product has a defined voice. If not, help the user
establish one — it's the foundation that makes all other copy decisions easier and keeps the
experience consistent as it grows.

### Establishing voice

If the user hasn't defined their product's voice yet, walk them through it:

1. **Ask what the product does and who it's for.** A banking app for professionals and a
   savings app for kids serve similar purposes but should sound completely different.
2. **Ask them to imagine the product as a person.** What personality traits would it have?
   Encourage them to brainstorm freely — smart, playful, calm, authoritative, warm, no-nonsense
   — then group similar words into 3–4 key qualities.
3. **Help them refine.** Look for natural tensions between the qualities (e.g. "friendly" and
   "concise" push against each other in useful ways — that tension helps modulate tone). Discard
   qualities that are always-on table stakes (like "not confusing") and keep the ones that
   genuinely differentiate the product's personality.
4. **Capture it.** Suggest the user write down their voice qualities somewhere durable — a
   CLAUDE.md, a design doc, a style guide — so it persists across sessions and contributors.
   A word list (see "Keep a word list" above) pairs well with this.

Once a voice is defined, use it as a lens for all copy work. When writing new copy, check that
it sounds like those qualities. When reviewing existing copy, flag anything that drifts from
the established voice.

### Voice vs. tone

**Voice** is the consistent personality of your product — what it always sounds like. The
3–4 qualities you defined above. These don't change.

**Tone** is how the voice adapts to the situation. Think of each voice quality as a dial you
can turn up or down depending on the moment:

- Celebrating a milestone? Turn up warmth, dial back brevity.
- Reporting an error? Turn up clarity and helpfulness, dial back friendliness.
- Onboarding a new user? Balance helpfulness with warmth.

No quality should ever be turned all the way off. You never want to be unclear, or unhelpful,
or cold — it's about emphasis.

### Applying voice and tone to copy

When writing or reviewing copy, consider:

- Does this sound like our 3–4 voice qualities? If you read it aloud, would you recognize it
  as coming from this product?
- Which qualities need to be dialed up or down for this particular situation?
- Is the voice getting in the way of usefulness? Never sacrifice clarity for personality.
  Look for moments where personality can shine through naturally — celebrations, welcome
  screens, empty states — rather than forcing it into error messages or critical flows.

## The simplest test

Read your writing out loud. If it sounds like how you'd explain something to a friend —
clear, natural, no filler — it's probably good. If it sounds like a robot, a legal document,
or a school essay padded to hit a word count, keep editing.
