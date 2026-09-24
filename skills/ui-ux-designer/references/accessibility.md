# Accessibility — WCAG 2.1 AA (non-negotiable)

Load whenever you specify anything interactive. Accessibility is designed in from screen one, baked into the design system — never bolted on at the end.

- **Contrast:** ≥ **4.5:1** for normal text; ≥ **3:1** for large text (≥24px or 18px bold) and essential UI components (input borders, clickable icons). Data-text labels on charts ≥4.5:1; data marks vs background ≥3:1.
- **Never use color as the sole carrier of information.** Pair it with an icon and/or text (≈8% of men have red/green color-blindness). Example: an error field gets a red border **and** an alert icon **and** explanatory text.
- **Visible focus state** on every interactive element for keyboard users; never remove the focus ring without an equivalent replacement.
- **Semantic heading hierarchy** (logical h1 → h6, no skipped levels; specify it). Provide a skip-to-content affordance for keyboard users.
- **Labels** on every input; meaningful, explicit error messages ("Phone number must be 10 digits," not "Error"). After a submit error, move focus to the first invalid field; for multiple errors, show a summary with anchor links.
- **Announce async updates** (toasts, validation, status) via a polite live region; toasts must not steal focus.
- **Touch targets ≥ 44×44px**; recommend relative units (rem/em) so the layout survives 200% browser zoom.
- **Respect `prefers-reduced-motion`** (provide a reduced/disabled variant) and **system text scaling / Dynamic Type** (no layout breakage as text grows).
- **Never disable zoom** (`user-scalable=no` / `maximum-scale=1` are forbidden).
- **Modals & multi-step flows** always offer a clear escape/cancel/back route; preserve and announce focus order matching visual order.
- **Charts** ship with a text summary or `aria-label` of the key insight and a data-table fallback; interactive marks are keyboard-reachable.

## Semantic structure — your spec is canonical; Discoverability layers on top

Heading order, landmark regions, alt text, and descriptive link text are **your** accessibility deliverable. On web projects a Discoverability/SEO spec may add requirements on the *same* elements — keyword-aware headings, descriptive anchor text for link equity, structured-data hooks. These **extend**, they don't replace: keep your accessibility structure as the baseline and fold SEO additions in where they don't harm clarity or accessibility. **One** heading hierarchy reaches the front-end, not two.
