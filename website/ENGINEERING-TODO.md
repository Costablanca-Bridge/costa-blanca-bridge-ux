# Engineering TODO — Website Issues

**Created:** April 2026
**Raised by:** Leo Berger, UX Lead
**Priority order:** P0 (blocking CEO priority) → P1 (legal/accessibility) → P2 (quality)

Pick these up in order. Each item links to a spec file for full implementation detail.

---

## P0 — Contact Form (CEO Priority #4)

**Status:** Spec written — awaiting implementation
**Spec:** `website/contact-form-spec.md`

The website has no working contact form. The closing CTA "Book a Discovery Call" links to a `mailto:` address. This does not meet the CEO's stated priority of "website live with a working contact form."

**Tasks:**
- [ ] Create `/contact` page with Calendly embed (left 60%) + contact form (right 40%)
- [ ] Implement the contact form HTML per `website/contact-form-spec.md`
- [ ] Add form CSS to `website/css/styles.css` per spec
- [ ] Implement `POST /api/contact` endpoint with server-side validation
- [ ] Endpoint returns structured JSON for AI intake workflow
- [ ] Endpoint sends email notification to `armando.ramirez.vila@gmail.com` on submission
- [ ] Update homepage Section 8 closing CTA: `mailto:` → `/contact`
- [ ] Update homepage secondary CTA "Send us a message": `mailto:` → `/contact`
- [ ] Form is fully accessible per the checklist in the spec
- [ ] GDPR consent checkbox is present, required, not pre-ticked
- [ ] Test: form submits, success state shown, email notification received
- [ ] Test: validation fires on empty required fields
- [ ] Test: server-side validation catches direct POST bypass

---

## P1a — Legal Pages (GDPR compliance)

**Status:** Spec written — content requires Clara's legal review
**Spec:** `website/legal-pages-spec.md`

Footer links to `/privacy-policy` and `/cookie-policy` go to `href="#"` — broken placeholders. With GDPR active in Spain and a contact form collecting personal data, these pages must exist before the form goes live.

**Tasks:**
- [ ] Create `/privacy-policy` page using structure in `website/legal-pages-spec.md`
- [ ] Create `/cookie-policy` page using structure in `website/legal-pages-spec.md`
- [ ] **Block deploy until Clara has reviewed and approved the copy** (marked `[DRAFT]` in spec)
- [ ] Update footer links: `href="#"` → `/privacy-policy` and `/cookie-policy`
- [ ] Contact form GDPR consent link points to `/privacy-policy` (live, not `#`)

**Note:** Do not go live with the contact form until both legal pages are published with Clara's approval.

---

## P1b — Skip Navigation Link (WCAG 2.4.1 — Level A)

**Status:** Spec written — awaiting implementation
**Spec:** `website/accessibility-spec.md`

No skip-to-content mechanism exists on any page. This is a WCAG 2.4.1 Level A failure — the most fundamental accessibility requirement. Keyboard users cannot bypass the navigation bar.

**Tasks:**
- [ ] Add `<a href="#main-content" class="skip-link">Skip to main content</a>` as first element inside `<body>` on every page (or in the shared layout/template)
- [ ] Add `id="main-content"` to the `<main>` element on every page
- [ ] Add skip link CSS from `website/accessibility-spec.md` to `website/css/styles.css`
- [ ] Test: press Tab on page load — skip link must appear; pressing Enter must move focus to `<main>`
- [ ] Verify skip link is present on all pages (homepage, services, about, contact, etc.)

---

## P2a — Gold Colour Token Fix

**Status:** Spec written — awaiting implementation
**Spec:** `brand/design-token-fix.md`

Website CSS uses `#C4965A` (incorrect). Brand source of truth is `#C8973A`. 

**Tasks:**
- [ ] Update `--color-gold` in `website/css/styles.css` to `#C8973A`
- [ ] Update `--color-gold-light` to `#E8C46A`
- [ ] Update all gold RGBA opacity variants to use `rgb(200, 151, 58)` base
- [ ] Remove `--color-gold-12` (non-standard); replace any usages with `--color-gold-10`
- [ ] Visual regression check: all gold elements look correct after change
- [ ] Contrast check: CTA buttons, stat numbers, section labels still pass 4.5:1

---

## P2b — Homepage Duplicate Stats

**Status:** No spec needed — straightforward content fix

The stats `€40B FDI into Spain in 2024` and `450M+ EU consumers via Spain` appear twice on the homepage:
1. In the hero stat strip (Section 2, below the main CTA)
2. In the Spain Advantage stats band (Section 6, gold background)

**Tasks:**
- [ ] Remove the stat strip from Section 2 (the hero)
- [ ] Keep the full stats in Section 6 (the gold stats band) — this is the proper home for them
- [ ] The hero should end cleanly with the CTA buttons — no stat strip below

---

## Deployment Order

Implement in this order to avoid shipping a broken or non-compliant site:

```
1. Skip nav link (P1b) — quick fix, no dependencies
2. Gold token fix (P2a) — quick fix, no dependencies
3. Duplicate stats removal (P2b) — quick fix, no dependencies
4. Legal pages (P1a) — structure only; wait for Clara's copy approval before deploy
5. Contact form (P0) — implement fully; do NOT deploy until legal pages are live
```

Items 1–3 can deploy immediately. Items 4–5 are gated on legal review.

---

## Questions for Engineering

- What is the backend stack? The contact form spec assumes `POST /api/contact` — confirm the API route convention.
- Is Calendly already configured? If not, the embed will need an account and a booking page set up.
- Where do email notifications route? Confirm `armando.ramirez.vila@gmail.com` is the correct intake address.
- Is there a shared layout/template file where the skip nav and `<main id="main-content">` can be added once?

Raise any blockers → Leo Berger (UX Lead).
