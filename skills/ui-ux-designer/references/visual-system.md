# Visual system — laws, tokens, motion, iconography

Load when specifying the look or the token system.

Contents: visual design laws (strict) · design foundations & tokens (color, typography, spacing/grid, radius/shadow/border, z-index) · motion choreography · iconography (incl. per-stack icon libraries).

---

## 1. Visual design laws (strict enforcement)

- **Design in monochrome first.** Build the entire layout in greys, black, white, and space. If it is legible and well-hierarchized without color, the structure is sound. Color is a finishing layer, never a patch for weak hierarchy.
- **No aggressive, complex, or amateurish gradients.** Prefer solid fills or subtle background-shade contrasts (e.g. a white card on a `#F8FAFC` page). A gradient, if ever used, is barely perceptible and two-tone within the same hue. **Never** use AI purple/pink gradients as decoration.
- **Shadows must be extremely soft** — the equivalent of `shadow-sm` / `shadow-md`: low opacity (≈4–12% black), small offset, diffuse blur. **Never hard shadows or crude black outlines.** Define a **consistent elevation/shadow scale** (sm/md/lg) and use only those steps — never invent random shadow values per card.
- **De-emphasize borders.** To separate elements, prefer (in order): more white space → a different background shade → a soft diffuse shadow. Reach for a 1px border only when nothing else works. Too many lines make an interface heavy.
- **Use strict scales — never pixel-push.** Define a type scale and a spacing scale once, then only use those steps. If 24px feels too small, jump to the next step (30px); never invent 27px.
- **Color semantics over saturation.** Reserve vivid, saturated colors exclusively for actions and critical states (primary CTAs, notifications, errors). For secondary text, reduce *contrast* (deep black → slate grey) rather than changing size. If everything is colorful, nothing stands out.
- **White space is a deliberate art-direction tool**, not wasted space — it signals premium quality and clarity and powers Gestalt proximity.
- **Build hierarchy with weight, size, contrast, and case** — not by making everything bigger.
- **One primary CTA per screen.** Exactly one primary action with the contrasting accent; all secondary actions visually subordinate. Multiple competing "primary" buttons destroy hierarchy.
- **Effects must match the chosen style.** Shadow, blur, radius, and motion all belong to the same system (glass / flat / clay / minimal). **Blur has a purpose** — it signals background dismissal for modals and sheets, not decoration.
- **Match execution complexity to the vision.** A minimal direction lives or dies on spacing and type precision; a maximalist direction must be elaborate and consistent everywhere. Never half-execute.

### The laws you design by (psychology, not preference)

- **Hick's Law:** decision time grows with the number/complexity of options. Split long forms or dense choices into sequential steps (a Wizard); never dump 30 fields on one screen.
- **Fitts's Law:** larger, closer targets are faster. Make primary actions large and reachable (bottom of screen on mobile, in the thumb zone). Make destructive actions (Delete account) deliberately smaller and offset to prevent mis-taps. Minimum touch target **44×44px**.
- **Von Restorff (isolation):** the element that differs is remembered. Give the single key action a contrasting accent so the eye finds it instantly. If everything is emphasized, nothing is.
- **Gestalt — Proximity:** related items close together; unrelated items get more space. The gap *above* a heading must exceed the gap *below* it, so it binds to the text it introduces.
- **Gestalt — Similarity:** elements sharing color/shape/size read as the same kind. Keep all links one consistent style; never style non-interactive text like a link.
- **Gestalt — Continuity:** the eye follows aligned paths. Let the next card peek off the screen edge to signal "swipe for more."
- **Gestalt — Closure:** the brain completes incomplete shapes. Exploit it for minimal icons and circular loaders.
- **F-pattern / Z-pattern scanning:** users scan, they don't read. Place strong cues (bold keywords, anchor icons, action buttons) on these natural sweep lines.

---

## 2. Design foundations & tokens

Think in **semantic design tokens**, in **three layers** so the system supports theming, dark mode, and clean handoff:

```
Primitive  (raw values)        --color-blue-600: #2563EB;  --space-4: 1rem;
    ↓
Semantic   (purpose aliases)   --color-primary: var(--color-blue-600);  --spacing-section: var(--space-16);
    ↓
Component  (component scope)    --button-bg: var(--color-primary);
```

Name by role (`color-brand-primary`, `color-text-body`), not by raw value. Primitives rarely change; semantic aliases drive theme switching; component tokens handle per-component needs.

**Color palette** — define and give hex codes for:
- `primary`, `secondary`, `accent` (the CTA color that contrasts decisively)
- semantic: `success`, `warning`, `error`, `info`
- `surface` levels (page background, elevated/card)
- `text` emphasis levels (high / medium / low) and `border`
- Note the contrast ratio of each text-on-surface pairing. If dark mode is required, define it via semantic aliases (e.g. `color-text-body` → near-black in light, near-white in dark). **Dark mode uses desaturated / lighter tonal variants, not naive inversion, and is contrast-tested independently** — never assume light-mode values carry over. Dark surfaces are **never pure `#000`** — use a near-black (≈`#0a0a0a`–`#121212`) so elevation and shadow can still register.
- Build ramps in a **perceptually-uniform space** (e.g. oklch) so steps feel evenly spaced and hue stays stable across lightness; you can still hand off hex. Keep WCAG 2.1 AA (§`accessibility.md`) as the contrast bar.
- Give each color a **mini monochromatic ramp** (tints/shades) so the system can scale; add a hint of the brand hue into greys and blacks so they don't read as harsh pure-neutral.
- **Choose a harmony scheme deliberately** and name it: *monochromatic* (one hue, shades — calmest), *analogous* (three adjacent hues — blended), *complementary* (opposite hues — high contrast, prominent), *split-complementary* (one hue + the two beside its opposite — bright but softer), *triadic* (three hues 120° apart — bold, balanced), *tetradic* (four hues — hardest to balance; usually stick to three or fewer).
- **Proportion with 60-30-10:** ~60% dominant/surface, ~30% secondary, ~10% accent (the CTA). This keeps the accent scarce enough to mean "act here."

**Typography:**
- Choose font(s) and justify the pairing (contrast but historically/structurally coherent — e.g. an elegant serif heading with a clean geometric sans body). Make the type treatment itself a memorable part of the design. Map to brand: serif for tradition/luxury/editorial; geometric sans for modern/tech/efficient.
- Define a full type scale (h1 → caption) with **size / weight / line-height / letter-spacing** per level. **Derive it, don't pick sizes by hand:** choose a base (usually 16px) and a modular ratio, then step up/down by it — common ratios are 1.2 (minor third), 1.25 (major third), 1.333 (perfect fourth), 1.618 (golden). One ratio, applied consistently, is what makes a scale feel composed.
- Body text minimum **16px** (14px absolute floor for secondary text). On mobile, never below 16px for inputs (prevents iOS auto-zoom).
- Line-height: **140–160%** for body, **110–120%** for large headings.
- Measure: **45–75 characters** — cap text containers at ~`65ch` / `~650px` (mobile 35–60 chars).
- Build hierarchy through weight and case (small-caps or uppercase + positive tracking for category labels), not size alone. Weight guide: bold headings 600–700, regular body 400, medium labels 500.
- **Tabular / monospaced figures** for data columns, prices, timers, counters so values don't shift. Respect platform default letter-spacing; avoid tight tracking on body text.
- **Truncation:** prefer wrapping over truncation; when you must truncate, use an ellipsis and expose full text via tooltip/expand. Apply heading balancing to prevent widows.

**Spacing & grid:**
- Strict scale on a **4px or 8px** base (e.g. 4, 8, 12, 16, 24, 32, 48, 64).
- A 12-column responsive grid with defined gutters; respect a vertical baseline rhythm. Never let an element straddle a gutter. Define section-spacing tiers (e.g. 16 / 24 / 32 / 48) by hierarchy; widen gutters on larger/landscape widths.
- **Name the layout strategy:** *fixed* (constant width regardless of viewport), *fluid* (stretches/shrinks with the viewport), or *adaptive* (swaps to a different grid at breakpoints). Default to fluid within capped max-width, adapting the column count at the systematic breakpoints (375 / 768 / 1024 / 1440).

**Radius, shadow, border:** a small radius scale, a soft shadow/elevation scale (sm/md/lg), and the minimal border treatment.

**Depth strategy — pick one and commit.** A product reads as coherent when depth comes from *one* system, not a mix: **borders-only** (dense tools), **subtle shadows** (approachable), **layered shadows** (premium cards), or **surface-tint shifts** (elevation by background lightness). Don't blend strategies at random.

**Surface elevation.** Surfaces stack: base → cards → dropdowns → overlays. Number them and move in small steps — in dark mode, higher elevation = *slightly lighter* (a few percent), not a dramatic jump; keep the same hue and shift only lightness across surfaces. Practical defaults: a **sidebar** shares the canvas background + a subtle border (a different colour fragments the space); an **input** sits slightly inset/darker than its surroundings to signal "type here"; a **dropdown** is one level above its parent surface. The squint test applies: blur your eyes and you should perceive the hierarchy without any harsh line jumping out.

**Z-index:** a layered scale (e.g. 0 / 10 / 20 / 40 / 100 / 1000) so stacking is predictable; avoid nested scroll regions that fight the main scroll.

**Motion tokens:** purposeful only — feedback, attention, or reduced perceived wait. Durations **100–300ms** (complex ≤400ms; avoid >500ms). Easing: **ease-out** entering, **ease-in** leaving; never linear. Respect reduced-motion. Full choreography below.

---

## 3. Motion choreography

Specify motion as a system, not per-element whimsy. Define global duration/easing tokens and apply them consistently.

- **Should it animate? Frequency decides.** The more often an element is seen, the less it should move. Something triggered 100+ times a day (keyboard shortcuts, a command palette) gets **no** animation; something seen tens of times a day (hovers, list nav) gets minimal; occasional surfaces (modals, drawers, toasts) get standard motion; rare/first-time moments (onboarding, success, celebration) can carry delight. "It looks cool" is never a reason to animate a frequently-seen element. A valid reason is one of: spatial continuity, state change, explanation, feedback, or preventing a jarring jump.
- **Meaning first:** every animation expresses a cause-effect relationship; animate 1–2 key elements per view, never everything.
- **Respond on press, not release.** Feedback is instant on pointer-down, and continuous *during* an interaction (a drag/slider/drawer tracks the finger 1:1 the whole way, respecting where it was grabbed) — never only at the end. Latency kills the feeling of directness.
- **Performance:** animate `transform` and `opacity` only — never width/height/top/left; motion must never cause reflow or layout shift.
- **Duration:** UI motion stays **under ~300ms** (a 180ms dropdown feels more responsive than a 400ms one). Rough guide: press feedback 100–160ms · tooltips/small popovers 125–200ms · dropdowns/selects 150–250ms · modals/drawers 200–500ms · marketing/explanatory can be longer.
- **Easing:** entering/exiting → **ease-out** (fast start, feels responsive); moving/morphing on screen → **ease-in-out**; hover/color → **ease**; constant motion (marquee, progress) → **linear**. Avoid slow-starting **ease-in** on UI — it delays the exact frame the user is watching. Built-in curves are weak; specify a stronger custom curve.
- **Physicality:** nothing appears from nothing — never scale from 0; start entrances at scale 0.9–0.97 + fade. Popovers/menus are **origin-aware** (they scale from their trigger, not their center); modals are the exception and stay centered. Pressable elements get a subtle press-down (~scale 0.97).
- **Springs for anything touchable.** Think in **bounce/damping** (overshoot) and **response** (snappiness) — a spring has no fixed duration, it settles. Keep bounce subtle (≈0.1–0.3) and avoid bounce in most UI; reserve it for drag-to-dismiss and playful moments. Springs carry velocity through interruptions, which is exactly what gestures need.
- **Asymmetry:** exit animations are shorter than enter (~60–70%) so the UI feels responsive.
- **Continuity:** screen transitions preserve spatial logic — forward navigates left/up, backward right/down; sheets animate from their trigger; use shared-element/hero transitions between related screens.
- **Lists:** stagger item entrance ~30–50ms each; never all-at-once or too-slow.
- **Interruptible & non-blocking:** never lock input during a transition. On interrupt or reversal, animate from the element's **current on-screen value**, not its target, so nothing jumps; blend velocity rather than hard-cutting. (This is why gesture-driven motion prefers springs over fixed keyframes.)
- **Loading:** show a skeleton/shimmer for operations >300ms instead of a long blocking spinner.
- **Restraint:** extra animation is a classic "AI-generated" tell — when in doubt, less is more.
- **Anatomy:** every microinteraction has four parts — Trigger, Rules, Feedback, Loops & modes (detailed in `pattern-library.md`). Specify all four, not just the visible animation.

---

## 4. Iconography (strict)

- **Never use emojis** in any interface, mockup, or screen description. Ever. Emojis are font-dependent, inconsistent across platforms, and cannot be tokenized.
- **Vector-only assets.** SVG / platform vector icons that scale cleanly and theme correctly. Never raster PNGs that blur.
- Use **one** icon family throughout, consistent style, stroke weight, and size, with clear semantic meaning (trash = delete; magnifier = search).
- **Stroke consistency:** one stroke width within a visual layer (e.g. 1.5px or 2px). **Filled-vs-outline discipline:** one icon style per hierarchy level; don't mix filled and outline at the same level.
- **Size as tokens:** define `icon-sm`, `icon-md` (24px), `icon-lg`; never scatter arbitrary 20/24/28 values. **Align** icons to the text baseline with consistent padding.
- **Icon contrast:** meet WCAG (≥3:1 for larger glyphs, ≥4.5:1 for small/essential ones) in both light and dark mode.
- Select the library based on the project's technical environment:

| Environment | Approved icon libraries |
|---|---|
| **React / Next.js / Vite** | `lucide-react`, `@phosphor-icons/react`, `@heroicons/react` (v2), `react-icons` (specify the sub-set: `fa`, `md`, `io`, etc.), or `@tabler/icons-react` |
| **Vue.js** | `lucide-vue-next`, `oh-vue-icons`, or `@heroicons/vue` |
| **Angular** | `ng-lucide`, `@ng-icons/core`, or FontAwesome Angular |
| **React Native / Expo** | `@phosphor-icons/react-native`, `@expo/vector-icons`, or platform SF Symbols / Material Symbols |
| **Pure HTML / CDN / classic Tailwind** | inline SVG (Heroicons, Lucide, Phosphor), FontAwesome CDN (6+), or Google Material Symbols |
| **CSS frameworks** | FontAwesome Icons, Bootstrap Icons, or Remix Icon (matched to the chosen framework) |

If the stack is unknown, default to **Lucide** (clean, neutral, portable) — or **Phosphor** for mobile/native-leaning products — and state the choice should be confirmed against the architect's blueprint. **When the recommended set lacks a fitting icon, pick the closest semantic match from the same family before switching families; if you must fall back, keep stroke weight, corner radius, and fill style consistent.**
