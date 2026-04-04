# CostablancaBridge — UX & Design System

**Version:** 1.0 · April 2026
**Owner:** UX Lead (AI Employee)
**Last updated by:** Armando Ramirez Vila, CEO

---

## How This Folder Works

This folder is the single source of truth for CostablancaBridge's visual identity, user experience, and website design. It is used by all AI employees and the coding agent to ensure every touchpoint is consistent, intentional, and aligned with the brand.

**Who uses this:**
- **UX Lead** — maintains and evolves personas, journeys, and design system
- **Marketing Lead** — pulls tone-of-voice, key messages, and visual identity for campaigns
- **Engineering Lead / Coding Agent** — reads design tokens, page specs, and component guidelines to build and update the website
- **CEO (Armando)** — reviews and approves strategic changes to brand direction

---

## Folder Structure

```
ux/
├── README.md                   ← You are here
├── brand/
│   ├── brand-guidelines.md     ← Colors, typography, logo, voice & tone
│   ├── design-tokens.css       ← CSS custom properties (copy directly into codebase)
│   └── design-tokens.json      ← Design tokens in JSON (for Figma/tooling)
├── ux/
│   ├── ux-principles.md        ← 7 design principles that govern all decisions
│   ├── personas.md             ← 4 primary user personas with goals & pain points
│   └── user-journeys.md        ← Key journeys per persona from discovery to conversion
├── website/
│   ├── website-brief.md        ← Goals, audience, KPIs, constraints
│   ├── sitemap.md              ← Full site structure and navigation
│   └── page-specs.md           ← Page-by-page content and layout specifications
├── components/
│   └── component-library.md    ← Design patterns, UI components, and usage rules
└── concept/
    └── homepage-concept.html   ← Working visual prototype (open in browser)
```

---

## The Brand in One Paragraph

CostablancaBridge is a professional-grade, trust-first brand. Navy blue conveys authority and stability. Gold signals premium quality and cross-cultural connection. Cream provides warmth and approachability. The visual language is editorial — bold serif headlines, clean sans-serif body text, generous whitespace. The brand says: "We have done this before, at the highest level, and we will walk through it with you."

---

## Quick Reference: Core Brand Values

| Token | Value |
|---|---|
| Primary colour | `#1B3A6B` (Navy) |
| Accent colour | `#C8973A` (Gold) |
| Background | `#F4F1EB` (Cream) |
| Heading font | `'Playfair Display', Cambria, Georgia, serif` |
| Body font | `'Inter', Calibri, 'Segoe UI', system-ui, sans-serif` |
| Tagline | *Connecting Worlds. Powering Prosperity.* |
| Website | costablancabridge.com |

---

## For the Coding Agent

Start here:
1. Read `brand/design-tokens.css` — import directly as your CSS variables
2. Read `website/page-specs.md` — the full content and layout spec for every page
3. Read `components/component-library.md` — the component system to build from
4. Use `concept/homepage-concept.html` as the visual reference for the homepage

The website should be **mobile-first**, **fast** (no unnecessary dependencies), and **conversion-focused**. Target metric: a prospect arriving from LinkedIn or Google should understand what Costa Blanca Bridge does and want to book a call within 60 seconds.
