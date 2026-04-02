# CostablancaBridge — Website Brief

**Version:** 1.0 · April 2026
**Owner:** CEO + UX Lead
**For:** Engineering Lead / Coding Agent

---

## 1. What the Website Must Do

The website is CBB's primary sales and trust-building asset. It must:

1. **Establish credibility instantly** — a prospect arriving cold must understand who CBB is, what they do, and why they are different within 10 seconds
2. **Reflect all four personas** — James, Sofia, Mohammed, and Erik must each see their situation reflected within the first scroll of the homepage
3. **Explain the Principal Model** — the co-investment angle is the key differentiator; it must have a dedicated, clear page
4. **Drive one action: book a discovery call** — every page ends with this CTA, with no competing actions
5. **Support AI employees** — the intake form generates structured data that AI employees can process immediately

---

## 2. Target Conversion Metric

**Primary:** Prospect books a discovery call or submits an enquiry form
**Secondary:** Prospect subscribes to market intelligence updates (newsletter)
**Target:** 3–5% conversion rate on first visit for qualified traffic

---

## 3. Technical Requirements

| Requirement | Specification |
|---|---|
| Stack | Static HTML/CSS/JS for MVP (no framework dependency); Next.js or Astro for v2 |
| Hosting | Vercel, Netlify, or Cloudflare Pages |
| Performance | Lighthouse score ≥ 90 (mobile), ≥ 95 (desktop) |
| Accessibility | WCAG 2.1 AA minimum |
| SEO | Server-side rendered or static; proper semantic HTML, meta tags, structured data |
| Analytics | Google Analytics 4 + Google Search Console |
| Forms | Formspree or custom API endpoint; structured JSON output |
| Fonts | Google Fonts (Playfair Display + Inter) with `font-display: swap` |
| Images | WebP format, lazy loading, properly sized srcsets |
| Mobile-first | Designed and coded at 375px, enhanced upward |
| GDPR | Cookie consent (minimal — analytics only), privacy policy |
| Domain | costablancabridge.com (already registered) |

---

## 4. Content Languages

**Phase 1 (MVP):** English only
**Phase 2:** Spanish (es), Dutch (nl), Swedish (sv) — defer until Phase 2

---

## 5. Tone of Voice on the Website

Refer to `brand/brand-guidelines.md` Section 7 for full voice guidance. Summary:
- Confident partner, not enthusiastic vendor
- Precise sentences, no filler
- First person plural ("we", "our") — not corporate third person ("CostablancaBridge provides...")
- Use real examples and numbers wherever possible
- CTAs are conversational: "Book a Discovery Call", "Explore Our Services", "Let's Talk"

---

## 6. SEO Priority Keywords (Phase 1)

| Intent | Keyword | Target Page |
|---|---|---|
| UK company Spain setup | "set up company in Spain UK" | LAND service page |
| Post-Brexit EU presence | "Spanish subsidiary post Brexit" | LAND service page |
| Digital nomad visa Spain | "digital nomad visa Spain" | PEOPLE / Relocation page |
| Costa Blanca relocation | "retire Costa Blanca legal advice" | PEOPLE / Relocation page |
| EU market entry | "EU market entry Spain" | Homepage / How We Work |
| Import to EU from emerging markets | "import to EU from Morocco" / "import to EU from Latin America" | TRADE page |
| Spain company formation | "company formation Spain" | LAND page |
| Non lucrative visa Spain | "non lucrative visa Spain cost" | PEOPLE page |

---

## 7. Integrations (Phase 1 MVP)

| Integration | Purpose | Tool |
|---|---|---|
| Booking | Discovery call booking | Calendly (embed) |
| Contact form | Enquiry intake | Formspree or custom |
| Email newsletter | Lead nurture | Mailchimp or ConvertKit |
| Analytics | Traffic and conversion tracking | Google Analytics 4 |
| Cookie consent | GDPR compliance | Minimal custom or CookieYes |

---

## 8. Out of Scope for MVP

- Client portal / login area
- Live chat or chatbot
- Payment processing
- Multi-language
- Blog CMS (Phase 1 blog pages are static HTML)
- Interactive deal calculator
- Job board / careers section
