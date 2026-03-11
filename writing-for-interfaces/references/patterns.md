# Interface copy patterns

Detailed guidance for common interface writing situations. Each pattern should be applied
through the lens of your product's voice and tone — the voice stays consistent, the tone
adapts to the situation.

## Table of contents

1. [Alerts and dialogs](#alerts-and-dialogs)
2. [Error messages](#error-messages)
3. [Destructive actions](#destructive-actions)
4. [Empty states](#empty-states)
5. [Onboarding and setup flows](#onboarding-and-setup-flows)
6. [Notifications](#notifications)
7. [Accessibility labels](#accessibility-labels)
8. [Buttons and actions](#buttons-and-actions)
9. [Instructional and inline copy](#instructional-and-inline-copy)
10. [Settings and preferences](#settings-and-preferences)

---

## Alerts and dialogs

Alerts interrupt what someone is doing. That interruption has a cost — every alert must
justify itself by delivering information the person genuinely needs right now.

### When to use an alert

- To confirm a significant or irreversible action.
- To request access to sensitive data (location, contacts, camera).
- To report an error that blocks progress.
- To notify of a critical update that requires immediate attention.

### When NOT to use an alert

- For non-essential information (use inline messaging or banners instead).
- For lengthy content or complex choices (use a dedicated screen).
- For problems you could have prevented (validate input inline instead).
- For technical diagnostics or error codes the person can't act on.
- For common, undoable actions — even destructive ones. People who delete an email intend
  to discard it and can undo the action; they don't need an alert every time.
- At app launch. If something's wrong at startup (like no network), show cached or
  placeholder data with a nonintrusive label describing the problem.

### Structure

A good alert answers three questions: **What happened? Why? What now?**

- **Title**: State the main point in one short sentence. If someone reads only the title
  and the buttons, they should understand the situation. Use sentence-style capitalisation
  for complete sentences (with appropriate punctuation) or title-style capitalisation for
  fragments (no ending punctuation).
- **Body** (optional): Brief additional context — the cause of the problem or reason for
  the request. Keep it to 1–2 sentences. Only include body text if it adds information the
  title doesn't already cover. Don't use the body to explain what the buttons do — if the
  title and buttons are clear, the body isn't needed.
- **Actions**: Label buttons with specific verbs that describe what happens when tapped.
  Avoid "Yes" / "No" — use the actual action. If you only read the button labels, you
  should still understand what you're choosing.

### Tone guidance

Alerts are interruptions in moments that range from routine to critical. Dial up clarity
and directness. Dial back personality — this isn't the place for the voice to shine, it's
the place for the voice to stay calm and get out of the way.

### Checklist

- Could this information be communicated without an interruption?
- Can someone understand the alert from the title and buttons alone?
- Are the button labels specific actions, not generic confirmations?
- Is the body text actually adding information the title doesn't cover?
- If the alert appears contextually (e.g. on opening an app), does it explain why?

**Example — before:**

> Title: "App cannot open this file"
> Body: "You may need to download the latest update.
> Buttons: Yes / No

**Example — after:**

> Title: "Can't Open 'Report.pdf'"
> Body: "Update the app to open this file format."
> Buttons: Update / Cancel

---

## Error messages

Errors are moments of friction. The person tried to do something and it didn't work. Your
job is to get them unstuck as fast as possible.

### Principles

1. **Say what happened** in plain language. Not error codes, not "something went wrong."
   Name the specific thing: "Can't connect to Wi-Fi" not "Network error."
2. **Explain why** if it helps them understand — but skip if the cause is obvious or
   irrelevant.
3. **Tell them what to do next.** Every error message should have a clear path forward — a
   button, a suggestion, a next step. Display errors as close to the problem as possible.

### What to avoid

- Technical jargon and error codes the person can't act on.
- Blaming the person ("invalid input", "bad request"). Instruct instead of scold: "Use
  only letters for your name" not "Don't use numbers or symbols."
- Interjections like "Oops!" or "Uh oh!" — they trivialise the problem.
- Vague non-information: "Something went wrong. Please try again."
- "Please" as a reflex — it sounds insincere in automated text. Use it only when it
  genuinely adds warmth.
- "Sorry" as padding — it takes away from the primary message.
- Robotic messages with no helpful information, like "Invalid name."

### Tone guidance

Errors can be frustrating. Dial up clarity and helpfulness. Dial back friendliness — calm,
direct language respects the person's situation more than forced warmth. If language alone
can't address an error that's likely to affect many people, use that as a signal to rethink
the interaction.

**Example — before:**

> "Oops! You can't do that. Error code 1234567. Please try again."
> Buttons: Okay / Cancel

**Example — after:**

> Title: "Billing Problem"
> Body: "To continue your subscription, add a new payment method."
> Buttons: Add Payment Method / Not Now

---

## Destructive actions

When an action can't be undone — deleting data, cancelling a subscription, removing an
account — the stakes are higher and the writing must be proportionally careful.

### Principles

- **Name the specific thing being destroyed**: "Delete 'Vacation Photos' album?" not
  "Delete this item?"
- **Make the consequences explicit**: "You'll lose all 847 photos in this album."
- **Label buttons with the actual action**: "Delete Album" / "Keep Album" — not "Confirm"
  / "Cancel."
- **Avoid double-negative confusion.** "Cancel Cancellation" is a dark pattern. If the
  action is "cancel a subscription," write: "Cancel Platinum Subscription?" with buttons
  "Cancel Subscription" / "Keep Subscription."
- **Use the destructive style** (e.g. red button) for actions the person didn't
  deliberately initiate. When someone deliberately chose a destructive action (like Empty
  Trash), the confirmation button doesn't need the destructive style — the convenience of
  confirming their original intent outweighs reaffirming the danger.
- **Always include a Cancel button** for destructive actions to give people a clear, safe
  way out. Use the title "Cancel" — it's universally understood.

### Tone guidance

Dial up directness and specificity. Keep the voice calm and neutral. This is not a moment
for personality — it's a moment for directness and clarity.

---

## Empty states

An empty state is a screen with no content yet. It's an opportunity to teach, guide, or
occasionally delight — but always with purpose.

### Principles

- **Tell the person what will appear here and how to make it happen**: "No Saved Episodes.
  Save episodes you want to listen to later, and they'll show up here."
- **Match the tone to the context.** A completed to-do list can be celebratory. An empty
  search result should be helpful, not whimsical.
- **Avoid idioms or humour that might not translate.** "Nothing strike your fancy?" is
  culturally specific and gives no useful guidance.
- **If possible, include a clear action**: a button to create, add, or search.
- **Remember that empty states are usually temporary** — don't show crucial information
  that could then disappear.

### Tone guidance

Empty states are one of the best places for personality to shine through — especially
welcome screens and completed states. But make sure the content is useful and fits the
context. Education first, delight second.

---

## Onboarding and setup flows

First impressions matter. Onboarding is your chance to welcome someone, explain your
product's value, and help them get started — without wasting their time.

### Principles

- **Define the purpose of the whole flow and each screen within it.** This prevents
  redundant steps and keeps things focused.
- **Lead with the why.** "Reducing screen time before bed helps you sleep better" gives a
  reason to engage with the feature. Tell people why you need what you're asking for.
- **Be honest about what you need and why**: if asking for permissions, explain how the
  data will be used. Make values like privacy visible throughout.
- **Welcome people with warmth, but don't waste their time.** A single sentence that
  captures the product's value is better than three paragraphs.
- **Use consistent button labels throughout the flow.** If "Next" moves you forward on one
  screen, use "Next" on all of them. Start with language like "Get Started" to signal the
  beginning and "Done" to signal the end.
- **Each screen should say one thing.** If you're trying to convey more than one idea,
  break it onto multiple screens and think about the flow of information across them.

### Tone guidance

Onboarding is a warm moment. Dial up friendliness and helpfulness. The voice can shine here
more than almost anywhere else. But never sacrifice clarity for personality — people need to
understand what they're setting up.

---

## Notifications

Notifications reach people when they're doing something else. They compete for attention
against whatever matters to the person right now.

### Principles

- **Lead with the why** — the benefit or the key information — not the instruction. "Your
  package arrives in 10 minutes" is better than "Open the app to check delivery status."
- **Be specific**: "8 minutes to Home — take Audubon Ave, traffic is light" gives real
  value. "Check your commute!" does not.
- **Respect attention.** If the information isn't time-sensitive or actionable, it probably
  shouldn't be a notification.
- **Keep it to one idea.** If you need to say more, the notification should take them to a
  screen that does.
- **Choose the right delivery method.** Consider urgency, importance, and how much
  supporting information is needed. An alert for critical interruptions, a banner for
  informational updates, inline messaging for contextual information.

### Tone guidance

Notifications should feel like a helpful tap on the shoulder, not a demand for attention.
Keep the voice present but restrained. Match the tone to urgency: a delayed delivery is
matter-of-fact; a milestone can be warmer.

---

## Accessibility labels

For people using screen readers, accessibility labels are the interface. Every interactive
element — buttons, controls, links — and every meaningful visual — icons, images, charts —
needs a thoughtful text label.

### Principles

- **Always add labels.** An unlabeled button reads as "button". Neither
  is usable. A person gives an app about 30 seconds — if they can't access the
  functionality, they delete it.
- **Be succinct.** "Add" is usually better than "Add item to the current list." But add
  context when needed to disambiguate: "Add to cart" when there are multiple
  "Add" buttons on screen.
- **Don't include the element type.** Screen readers already announce "button," "link," etc.
  Writing "Add button" produces "Add button, button."
- **Describe intent, not just appearance.** An image label should convey meaning: "Person
  meditating with relaxed arms and forefingers touching" — both the physical details and
  the context. Not "circular image, blue background."
- **Update labels when state changes.** If a toggle switches from "Play" to "Pause," the
  label must update too.
- **Label animations and loading states.** A spinner should announce "Loading" so people
  know something is happening.
- **Skip redundant context.** In a music player, "Play" is enough — you don't need "Play
  song" because the context is already clear.
- **Match the label's richness to the content.** Most labels should be succinct. But when
  the content itself is expressive — stickers, emoji, illustrations — a richer description
  serves the person better. A sticker of Cookie Monster might be labelled "Me happy face
  eat small cookie, om nom nom" because that captures the spirit of what a sighted person
  sees. The goal is an equivalent experience, not just a minimal one.
- **Use inclusive language.** Describe people as "person" rather than assuming gender unless
  it's explicitly specified.
- **Web interfaces:** These principles apply to `aria-label`, `aria-describedby`, and `alt`
  attributes. The guidance is platform-agnostic.

---

## Buttons and actions

Buttons are the most-read text in any interface. People scan headers and buttons to
understand a screen — they may never read the body text.

### Principles

- **Use specific verbs**: "Save Changes," "Send Message," "Download Report" — not "OK,"
  "Submit," "Done" (unless "Done" genuinely means "I'm finished with this whole task").
- **Match the button label to the surrounding text.** If the body says "pair your device,"
  the button should say "Start Pairing," not "Continue."
- **For paired choices, make both options clear on their own**: "Keep Subscription" /
  "Cancel Subscription" — not "Confirm" / "Cancel."
- **Destructive actions should be visually distinct** (e.g. red) and labelled with what
  they destroy: "Delete Album," not "Delete."
- **Avoid "OK" as a default unless the alert is purely informational.** The meaning of "OK"
  can be ambiguous — does it mean "OK, do it" or "OK, I understand"? A specific verb is
  almost always better.
- **Prefer verbs over "Yes" / "No."** If you only read the button labels, you should still
  understand the choice. "Cancel Subscription" / "Keep Subscription" is clear without any
  surrounding text.
- **Be consistent.** If "Next" advances through a flow, use "Next" everywhere. Add button
  labels to your word list.

---

## Instructional and inline copy

Short instructional text that appears within a screen — field hints, tooltips, inline
guidance, step descriptions, settings labels.

### Principles

- **Lead with the benefit**: "To keep your streak, solve today's crossword" not "Solve
  today's crossword to keep your streak."
- **Be direct.** "Enter your license plate number to pay for parking" — no "simply," no
  "quickly."
- **Place instructions where the person is looking.** If they're focused on a camera
  viewfinder, overlay the instruction near their focal point.
- **One instruction at a time.** Don't stack multiple steps into a single line.
- **For text fields**, label all fields clearly and use hint or placeholder text so people
  know how to format information. Give an example in hint text ("name@example.com") or
  describe the information ("Your name"). Show errors right next to the field.

---

## Settings and preferences

Settings are utilitarian — people visit them to find something specific and get out.

### Principles

- **Keep labels clear and practical.** Help people easily find what they need by naming
  settings as plainly as possible.
- **If the label isn't enough, add a short description.** Describe what the setting does
  when turned on — people can infer the opposite. "Apple Watch can detect when you're
  washing your hands and start a 20-second timer" is complete; you don't need to explain
  what happens when it's off.
- **Provide direct links or buttons** to navigate to a setting rather than trying to
  describe its location in prose.
