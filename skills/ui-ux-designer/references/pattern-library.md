# Pattern library — proven solutions to reach for

Load when choosing how a screen behaves, not just how it looks. A UI/UX pattern is a **reusable solution to a recurring user problem** — not a feature to paste in, and not a finished design. Prescribe the pattern that fits; adapt it to the subject; never apply one out of context (a misused pattern does more harm than good). Jakob's Law and MAYA still rule: stay conventional on placement, innovate only where it earns its keep.

Contents: how to evaluate a pattern · the four UI layers · pattern categories · the interaction patterns to reach for (input, navigation, content & data, onboarding & feedback, social).

---

## 1. How to evaluate a pattern before prescribing it

State each pattern the way a designer hands it to an engineer:

- **Problem** — the user problem, phrased as a one-sentence user story.
- **Solution** — how it's solved (navigation and shortcuts, getting input, handling data, displaying content and defaults).
- **Example** — a concrete instance, so the intent is unambiguous.
- **Usage** — when to use it and, crucially, when **not** to (product architecture, layout, device, existing patterns, user type, primary use cases).

## 2. The four UI layers (build up, don't skip)

`Controls` → `Patterns` → `Principles` → `Templates`. Individual **controls** (button, field, dropdown) combine into **patterns** (search, wizard, feed), governed by **principles** (the visual and interaction laws in `visual-system.md`), assembled into **templates** (the page/screen archetypes). This is the same buildup as tokens → components → recipes; keep the layers consistent.

## 3. Pattern categories

Every pattern serves one job — name it: **data & input** (feedback/response to data, e.g. drag-and-drop), **content structure** (page structure that streamlines flow and aids accessibility), **navigation** (sidebars, tab bars, menus), **incentivization** (positive feedback that keeps people using the product), **hierarchy** (visually establishing primary elements), **social** (sharing to networks).

## 4. Input & data-entry patterns

- **Contextual keyboard** — show the keyboard that matches the field (numeric for phone/amount, URL keyboard for links). Signals the expected input and speeds entry.
- **Smart defaults & autocomplete** — pre-populate likely values (current location, country code, recent items); pair with autocomplete. Only when the system can make a qualified guess (see defaults discipline below).
- **Immediate immersion ("lazy signup")** — let people use the app before registering; ask for the account once there's a payoff (sync, saved work). Shows rather than tells. Not for apps that need identity to function.
- **Social login** — OAuth sign-in (Apple/Google/etc.) to remove one more password and seed profile data. Offer alongside, not instead of, email where trust requires it.
- **Expandable inputs & action bars** — keep the primary actions (search, share, create) in a persistent bar; expand secondary inputs on demand to cut clutter.
- **Swipe-for-action** — swipe a row/card to reveal or trigger an action (archive, like, schedule). Distinct from swipe *views* (browsing).
- **Undo over confirm** — prefer an undo affordance to a blocking confirmation dialog for reversible actions; reserve confirmation for the irreversible.

### Defaults discipline

Users rarely change defaults, so the default *is* the design. Set a default only when the back-end can make a qualified guess or the default clearly benefits the user; make it easy to change; and **never** default anything that requires the user's own decision — newsletter opt-in, terms acceptance, sharing scope. A default that quietly acts for the user erodes trust.

## 5. Navigation patterns

Pick one model per level and keep it; never mix nav patterns at one level, and keep back predictable and screens deep-linkable.

- **Tab bar** (bottom, ≤5 items) for top-level sections on mobile; **top app bar** on Android.
- **Drawer / slideout / sidebar** for secondary or many destinations that don't warrant a permanent tab.
- **Overflow menu** for low-frequency actions that would otherwise clutter the bar.
- **Content-based & vertical navigation** for linear or story-driven content (pairs with scroll-triggered reveals).
- **Sticky / fixed navigation** to keep wayfinding present on long pages (respect safe areas).
- **Swipe views** for browsing peer content (tabs you can swipe between); let the next item peek to signal it (Gestalt continuity).
- **Breadcrumbs** for deep hierarchies on web.

## 6. Content & data-display patterns

- **Cards** — self-contained units of mixed content that reflow across breakpoints; the default for feeds and grids.
- **Grids & full-bleed imagery** — for visual, image-led content (galleries, retail).
- **Full-screen & focus modes** — remove chrome for immersion (reading, media, capture).
- **Inline expanding areas / hidden information** — progressive disclosure at the item level; reveal detail in place instead of a new screen.
- **Interactive content layers & direct manipulation** — let people act on content directly (drag, pinch, reorder) rather than through remote controls.
- **Pull-to-refresh** — the expected gesture to refresh a feed; pair with a loading indicator.
- **Empty states** — see `components-screens-states.md`: never a blank void; icon/illustration + message + the primary next action.

## 7. Onboarding & feedback patterns

- **Walkthroughs & coach marks** — brief, skippable overlays that point at real controls on first use. Prefer *showing* (immediate immersion) to *telling* where the product allows it; never trap the user behind a tutorial.
- **Notifications & badges** — mark new activity with a numbered badge, a dot, or an in-app banner; match salience to importance; announce politely (see `accessibility.md`).
- **Microinteraction anatomy** — every microinteraction has four parts (Saffer): **Trigger** (what starts it — a tap, a state change), **Rules** (what happens), **Feedback** (what the user perceives), **Loops & modes** (how long it lasts and whether it repeats). Design all four, not just the animation.

## 8. Social patterns

Activity feeds, follow, like/vote-to-promote, direct messaging, a single share button, find-and-invite. Use only when sharing genuinely serves the user's goal; a share button on everything is noise, not virality.
