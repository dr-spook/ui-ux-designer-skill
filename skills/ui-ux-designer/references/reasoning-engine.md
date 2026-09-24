# Reasoning Engine — how you derive a design system

Load this **first**, before any visual choice. Never improvise a look; **derive** it and write down the result, justifying each link.

Contents: the derivation chain · the sector-adaptation table (highest priority) · the "AI-generated default" tells to escape · the Master-spec + page-overrides consistency model.

---

## 1. The derivation chain

For the product at hand, reason through this chain and record the result, then justify each link:

`Product type` → `Recommended pattern` → `Style priority` → `Color mood` → `Typography mood` → `Key effects (with timings)` → `Conditional decision rules` → `Anti-patterns to avoid` → `Severity`

- **Recommended pattern** = the macro-structure that converts for this product (e.g. *Hero + Features + CTA*; *Hero + Social Proof + CTA*; *Data-Dense Dashboard*; *Storytelling-Driven*; *Feature-Rich Showcase*; *Minimal & Direct + Demo*).
- **Style priority** = the dominant aesthetic system (e.g. *Minimalism/Swiss*, *Glassmorphism*, *Flat*, *Soft UI / Neumorphism*, *Claymorphism*, *Brutalism*, *Motion-Driven*, *Dark Mode OLED*, *Editorial/Magazine*, *Bento Grid*), chosen to fit the sector — never at random.
- **Color mood / Typography mood** = the emotional and tonal targets (e.g. *Trust blue + decisive accent*; *Premium + minimal accent*; *Calm blue/green, large readable type*).
- **Key effects** = the motion and depth language *with concrete timings* (e.g. *subtle hover 200–250ms*, *card lift 200ms*, *real-time number animation + alert pulse for dashboards*, *fluid 400–600ms for luxury*).
- **Conditional decision rules** = "if/then" branches that adapt the system to context. Examples: *if luxury → liquid-glass / refined elegance*; *if conversion-focused → urgency accent colors*; *if data-heavy → depth/glassmorphism layering*; *if pre-launch → waitlist pattern*; *if checkout → trust signals*; *if healthcare/medical → WCAG AAA*; *if gamified → progress animations*. Surface the branches you took.
- **Anti-patterns** = what to explicitly avoid for *this* sector (e.g. *no dark-mode-by-default for general SaaS*; *no flat-without-depth for e-commerce*; *no vibrant/block for luxury*; *no low-contrast neumorphism where accessibility is critical*).
- **Severity** = how strict the rule is (CRITICAL / HIGH / MEDIUM / LOW). CRITICAL and HIGH rules win every trade-off.

Translate this chain into the **Artistic Direction** section of the deliverable. Always include the **"Avoid (anti-patterns)"** line so the implementer knows the boundaries, not just the targets.

---

## 2. Sector adaptation (HIGHEST PRIORITY)

**It is strictly forbidden to apply a generic, one-size-fits-all "SaaS" style.** Translate the brand's values into concrete aesthetic decisions: typography is the *tone of voice*, color is the *dominant emotion*, imagery/iconography is the *visual universe*. Every sector demands a different psychological and demographic target.

| Sector | Art direction & rationale (pattern · style · color/type mood · effects · avoid) |
|---|---|
| **SaaS B2B / Productivity** | Professional, clear, efficient, trustworthy. Pattern: Hero + Features + CTA. Style: Glassmorphism + Flat / Minimalism. Restrained palette, neutral surfaces, strong data legibility, one decisive accent. Subtle hovers 200–250ms. *Avoid:* excessive animation, dark-mode-by-default. (Reference feel: Linear, Stripe.) |
| **Micro-SaaS / Indie** | Modern, energetic, fast to grasp. Pattern: Hero-centric + Trust / Demo. Style: Flat + Vibrant Block, Motion-driven. Bold primaries + accent. Scroll-triggered reveals. *Avoid:* static, no-video, poor mobile. |
| **E-commerce / Retail** | Engaging, clear hierarchy, product-forward. Pattern: Feature-Rich Showcase. Style: Vibrant & Block. Brand primary + success green. Card hover-lift 200ms + scale. *Avoid:* flat-without-depth, text-heavy pages. |
| **E-commerce / Luxury** | Premium, minimal, white-dominant, storytelling through large imagery and generous white space. The product is the hero; the UI recedes. Style: Liquid Glass / refined elegance. Premium colors + minimal accent. Fluid 400–600ms. *Avoid:* vibrant block, playful colors. |
| **Healthcare / Wellness** | Reassuring, clean, accessible. Soft tones (calm blues/greens), high readability, gentle contrast, no aggressive reds except for genuine alerts. Large type (16px+). *If medical:* enforce WCAG AAA. *Avoid:* low-contrast neumorphism, harsh motion. |
| **Education / Kids** | Playful but legible. Controlled bright, saturated colors; rounded, thick type; large touch targets; friendly illustration (Claymorphism + micro-interactions). *If gamified:* add progress animations. Never sacrifice readability for fun. |
| **Finance / Banking** | Serious, navy/grey, data-dense, maximum legibility and trust. Conservative layout, conventional element placement, rigorous hierarchy. *Avoid:* decorative flourish over clarity. |
| **Financial / Analytics Dashboard** | Data-dense, scannable, real-time. Style: Data-Dense / Dark-Mode OLED, heat-map gradients where apt. Trust blue + red/green alerts. Real-time number animation + alert pulse. *Must-have:* real-time updates, data export, drill-down. |
| **Social / Community** | Engaging, warm, rich micro-interactions, content-forward, lively but not chaotic. |
| **Creative Agency / Portfolio** | Storytelling-driven, expressive. Style: Motion-driven / Brutalism (where the brand allows). Bold, artistic. Parallax (sparingly), scroll-triggered reveals. *Must-have:* case studies. |
| **Any other** | Rigorously map color theory, type, density, and motion to the sector's demographic and psychological target. State your reasoning. |

Before committing a direction, mentally validate it like a stylescape: one hero section, one heading, one paragraph, one key component — does the feel match the brand? If yes, scale it.

---

## 3. Escape the "AI-generated default" look

Generic AI design clusters around a few tells. Treat these as **defaults to escape, not choices**, unless the brief explicitly asks for one (the brief's own words always win):

- A warm cream background (~`#F4F1EA`) with a high-contrast serif display and a terracotta accent.
- A near-black background with a single bright acid-green or vermilion accent.
- A broadsheet/newspaper layout: hairline rules, zero radius, dense columns — used regardless of subject.
- **AI purple/pink gradients** and rainbow multi-stop gradients as a hero crutch.
- A big number + small label + supporting stats + gradient accent as the "default hero" — only use if it is truly the best answer for this subject.

Where the brief leaves an axis free, **don't spend that freedom on a default.** Take one real, justifiable aesthetic risk rooted in the subject's world — that becomes your signature element.

---

## 4. Consistency model — Master spec + page overrides

Structure the design system as a **hierarchy**, not a flat list, to guarantee cross-screen and cross-session consistency:

- **MASTER (Global Source of Truth).** All global rules: tokens, palette, type scale, spacing, radius/shadow scales, component library, motion tokens, voice & tone. Every screen inherits from Master by default.
- **PAGE OVERRIDES.** Per-page deviations only (e.g. Checkout emphasizes trust; Dashboard raises data density). An override **replaces** the corresponding Master rule for that page only.

**Retrieval rule when specifying any page:** first apply the page's override block if one exists; otherwise apply Master exclusively. Never silently contradict Master — every deviation is explicit and justified. Same action → same color, label, and behavior everywhere, with intentional documented exceptions.
