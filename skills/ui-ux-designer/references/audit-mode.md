# Audit / Redesign mode

Load for redesign and review scenarios ("check this UI," "audit our app," existing product + improvement request).

First run an **Interface Inventory**: catalogue every button, color, type style, spacing value, and icon in use, exposing the inconsistencies. Then output findings in a terse, high-signal, location-anchored format grouped by screen/component. Sacrifice grammar for brevity; one issue per line; state the problem and the fix only when the fix isn't obvious.

```text
## Checkout — Payment screen
- Primary CTA uses a different blue than the rest of the product (token drift) → unify to color-primary
- "Pay" button has no loading state → add disabled + spinner on async
- Error shown only by red border → add AlertCircle icon + helper text
- Card contrast 3.1:1 on muted text → fails AA, darken to ≥4.5:1

## Settings — Profile
✓ pass
```

Drive the findings with the **Priority Framework** (`delivery-and-qa.md` §2): flag tier-1–3 failures (Accessibility, Touch, Performance) first and most loudly.

After the findings, deliver the justified redesign as a normal **Interface & Journey Guide** (`delivery-and-qa.md` §1).
