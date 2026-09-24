# Copy & content — UX writing, resilience, i18n

Load when writing interface text or specifying content behavior. Words are design material — treat them with the same intentionality as spacing and color.

Contents: UX writing & microcopy · content resilience & internationalization.

---

## 1. UX writing & microcopy

Copy can make a design feel as templated as the visuals. Before writing any interface text, ask what the design needs to *say* and how it best helps the person navigate.

- **Define voice and tone.** *Voice* is the brand's consistent personality; *tone* adapts to context. Place the brand on the spectrums — Formal↔Casual, Simple↔Complex, Serious↔Playful, Reserved↔Expressive — and pick 3–5 traits ("confident, not arrogant"; "friendly, not unprofessional"). Tone shifts by context: more celebratory on success, more empathetic in support, more formal in legal.
- **Write from the user's side of the screen.** Name things by what people control and recognize, never by how the system is built ("Notifications," not "webhook config"). Describe what something does in plain terms; specific beats clever.
- **Active voice, consistent vocabulary.** A control says exactly what happens: "Save changes," not "Submit." An action keeps the same name through the whole flow — a "Publish" button produces a "Published" toast. Consistency is how people learn the product. Sentence case in body and labels; Title Case for prominent buttons/headings if the brand calls for it.
- **Errors give direction, not mood.** State what went wrong *and* how to fix it, in the interface's voice. Errors never apologize and are never vague ("Email must include an @," not "Invalid input"). Always include a recovery path (retry, edit, help).
- **Empty states are invitations to act** — a clear message plus the primary next action, never a blank void.
- **Mechanical polish:** real ellipsis `…` (not `...`); curly quotes; non-breaking spaces in units and brand names (`10 MB`, `⌘ K`); loading labels end with `…` ("Loading…"); numerals for counts ("8 deployments"); each element does exactly one job (a label labels, an example demonstrates).

---

## 2. Content resilience & internationalization

Specs must survive real, messy, multilingual content:

- **Anticipate short, average, and very long inputs** for every text container (names, titles, user-generated content). Define the wrap/clamp/truncate behavior and reserve min-width so flex children can shrink. Handle empty strings and empty arrays — never render a broken UI for "nothing."
- **Locale-aware formatting:** dates, times, numbers, and currency follow the user's locale (the `Intl` philosophy), never hardcoded formats. Detect language by user/browser preference, not by IP.
- **Protect identifiers:** brand names, code tokens, and identifiers must be flagged not-to-translate so auto-translation doesn't garble them.
- **RTL readiness:** note where layout, icons, and alignment must mirror for right-to-left languages.
