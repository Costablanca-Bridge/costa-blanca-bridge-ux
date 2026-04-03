# Legal Pages — Specification

**Version:** 1.0 · April 2026
**Owner:** UX Lead
**Legal review required:** Clara (legal counsel) must review content before publish
**Resolves:** Footer links to `href="#"` for Privacy Policy and Cookie Policy — GDPR exposure

---

## Overview

The website footer currently links to `/privacy-policy` and `/cookie-policy` using `href="#"` — placeholder anchors that go nowhere. Both pages are required before the site can be considered legally compliant under EU GDPR and Spain's LOPDGDD (Ley Orgánica de Protección de Datos y garantía de los derechos digitales).

**These are not design-optional pages. They are legal requirements.**

The coding agent should create the pages using the structure below. The copy marked `[DRAFT]` is a starting scaffold — Clara must review and approve the final text before the site goes live with the contact form active.

---

## Page 01 — Privacy Policy `/privacy-policy`

**Meta title:** Privacy Policy | CostablancaBridge
**Meta description:** How CostablancaBridge collects, uses, and protects your personal data.

### Layout
- Standard page layout: nav + content + footer
- **Background:** Cream (`var(--color-cream)`)
- **Content width:** Max 800px, centred
- **Typography:** Body text `var(--text-base)` Inter, headings `var(--text-heading-3)` Playfair Display

### Required Sections

#### 1. Introduction
```
[DRAFT]
CostablancaBridge SL ("we", "us", "our") is committed to protecting your personal data. 
This Privacy Policy explains what data we collect, why we collect it, how we use it, 
and your rights under the EU General Data Protection Regulation (GDPR) and Spain's 
Ley Orgánica de Protección de Datos y garantía de los derechos digitales (LOPDGDD).

Data controller: [Legal entity name], [Registered address, Spain]
Contact: [DPO email or privacy contact email]
Last updated: [Date]
```

#### 2. What data we collect
```
[DRAFT]
We collect personal data when you:
- Submit the contact form on our website (name, email, phone, company, message)
- Book a discovery call (name, email, calendar data via Calendly)
- Subscribe to our newsletter or waitlist (email)
- Engage with us by email or phone directly

We do not collect sensitive personal data (health, religion, political opinion, etc.).
```

#### 3. How we use your data
```
[DRAFT]
We use your data exclusively to:
- Respond to your enquiry
- Schedule and manage discovery calls
- Send information you have explicitly requested
- Improve our services based on aggregated, anonymised usage patterns

We do not sell your data. We do not share it with third parties except as described below.
```

#### 4. Legal basis for processing
```
[DRAFT]
- Contact form submissions: Consent (Article 6(1)(a) GDPR) — you tick the consent box
- Discovery call bookings: Contract performance (Article 6(1)(b) GDPR)
- Legal obligations: Legal compliance (Article 6(1)(c) GDPR)
```

#### 5. Third-party processors
```
[DRAFT]
We use the following third-party services that may process your data:
- Calendly (USA) — calendar booking. Governed by Calendly's Privacy Policy and SCCs.
- [Email provider] — for sending notifications
- [Hosting provider] — website hosting

All processors are contractually bound to handle your data only on our instructions.
```

#### 6. Data retention
```
[DRAFT]
We retain enquiry data for [X months/years] or until you request deletion.
We delete inactive leads after [X months].
You can request deletion at any time (see Your Rights below).
```

#### 7. Your rights
```
[DRAFT]
Under GDPR, you have the right to:
- Access the personal data we hold about you
- Correct inaccurate data
- Request deletion of your data ("right to be forgotten")
- Object to processing
- Data portability
- Withdraw consent at any time (this does not affect prior processing)

To exercise any right, email: [privacy contact email]
Response time: within 30 days.

You also have the right to lodge a complaint with Spain's data protection authority:
Agencia Española de Protección de Datos (AEPD) — www.aepd.es
```

#### 8. Cookies
```
[DRAFT]
See our Cookie Policy for full details.
We use only [essential / essential + analytics] cookies. 
We do not use advertising or tracking cookies.
```

#### 9. Changes to this policy
```
[DRAFT]
We may update this policy. We will notify you of material changes by updating the 
"Last updated" date at the top of this page. Continued use of the website after 
changes constitutes acceptance of the updated policy.
```

---

## Page 02 — Cookie Policy `/cookie-policy`

**Meta title:** Cookie Policy | CostablancaBridge
**Meta description:** How CostablancaBridge uses cookies and how to control them.

### Required Sections

#### 1. What are cookies
Brief plain-language explanation (2–3 sentences).

#### 2. Cookies we use

| Name | Type | Purpose | Expires |
|---|---|---|---|
| `session_id` | Essential | Maintains your session | Session |
| `csrf_token` | Essential | Security (CSRF protection) | Session |
| `_ga`, `_gid` | Analytics | Google Analytics (if used) | 2 years / 1 day |

**Note:** If Google Analytics is not installed, remove the analytics row. Do not declare cookies you don't use.

#### 3. How to control cookies
```
[DRAFT]
You can control cookies through your browser settings. Disabling essential cookies 
may affect site functionality. Instructions for major browsers:
- Chrome: Settings → Privacy → Cookies
- Firefox: Options → Privacy → Cookies
- Safari: Preferences → Privacy → Cookies
- Edge: Settings → Privacy → Cookies

You can also opt out of Google Analytics at: https://tools.google.com/dlpage/gaoptout
```

#### 4. Changes
Same as Privacy Policy changes section.

---

## Footer Link Implementation

Update the footer HTML to use real URLs (not `href="#"`):

```html
<!-- Before -->
<a href="#">Privacy Policy</a>
<a href="#">Cookie Policy</a>

<!-- After -->
<a href="/privacy-policy">Privacy Policy</a>
<a href="/cookie-policy">Cookie Policy</a>
```

---

## Pre-Launch Checklist (Legal Pages)

- [ ] Clara has reviewed and approved Privacy Policy content
- [ ] Clara has reviewed and approved Cookie Policy content
- [ ] Legal entity name and registered address filled in
- [ ] Privacy contact email filled in and monitored
- [ ] Data retention periods decided and filled in
- [ ] Third-party processors list accurate (match actual integrations)
- [ ] Cookie table matches cookies actually set by the site
- [ ] Both pages live and accessible from the footer before contact form goes live
- [ ] Both pages accessible without JavaScript
- [ ] Both pages pass WCAG 2.1 AA (contrast, headings, structure)

---

## UX Notes

- These pages do not need to be beautiful — they need to be clear, complete, and machine-readable
- Use plain language throughout — no legal jargon without explanation
- One heading level per section — use `<h2>` for sections, `<h3>` for sub-sections
- Table of contents at the top (anchor links) for longer Privacy Policy
- Last updated date must be accurate — update it when content changes
