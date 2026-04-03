# Contact Form — Component & Page Specification

**Version:** 1.0 · April 2026
**Owner:** UX Lead
**Depends on:** `brand/design-tokens.css`, `components/component-library.md`
**Resolves:** CEO Priority #4 — "website live with a working contact form"

---

## Overview

The current website uses a `mailto:` link in the closing CTA section instead of a contact form. This does not meet the CEO's stated priority. This spec defines the complete contact form component and the `/contact` page layout.

The form must:
- Capture structured lead data for AI employee intake workflow
- Be fully accessible (WCAG 2.1 AA)
- Work without JavaScript on submit (progressive enhancement)
- Be GDPR-compliant (Spain / EU law)

---

## Page: `/contact`

**Meta title:** Talk to Us — CostablancaBridge
**Meta description:** Book a discovery call or send us a message. We respond within one business day.
**Primary CTA:** Book a Discovery Call (via Calendly embed)

### Layout

```
┌─────────────────────────────────────────────────────┐
│  NAV                                                  │
├──────────────────────────┬──────────────────────────┤
│                          │                           │
│  Calendly embed (60%)    │  Contact form (40%)       │
│                          │                           │
│  "Book a call directly"  │  "Or send us a message"   │
│                          │                           │
└──────────────────────────┴──────────────────────────┘
│  Footer                                               │
└─────────────────────────────────────────────────────┘
```

**Mobile:** Stack vertically — form first, then Calendly embed below.

### Section: Hero (compact)
- **Background:** Navy dark (`var(--color-navy-dark)`)
- **Heading:** `Let's Talk.`
- **Sub:** `Book a call directly, or send us a message and we'll respond within one business day.`
- No CTA button — page is the CTA.

---

## Contact Form Component

### Fields (in order)

| Field | Type | Required | Placeholder / Label |
|---|---|---|---|
| Full name | `text` | Yes | Full name |
| Email | `email` | Yes | Email address |
| Phone | `tel` | No | Phone number (optional) |
| Company | `text` | No | Company name (optional) |
| Service interest | `select` | Yes | What are you interested in? |
| Message | `textarea` | Yes | Tell us briefly what you need |
| How did you hear about us? | `select` | No | How did you find us? |
| GDPR consent | `checkbox` | Yes | *(see GDPR section below)* |

### Service interest options (select)
```
-- Select a service --
Company formation / Market entry (LAND)
Business operations / Compliance (OPERATE)
Cross-border trade / Investment (TRADE)
Relocation / Visa / Workforce (PEOPLE)
Not sure yet — I need to talk it through
```

### How did you find us? options (select)
```
-- Optional --
Google search
LinkedIn
Referral from a contact
Social media
Event or conference
Other
```

### Form HTML (reference implementation)

```html
<form
  id="contact-form"
  action="/api/contact"
  method="POST"
  novalidate
  aria-label="Contact form"
>
  <div class="form-group">
    <label for="name">Full name <span aria-hidden="true">*</span></label>
    <input
      type="text"
      id="name"
      name="name"
      required
      autocomplete="name"
      aria-required="true"
      aria-describedby="name-error"
    />
    <span id="name-error" class="form-error" role="alert" aria-live="polite"></span>
  </div>

  <div class="form-group">
    <label for="email">Email address <span aria-hidden="true">*</span></label>
    <input
      type="email"
      id="email"
      name="email"
      required
      autocomplete="email"
      aria-required="true"
      aria-describedby="email-error"
    />
    <span id="email-error" class="form-error" role="alert" aria-live="polite"></span>
  </div>

  <div class="form-group">
    <label for="phone">Phone number <span class="form-optional">(optional)</span></label>
    <input
      type="tel"
      id="phone"
      name="phone"
      autocomplete="tel"
    />
  </div>

  <div class="form-group">
    <label for="company">Company <span class="form-optional">(optional)</span></label>
    <input
      type="text"
      id="company"
      name="company"
      autocomplete="organization"
    />
  </div>

  <div class="form-group">
    <label for="service">What are you interested in? <span aria-hidden="true">*</span></label>
    <select
      id="service"
      name="service"
      required
      aria-required="true"
      aria-describedby="service-error"
    >
      <option value="">-- Select a service --</option>
      <option value="land">Company formation / Market entry (LAND)</option>
      <option value="operate">Business operations / Compliance (OPERATE)</option>
      <option value="trade">Cross-border trade / Investment (TRADE)</option>
      <option value="people">Relocation / Visa / Workforce (PEOPLE)</option>
      <option value="general">Not sure yet — I need to talk it through</option>
    </select>
    <span id="service-error" class="form-error" role="alert" aria-live="polite"></span>
  </div>

  <div class="form-group">
    <label for="message">Message <span aria-hidden="true">*</span></label>
    <textarea
      id="message"
      name="message"
      rows="5"
      required
      aria-required="true"
      aria-describedby="message-hint message-error"
      placeholder="Tell us briefly what you need"
    ></textarea>
    <span id="message-hint" class="form-hint">
      No confidential details needed at this stage — just a brief summary.
    </span>
    <span id="message-error" class="form-error" role="alert" aria-live="polite"></span>
  </div>

  <div class="form-group">
    <label for="source">How did you find us? <span class="form-optional">(optional)</span></label>
    <select id="source" name="source">
      <option value="">-- Optional --</option>
      <option value="google">Google search</option>
      <option value="linkedin">LinkedIn</option>
      <option value="referral">Referral from a contact</option>
      <option value="social">Social media</option>
      <option value="event">Event or conference</option>
      <option value="other">Other</option>
    </select>
  </div>

  <!-- GDPR consent — required -->
  <div class="form-group form-group--checkbox">
    <input
      type="checkbox"
      id="gdpr-consent"
      name="gdpr_consent"
      required
      aria-required="true"
      aria-describedby="gdpr-error"
    />
    <label for="gdpr-consent">
      I consent to CostablancaBridge storing and processing my data to respond to
      my enquiry, in accordance with the
      <a href="/privacy-policy" target="_blank" rel="noopener">Privacy Policy</a>.
      <span aria-hidden="true">*</span>
    </label>
    <span id="gdpr-error" class="form-error" role="alert" aria-live="polite"></span>
  </div>

  <button type="submit" class="btn-primary">Send message</button>

  <!-- Success / error state (hidden by default, shown via JS or server redirect) -->
  <div
    id="form-success"
    class="form-feedback form-feedback--success"
    role="alert"
    aria-live="polite"
    hidden
  >
    <strong>Message sent.</strong> We'll respond within one business day.
  </div>
  <div
    id="form-error-global"
    class="form-feedback form-feedback--error"
    role="alert"
    aria-live="assertive"
    hidden
  >
    <strong>Something went wrong.</strong> Please try again, or email us directly at
    <a href="mailto:armando.ramirez.vila@gmail.com">armando.ramirez.vila@gmail.com</a>.
  </div>

</form>
```

---

## Form Styles

Add to `website/css/styles.css`:

```css
/* ── Contact Form ─────────────────────────────────── */

.form-group {
  display: flex;
  flex-direction: column;
  gap: var(--space-1);
  margin-bottom: var(--space-6);
}

.form-group label {
  font-family: var(--font-body);
  font-size: var(--text-sm);
  font-weight: var(--font-semibold);
  color: var(--color-navy);
}

.form-group input,
.form-group select,
.form-group textarea {
  font-family: var(--font-body);
  font-size: var(--text-base);
  color: var(--color-near-black);
  background-color: var(--color-white);
  border: 1.5px solid var(--color-warm-gray);
  border-radius: var(--radius-sm);
  padding: var(--space-3) var(--space-4);
  transition: border-color var(--transition-base), box-shadow var(--transition-base);
  width: 100%;
  box-sizing: border-box;
}

.form-group input:focus,
.form-group select:focus,
.form-group textarea:focus {
  outline: none;
  border-color: var(--color-navy);
  box-shadow: 0 0 0 3px var(--color-navy-10);
}

/* Visible focus ring — never suppress focus outlines */
.form-group input:focus-visible,
.form-group select:focus-visible,
.form-group textarea:focus-visible {
  outline: 3px solid var(--color-gold);
  outline-offset: 2px;
}

.form-group textarea {
  resize: vertical;
  min-height: 120px;
}

.form-hint {
  font-size: var(--text-sm);
  color: var(--color-mid-gray);
}

.form-optional {
  font-size: var(--text-sm);
  font-weight: var(--font-normal);
  color: var(--color-mid-gray);
}

.form-error {
  font-size: var(--text-sm);
  color: #C0392B; /* semantic error red — not in palette, intentional */
  display: none;
}
.form-error:not(:empty) { display: block; }

/* Invalid state (set via JS after user interaction) */
.form-group input[aria-invalid="true"],
.form-group select[aria-invalid="true"],
.form-group textarea[aria-invalid="true"] {
  border-color: #C0392B;
}

/* Checkbox group */
.form-group--checkbox {
  flex-direction: row;
  align-items: flex-start;
  gap: var(--space-3);
}
.form-group--checkbox input[type="checkbox"] {
  width: 20px;
  height: 20px;
  min-width: 20px;
  flex-shrink: 0;
  margin-top: 2px;
  accent-color: var(--color-navy);
  cursor: pointer;
}
.form-group--checkbox label {
  font-weight: var(--font-normal);
  color: var(--color-near-black);
  font-size: var(--text-sm);
  cursor: pointer;
}

/* Feedback states */
.form-feedback {
  padding: var(--space-4);
  border-radius: var(--radius-sm);
  font-size: var(--text-base);
  margin-top: var(--space-4);
}
.form-feedback--success {
  background-color: #D4EDDA;
  color: #155724;
  border: 1px solid #C3E6CB;
}
.form-feedback--error {
  background-color: #F8D7DA;
  color: #721C24;
  border: 1px solid #F5C6CB;
}
```

---

## Form Submission & Backend

The form submits to `POST /api/contact`. The endpoint must:

1. Validate all required fields server-side (never trust client-only validation)
2. Return structured JSON to the AI employee intake workflow:

```json
{
  "source": "website-contact-form",
  "timestamp": "2026-04-03T19:00:00Z",
  "lead": {
    "name": "...",
    "email": "...",
    "phone": "...",
    "company": "...",
    "service_interest": "land|operate|trade|people|general",
    "message": "...",
    "referral_source": "google|linkedin|referral|social|event|other|null",
    "gdpr_consent": true
  }
}
```

3. On success: return HTTP 200 + `{ "ok": true }` — JS shows `#form-success`, or redirect to `/contact?sent=1`
4. On validation error: return HTTP 422 + field errors — JS surfaces per-field messages
5. On server error: return HTTP 500 — JS shows `#form-error-global`

**Email notification:** Send plain-text email to `armando.ramirez.vila@gmail.com` with the structured lead data on every submission.

---

## Updating the Homepage Closing CTA

The homepage Section 8 "Closing CTA" currently has a "Book a Discovery Call" button linking to `mailto:`. Update it:

```html
<!-- Before -->
<a href="mailto:armando.ramirez.vila@gmail.com" class="btn-primary">Book a Discovery Call</a>

<!-- After -->
<a href="/contact" class="btn-primary">Book a Discovery Call</a>
```

The secondary "Send us a message" CTA also links to `/contact`:
```html
<a href="/contact" class="btn-secondary">Send us a message</a>
```

---

## GDPR Notes

This form collects personal data from EU residents. Required at minimum:

- Explicit, unbundled consent checkbox (above — do not pre-tick)
- Link to Privacy Policy in consent copy
- Data is used only for responding to the enquiry (state this in the Privacy Policy)
- Do not retain leads who have not consented
- Right to erasure: include contact info for data deletion requests in Privacy Policy

See also: `website/legal-pages-spec.md` for Privacy Policy page spec.

---

## Accessibility Checklist

- [ ] All inputs have associated `<label>` elements (not placeholder-only)
- [ ] Required fields indicated visually and via `aria-required="true"`
- [ ] Error messages linked to inputs via `aria-describedby`
- [ ] Error messages use `role="alert"` and `aria-live`
- [ ] Form success message uses `role="alert"`
- [ ] Focus ring is visible and not suppressed (see CSS above)
- [ ] Checkbox touch target ≥ 44×44px
- [ ] Submit button is a `<button type="submit">`, not an `<input type="submit">` or `<div>`
- [ ] No colour-only error indication — use icon + text + border colour together
