# Delivery & QA

Load before delivering. This is the output contract, the conflict-resolution order, and the mandatory QA gate.

Contents: the Interface & Journey Guide format · the Priority Framework (what wins when rules conflict) · self-critique & pre-delivery checklist · concrete do/don't · errors to strictly avoid.

---

## 1. Output format — "The Interface & Journey Guide"

Always deliver a single, self-contained **Markdown** document with these sections:

1. **Project Summary** — one paragraph: project type, sector, target audience, and the single job of the product/page.
2. **Personas, Information Architecture & Journey** — persona reminders (as job stories); the sitemap / IA; the primary user journey and key secondary flows.
3. **Design System Blueprint** (the Reasoning Engine result) — recommended pattern · style priority · color mood · typography mood · key effects (with timings) · conditional rules taken · **anti-patterns to avoid** · the signature element.
4. **Artistic Direction**
   - Sector adaptation: the chosen approach and *why*.
   - Color palette: names + hex codes (+ contrast notes), light and dark.
   - Typography: font(s), full scale, weights, line-heights, letter-spacing.
   - Spacing system: grid, gutters, margins, section-spacing tiers.
   - Radius, shadow/elevation scale, border treatment, z-index scale.
5. **Selected Icon Library** — justified by the technical environment, with size tokens and stroke discipline.
6. **Design System** — reusable component styles (buttons, inputs, cards, modals, navigation, tables, charts, etc.) as three-layer tokens, with variants, sizes, and all states.
7. **Screens** — exhaustive screen-by-screen description (visual, components, states, behavior, motion, copy, responsive deltas).
8. **Navigation Flow** — how the user moves screen to screen; primary vs secondary nav; deep-linking; back/state preservation.
9. **Motion Choreography** — global duration/easing tokens and per-flow transitions.
10. **UX Copy** — voice & tone profile; key labels, helper texts, empty/error/success messages.
11. **Data Visualization** — chart specs where applicable. *(Omit if the product has no data viz.)*
12. **Accessibility Rules Applied** — contrasts, sizes, focus, heading order, reduced-motion, dynamic type.
13. **Developer Notes** — attention points, edge cases (very long names → wrap or ellipsis; empty arrays; long UGC; i18n/RTL), pitfalls, integration recommendations.
14. **Self-Critique & QA Log** — what generic default you rejected and why; the Pre-Delivery Checklist results.
15. **Store creative assets** *(mobile-app projects with an ASO brief only)* — icon, screenshot set, and preview-video poster executed from the ASO brief; omit entirely otherwise.

---

## 2. Priority Framework — what wins when rules conflict

When constraints collide (brand boldness vs legibility, density vs touch comfort), resolve in this fixed order. Higher tiers are non-negotiable and override lower ones. Use this table as the spine of the final QA pass: confirm tiers 1–3 are flawless before polishing anything below.

| # | Category | Impact | Must-have checks | Anti-patterns to flag |
|---|---|---|---|---|
| 1 | **Accessibility** | CRITICAL | Contrast ≥4.5:1 (text) / ≥3:1 (large & UI); alt text; keyboard nav; visible focus; aria/accessibility labels; reduced-motion; dynamic type | Removing focus rings; icon-only buttons without labels; color as sole signal; disabling zoom |
| 2 | **Touch & Interaction** | CRITICAL | Targets ≥44×44px; ≥8px spacing; press feedback ≤150ms; loading feedback on async | Hover-only interactions; 0ms instant state changes; tiny tap targets; blocking system gestures |
| 3 | **Performance (perceived)** | HIGH | Reserve space for async content (no layout shift); skeletons for >300ms loads; virtualize lists >50 items; specify aspect ratios | Layout thrashing; CLS; long blocking spinners |
| 4 | **Style Selection** | HIGH | Match style to product type; one consistent style across pages; SVG icons (no emoji) | Mixing flat & skeuomorphic at random; emoji as icons; generic "SaaS default" |
| 5 | **Layout & Responsive** | HIGH | Mobile-first; systematic breakpoints; no horizontal scroll; capped content width | Fixed px widths; horizontal scroll on mobile; desktop-only specs |
| 6 | **Typography & Color** | MEDIUM | Base ≥16px body; line-height ~1.5; semantic tokens not raw hex in components | Body <12px; gray-on-gray; raw hex per component |
| 7 | **Animation** | MEDIUM | 150–300ms micro-interactions; motion conveys meaning; spatial continuity; reduced-motion respected | Decorative-only motion; animating width/height; no reduced-motion variant |
| 8 | **Forms & Feedback** | MEDIUM | Visible labels; error near field; helper text; progressive disclosure; validate on blur | Placeholder-as-label; errors only at top; overwhelming the user upfront |
| 9 | **Navigation Patterns** | HIGH | Predictable back; bottom nav ≤5; deep-linkable screens; active-state highlight; state preservation | Overloaded nav; broken back behavior; mixed nav patterns at one level |
| 10 | **Charts & Data** | LOW–HIGH (data products: HIGH) | Match chart to data type; legends & tooltips; accessible color + pattern; table fallback | Color-only meaning; pie for >5 categories; broken/empty chart on no-data |

---

## 3. Self-critique & pre-delivery QA (mandatory)

Work in two passes: **plan → critique against the brief → produce → critique again.** Before delivering, do the following briefly in the QA Log:

- **Anti-default check:** if any part of the direction reads like the generic answer you'd give *any* similar brief (mentally run a near-identical prompt and see if you land in the same place), revise it and state what changed and why.
- **"Remove one accessory" (Chanel):** look over the whole design and cut the one element that adds the least. Restraint reads as polish.
- **Squint test:** blur your eyes over the screen. You should perceive the hierarchy and grouping without any harsh border or element jumping out; craft whispers.
- **Signature test:** point to the specific elements (not "the overall feel") where the signature element actually shows up. If you can't, the direction never left prose.
- **Run the Priority Framework top to bottom**, confirming tiers 1–3 (Accessibility, Touch, Performance) are flawless before anything else.

**Pre-Delivery Checklist:**
- [ ] No emojis as icons; one consistent icon family, consistent stroke and sizing.
- [ ] Every interactive element has all relevant states, including a visible focus ring.
- [ ] Touch targets ≥44×44px with ≥8px spacing; press feedback ≤150ms.
- [ ] Light **and** dark mode contrast checked independently (text ≥4.5:1, large/UI ≥3:1).
- [ ] No layout shift: async content has reserved space / skeletons; images have aspect ratios.
- [ ] Color is never the sole signal; errors pair color + icon + text.
- [ ] Reduced-motion variant defined; system text scaling survives without breakage.
- [ ] Every animation is justified by frequency and purpose (none on high-frequency/keyboard-initiated elements); entrances start from ~0.9–0.97, not 0; motion is interruptible.
- [ ] Responsive verified at 375 / 768 / 1024 / 1440 and in landscape; no horizontal scroll; safe areas respected top and bottom.
- [ ] One primary CTA per screen; consistent action vocabulary through each flow.
- [ ] Empty, error, and success states written, not just default.
- [ ] Long names, empty arrays, and long user-generated content handled.
- [ ] Charts (if any) have legend, tooltip, accessible color+pattern, and a table/text fallback.
- [ ] No code written; no stack chosen beyond the architect's blueprint.

---

## 4. Do / Don't (concrete)

- **DON'T:** "Add a nice button here."
  **DO:** "Primary button, size lg (height 48px, horizontal padding 24px), background `primary-600`, label white 16px/600 (contrast 7.2:1), radius 8px. Hover: `primary-700` + soft shadow (y-2, blur-8, 8% black), 150ms ease-out. Focus: 2px `primary-300` ring offset 2px. Disabled: `primary-600` at 40% opacity, cursor not-allowed. Loading: label hidden, centered spinner."
- **DON'T:** A rainbow or multi-stop gradient hero.
  **DO:** A solid `primary-700` hero, or a subtle two-tone shift within one hue; let typography and one accent carry the impact.
- **DON'T:** Default to AI purple/pink gradients or a cream + serif + terracotta template.
  **DO:** Derive the palette from the product's sector and subject; take one justified aesthetic risk as the signature element.
- **DON'T:** Use an emoji for search.
  **DO:** Use the `Search` icon from the chosen family (e.g. lucide-react / Phosphor) at 20px, `text-medium` color, consistent stroke weight.
- **DON'T:** Signal a form error with a red border only.
  **DO:** Red border + `AlertCircle` icon + helper text "This field is required."
- **DON'T:** Validate on every keystroke and dump all errors at the top.
  **DO:** Validate on blur, show the error below the field, and focus the first invalid field on submit.
- **DON'T:** Separate every section with grey 1px lines.
  **DO:** Separate with white space and a faint surface-shade change; add a soft shadow only to lift a card.
- **DON'T:** Put 30 fields on one signup screen.
  **DO:** Split into a 3–4 step wizard with a progress indicator (Hick's Law), revealing advanced options progressively, with autosaved drafts so nothing is lost on dismissal.
- **DON'T:** Label a button "Submit" and confirm with "Success."
  **DO:** "Save changes" → toast "Changes saved." Same vocabulary through the flow.

---

## 5. Errors to strictly avoid

Generic SaaS style with no sector adaptation · the "AI-generated default" looks (cream+serif+terracotta, near-black+acid-green, broadsheet hairlines, AI purple/pink gradients) · aggressive/amateur gradients · hard shadows or crude black outlines · random per-card shadow/elevation values · emojis instead of icons · mixed icon styles or strokes · visual inconsistency across screens · token drift (same action different color/label) · missing states (loading, empty, error, focus) · colors below WCAG contrast · removing focus rings · color as the sole signal · placeholder-as-label · errors only at the top · validating on every keystroke · multiple competing primary CTAs · vague descriptions ("a nice button") · decorative-only animation / animating width-height / no reduced-motion · ignoring safe areas and dynamic type · encroaching on the architect (stack decisions) · encroaching on front-end (writing code) · ignoring responsive (desktop-only descriptions) · charts that rely on color alone or lack a table fallback · hardcoded date/number formats.
