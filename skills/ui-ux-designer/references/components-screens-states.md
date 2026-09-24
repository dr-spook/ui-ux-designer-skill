# Components, screens & states

Load when specifying anything interactive. Nothing is "done" until every relevant state is described.

Contents: the nine states + priority · mobile-first rules · how to specify a component · how to specify a screen.

---

## 1. Always specify every state

For every interactive component and every screen, define all relevant states:

- **Default** (at rest)
- **Hover** (pointer over)
- **Focus** (keyboard navigation — a clearly visible, contrasted focus ring; mandatory for accessibility; prefer a `focus-visible`-style ring so it doesn't appear on mouse click)
- **Active / Pressed** (the moment of click/tap; subtle scale 0.95–1.05 on tappable cards/buttons, restored on release)
- **Disabled** (action unavailable — reduced opacity ≈0.38–0.5 + `not-allowed` cursor; never color alone; semantically marked, not just visually dimmed)
- **Loading** (after a triggering action — **skeleton screen** preferred over a bare spinner for content; spinner acceptable for short isolated actions; button shows spinner and is disabled during async)
- **Empty** (no data yet — illustration or icon + a clear message + a primary action to move forward; an empty screen is an invitation to act, never a dead end)
- **Error** (what went wrong + how to recover; message + corrective action, paired with an icon and color)
- **Success** (confirmation feedback — checkmark, toast, or color flash)
- **Read-only** (where relevant — visually and semantically distinct from disabled)

**State priority (when several apply at once), highest to lowest:** `disabled → loading → active → focus → hover → default`. Specify which state wins so implementers don't guess.

---

## 2. Mobile-first, always

- **Describe the mobile version first, then tablet, then desktop.** Never deliver a desktop-only description.
- Scale fluidly between breakpoints (the `clamp(min, fluid, max)` philosophy): readable minimums on small screens, controlled maximums on large ones. Use **systematic breakpoints** (e.g. 375 / 768 / 1024 / 1440) consistently across the whole product.
- **Cap content width on ultra-wide screens** (≈`max-width 1200–1440px`, centered) so lines never stretch uncomfortably.
- **Prevent layout shift:** reserve space for images and async content using fixed aspect ratios or skeletons.
- Touch targets ≥ **44×44px** (iOS) / **48×48dp** (Android); primary actions in the thumb zone; clear of notch, Dynamic Island, gesture bar, and edges.
- **Respect safe areas top *and* bottom** for fixed headers, tab bars, and bottom CTA bars; add content insets so scrollable content is never hidden behind fixed/sticky bars.
- **Prefer native, platform-adaptive idioms** (iOS HIG vs Material): bottom tab bar for top-level iOS navigation, top app bar for Android, native controls before fully custom ones, platform-native easing.
- **Honor native semantics that auto-adapt:** describe colors by role so they map to system semantic colors (auto light/dark, accessibility settings); recommend **haptic feedback** for confirmations and important actions on capable platforms (sparingly); make data text **selectable/copyable**; format large numbers compactly (1.4M, 38k); use a **continuous corner curve** except for true capsule shapes.
- Support **Dynamic Type / system text scaling** and survive **200% browser zoom** (relative units rem/em); avoid truncation as text grows.
- **Touch has no hover.** Never make hover the only way to reach an action or reveal information — a hover-only control is invisible on a phone, and the first tap leaves a "stuck" hover state until the user taps elsewhere (gate hover styling behind a capability query). Size one-screen layouts with dynamic viewport units (`dvh`/`svh`), not `100vh`, so mobile browser chrome doesn't clip them.
- **Verify on real hardware.** Sticky hover, tap latency, safe areas, rubber-banding, and keyboard behaviour don't reproduce in desktop device-emulation; if you can't test on a device, say which specs are verified from the design and which need a real phone.

---

## 3. How to specify a component

For each reusable component provide: **name · purpose · anatomy · variants · sizes (sm/md/lg) · all states (Section 1) · tokens used · accessibility notes · one do / one don't.** Ensure cross-screen consistency — the same action keeps the same color, label, and style everywhere (no "Validate" button blue on one page and green on another).

Before designing a component from scratch, check `pattern-library.md` for the proven pattern that already solves the problem, and prescribe that — adapted to the subject — rather than reinventing it.

**Forms & defaults.** Labels always visible (never placeholder-as-label); validate on blur; show the error beside the field and focus the first invalid field on submit; split long forms into steps (Hick's Law). Set an input default **only** when the system can make a qualified guess or it clearly helps; make it easy to change; and never pre-fill a choice that needs the user's own decision (newsletter opt-in, terms acceptance, sharing scope).

Present variants, sizes, and states as compact tables plus an anatomy sketch. Example skeleton for a Button:

- **Variants:** default (primary) · secondary · outline · ghost · link · destructive — with their background/text/border tokens and use case.
- **Sizes:** sm (h32) · md (h40) · lg (h48) · icon — with padding-x/y, font size, icon size.
- **States table:** default / hover / active / focus / disabled / loading — with background, text, opacity, cursor per state.
- **Anatomy:** `[leading icon] Label [trailing icon]`, noting alignment and spacing.

---

## 4. How to specify a screen

For every screen/page provide:

- **Screen name and function.**
- **Visual description, mobile-first, top to bottom** (header → content → footer).
- **Component list with exact styles**, e.g. *"Primary button, size lg (height 48px), background `primary-600`, text white, radius 8px, soft shadow on hover, 150ms ease-out."*
- **States to plan** (loading / empty / error / etc.).
- **Expected behavior** (click, hover, transition, validation, navigation).
- **Motion** (entrance, transitions, gesture feedback — see `visual-system.md` §3).
- **UX copy** (labels, helper text, empty/error/success messages — see `copy-and-content.md`).
- **Responsive deltas** (mobile vs tablet vs desktop).
