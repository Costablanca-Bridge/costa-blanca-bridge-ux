# CostablancaBridge — UX Principles

**Version:** 1.0 · April 2026
**Owner:** UX Lead

These seven principles govern every design decision at Costa Blanca Bridge — across the website, client portal, AI employee interfaces, onboarding flows, and any other digital touchpoint. When two design options compete, these principles are the tiebreaker.

---

## Principle 1 — Trust is the Product

Costa Blanca Bridge operates in cross-border legal, financial, and immigration territory. Every pixel must earn trust. Users are handing us their company structures, their immigration status, or their investment capital. The experience must feel safer than a law firm and more responsive than a bank.

**In practice:**
- Show credentials, case studies, and real outcomes — not vague promises
- Use professional typography and precise language — no playful language near legal or financial content
- Surfaces must feel polished and complete — nothing half-finished should reach a client
- Error messages are calm, clear, and actionable — never alarming
- Data entry forms explain *why* information is needed, not just *what* is needed

---

## Principle 2 — Clarity Over Cleverness

Our clients are senior business people, investors, and professionals. They do not have time for ambiguity. The interface should communicate what Costa Blanca Bridge does and how to engage within 60 seconds of arrival.

**In practice:**
- Headlines state the benefit, not describe the service
- Navigation labels are plain English — no jargon, no invented terms
- Every page has one primary action — never compete with yourself
- Avoid multi-step tooltips for features that should be self-evident
- If something needs explaining, the design has failed — simplify first

---

## Principle 3 — Global Audience, Local Warmth

Costa Blanca Bridge's clients arrive from the UK, Netherlands, Russia, Cuba, North America, and across the emerging world. The UX must feel globally neutral and locally welcoming simultaneously.

**In practice:**
- No idioms or cultural references that won't translate
- Date formats: always DD Month YYYY (not MM/DD/YYYY or DD/MM/YYYY)
- Currency defaults: EUR, with GBP and USD available
- Right-to-left language support considered in layout (avoid hard-coded left-alignment for text)
- Photographs and illustrations represent diverse, international people
- Response times account for international time zones — never assume same-day availability

---

## Principle 4 — Hierarchy of Confidence

Not all users arrive equally ready. Some are researching. Some are ready to act. Some are mid-deal. The UX must serve all three states without forcing premature commitment.

**Three user states to design for:**
1. **Discovery** — browsing, comparing, learning. Need: reassurance and clarity
2. **Consideration** — specific need identified, evaluating Costa Blanca Bridge. Need: proof and specificity
3. **Ready** — wants to act now. Need: zero friction to contact/book

**In practice:**
- Information hierarchy moves from general → specific as the user scrolls
- Every page has a visible, low-commitment entry point ("Book a 30-min call" not "Submit your case")
- Case studies and testimonials sit between service descriptions and CTAs
- Never gate content that builds trust (no forced registration to read about services)

---

## Principle 5 — Speed is Respect

A slow website signals that the company doesn't value the user's time. Costa Blanca Bridge's tech-native positioning makes performance non-negotiable.

**In practice:**
- Target: Lighthouse performance score ≥ 90 on mobile
- Time to First Contentful Paint: < 1.5s
- No render-blocking JavaScript for above-the-fold content
- Images: WebP format, lazy-loaded below the fold, properly sized
- Fonts: use `font-display: swap` to avoid invisible text during load
- No third-party scripts that aren't strictly necessary (analytics, chat, no decorative)

---

## Principle 6 — Mobile is the Primary Canvas

The majority of Costa Blanca Bridge's international audience will first encounter the brand on a mobile device. Every design starts at 375px width and scales up — never the reverse.

**In practice:**
- Single-column layout on mobile is the default — multi-column is an enhancement
- Touch targets: minimum 44px × 44px
- Navigation: hamburger or bottom nav on mobile — no horizontal overflows
- Forms: one question per screen on mobile where possible
- No hover-dependent interactions — all states must be accessible by tap

---

## Principle 7 — The AI-Native Standard

Costa Blanca Bridge builds with AI. The UX must reflect that — not through decorative "AI" language, but through operational excellence: intelligent defaults, predictive content, and frictionless data capture that the AI layer can act on.

**In practice:**
- Intake forms are designed for AI processing — structured fields, not free-text wherever possible
- Every form submission generates a structured object (JSON-compatible) that AI employees can act on immediately
- Language in the UI helps users give Costa Blanca Bridge the right information — guided prompts, not blank fields
- Client portal (future) will show AI-generated progress summaries, not raw status flags
- Never present AI capability as a gimmick — it shows in the speed and quality of response, not in the copy

---

## Anti-Principles (What We Actively Reject)

| ❌ Reject | Reason |
|---|---|
| Dark patterns (forced consent, hidden opt-outs) | Destroys trust in a trust-first business |
| Infinite scroll on service pages | Users need endpoints and decisions |
| Auto-playing video or audio | Disrespectful of context (user may be in an office) |
| Cookie walls that block content | Legally dubious, user-hostile |
| Vanity animations that delay content | Performance and clarity over decoration |
| "Chat with us" bots before meaningful content | Premature. Show value first. |
| Mandatory account creation | Barrier before value is demonstrated |
