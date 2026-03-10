# Interface copy patterns

Detailed guidance for common interface writing situations. Read the relevant section when
working on a specific pattern.

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

---

## Alerts and dialogs

Alerts interrupt what someone is doing. That interruption has a cost, so every alert must
justify itself.

### When to use an alert

- To confirm a significant or irreversible action
- To request access to sensitive data (location, contacts, camera)
- To report an error that blocks progress
- To notify of a critical update that requires immediate attention

### When NOT to use an alert

- For non-essential information (use inline messaging or banners instead)
- For lengthy content or complex choices (use a dedicated screen)
- For problems you could have prevented (validate input inline instead)
- For technical diagnostics or error codes the person can't act on

### Structure

A good alert answers three questions: **What happened? Why? What now?**

- **Title**: State the main point in one short sentence. If someone reads only the title and
  the buttons, they should understand the situation.
- **Body** (optional): Brief additional context — the cause of the problem or reason for the
  request. Keep it to 1–2 sentences.
- **Actions**: Label buttons with specific verbs that describe what happens when tapped. Avoid
  "Yes" / "No" — use the actual action: "Delete Photo" / "Keep Photo."

### Checklist

- Could this information be communicated without an interruption?
- Can someone understand the alert from the title and buttons alone?
- Are the button labels specific actions, not generic confirmations?
- Is the body text actually adding information the title doesn't cover?

**Example — before:**

> Title: "App cannot open this file"
> Body: "You may need to download the latest updates. Do you want to visit our website for
> more information and troubleshooting tips?"
> Buttons: Yes / No

**Example — after:**

> Title: "Can't Open 'Report.pdf'"
> Body: "Update the app to open this file format."
> Buttons: Update App / Cancel

---

## Error messages

Errors are moments of friction. The person tried to do something and it didn't work. Your job
is to get them unstuck as fast as possible.

### Principles

1. **Say what happened** in plain language. Not error codes, not "something went wrong."
2. **Explain why** if it helps them understand (but skip if the cause is obvious or
   irrelevant).
3. **Tell them what to do next.** Every error message should have a clear path forward — a
   button, a suggestion, a next step.

### What to avoid

- Technical jargon and error codes (the person can't act on "Error 500")
- Blaming the person ("invalid input", "bad request")
- Interjections like "Oops!" or "Uh oh!" — they trivialize the problem
- Vague non-information: "Something went wrong. Please try again."
- The word "please" as a reflex — it sounds insincere in automated text

**Example — before:**

> "Oops! You can't do that. Error code 1234567. Sorry, bad input. Please try again."
> Buttons: Okay / Cancel

**Example — after:**

> Title: "Billing Problem"
> Body: "To continue your subscription, add a new payment method."
> Buttons: Add Payment Method / Not Now

---

## Destructive actions

When an action can't be undone — deleting data, canceling a subscription, removing an
account — the stakes are higher and the writing must be proportionally careful.

### Principles

- Name the specific thing being destroyed: "Delete 'Vacation Photos' album?" not "Delete
  this item?"
- Make the consequences explicit: "You'll lose all 847 photos in this album."
- Label buttons with the actual action. "Delete Album" / "Keep Album" — not "Confirm" /
  "Cancel."
- Avoid double-negative confusion. "Cancel Cancellation" is a dark pattern. If the action is
  "cancel a subscription," write: "Cancel Subscription?" with buttons "Cancel Subscription" /
  "Keep Subscription."

---

## Empty states

An empty state is a screen with no content yet. It's an opportunity to teach, guide, or
occasionally delight — but always with purpose.

### Principles

- Tell the person what will appear here and how to make it happen: "No Saved Episodes. Save
  episodes you want to listen to later, and they'll show up here."
- Match the tone to the context. A completed to-do list can be celebratory. An empty search
  result should be helpful, not whimsical.
- Avoid idioms or humor that might not translate ("Nothing strike your fancy?").
- If possible, include a clear action: a button to create, add, or search.

---

## Onboarding and setup flows

First impressions matter. Onboarding is your chance to welcome someone, explain your
product's value, and help them get started.

### Principles

- Define the purpose of the whole flow and each screen within it. This prevents redundant
  steps and keeps things focused.
- Tell people why: "Reducing screen time before bed helps you sleep better" gives a reason to
  engage with the feature.
- Be honest about what you need and why: if you're asking for permissions, explain how the
  data will be used.
- Welcome people in with warmth, but don't waste their time. A single sentence that captures
  the product's value is better than three paragraphs.
- Use consistent button labels throughout the flow (if "Next" moves you forward on one
  screen, use "Next" on all of them).

---

## Notifications

Notifications reach people when they're doing something else. They compete for attention
against whatever matters to the person right now.

### Principles

- Lead with the why — the benefit or the key information — not the instruction.
  "Your package arrives in 10 minutes" is better than "Open the app to check delivery
  status."
- Be specific: "8 minutes to Home — take Audubon Ave, traffic is light" gives real value.
  "Check your commute!" does not.
- Respect attention. If the information isn't time-sensitive or actionable, it probably
  shouldn't be a notification.
- Keep it to one idea. If you need to say more, the notification should take them to a screen
  that does.

---

## Accessibility labels

For people using screen readers, accessibility labels are the interface. Every interactive
element — buttons, controls, links — and every meaningful visual — icons, images, charts —
needs a thoughtful text label.

### Principles

- **Always add labels.** An unlabeled button reads as "button" or a raw filename. Neither is
  usable.
- **Be succinct.** "Add" is usually better than "Add item to the current list." But add
  context when needed to disambiguate: "Add peanut butter to cart" when there are multiple
  "Add" buttons.
- **Don't include the element type.** Screen readers already announce "button," "link," etc.
  Writing "Add button" produces "Add button button."
- **Describe intent, not just appearance.** An image label should convey meaning: "Person
  meditating with relaxed arms" not "circular image, blue background."
- **Update labels when state changes.** If a toggle switches from "Play" to "Pause," the
  label must update too.
- **Label animations and loading states.** A spinner should announce "Loading" so people know
  something is happening.
- **Skip redundant context.** In a music player, "Play" is enough — you don't need "Play
  song" because the context is already clear.
- **Match the label's richness to the content.** Most labels should be succinct. But when the
  content itself is expressive — stickers, emoji, illustrations, artwork — a richer description
  serves the person better. A sticker of Cookie Monster might be labelled "Me happy face eat
  small cookie, om nom nom" because that captures the spirit of what a sighted person sees.
  The goal is an equivalent experience, not just a minimal one.
- **Web interfaces:** These same principles apply to `aria-label`, `aria-describedby`, and
  `alt` attributes. The guidance above is platform-agnostic — apply it to whatever labeling
  mechanism the platform provides.

---

## Buttons and actions

Buttons are the most-read text in any interface. People scan headers and buttons to understand
a screen — they may never read the body text.

### Principles

- Use specific verbs: "Save Changes," "Send Message," "Download Report" — not "OK," "Submit,"
  "Done" (unless "Done" genuinely means "I'm finished with this whole task").
- Match the button label to the action described in the surrounding text. If the body says
  "pair your device," the button should say "Start Pairing," not "Continue."
- For paired choices, make both options clear on their own: "Keep Subscription" /
  "Cancel Subscription" — not "Confirm" / "Cancel."
- Destructive actions should be visually distinct (e.g. red) and labeled with what they
  destroy: "Delete Album," not "Delete."

---

## Instructional and inline copy

Short instructional text that appears within a screen — field hints, tooltips, inline
guidance, step descriptions.

### Principles

- Lead with the benefit: "To keep your streak, solve today's crossword" not "Solve today's
  crossword to keep your streak."
- Be direct. "Enter your license plate number to pay for parking" — no "simply," no
  "quickly."
- Place instructions where the person is looking. If they're focused on a camera viewfinder,
  overlay the instruction near their focal point.
- One instruction at a time. Don't stack multiple steps into a single line.
