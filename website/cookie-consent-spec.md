# Cookie Consent Banner — Implementation Spec

**Owner:** Leo Berger (UX Lead)
**Stakeholder:** Clara Blanco (Legal Lead)
**Status:** Spec Complete — Ready for Implementation

---

## 1. Overview

This document specifies the requirements for a cookie consent mechanism (banner) for the Costa Blanca Bridge website (`costablancabridge.com`).

This implementation is a **legal requirement** under GDPR and Spanish ePrivacy law. It is the final blocker preventing the removal of the "DRAFT" notice from the website's legal pages.

## 2. Legal Requirements (from Clara Blanco)

The implementation **must** satisfy the following five criteria to be compliant:

1.  **Load Order:** The consent banner must be the very first thing that loads and must be presented to the user **before** the Google Analytics 4 (GA4) script is loaded and executed.
2.  **Clear Choice:** The banner must provide a clear and unambiguous choice between "Accept" and "Decline" (or similar wording). There should be no "soft accept" or implied consent.
3.  **Opt-In by Default:** GA4 cookies must **not** be set unless the user explicitly clicks "Accept". The default state is no consent.
4.  **Persistence:** The user's choice must be stored and respected on subsequent visits. If they accept, the banner does not reappear. If they decline, the banner does not reappear and GA4 is never loaded.
5.  **Change of Preference:** The user must be able to easily change their consent preference at any time. This should be implemented as a link in the website footer (e.g., "Manage Cookie Consent") that re-opens the banner.

## 3. UX and Design Requirements

### 3.1. Placement and Layout
- The banner should be positioned at the bottom of the screen, full-width.
- It should not cover or obscure navigation elements or the footer content.
- It should be non-modal; the user should be able to browse the page content even with the banner present.

### 3.2. Visual Design
- **Background:** `var(--color-cream)` (`#F5F1EA`)
- **Text:** `var(--color-navy)` (`#0D2340`)
- **Buttons:**
    - **Accept:** Primary button style (`btn-primary`). Text: "Accept".
    - **Decline:** Secondary button style (`btn-secondary`). Text: "Decline".
- The two buttons must have equal visual weight to avoid dark patterns.

### 3.3. Copy
- **Headline:** `This website uses cookies.`
- **Body Text:** `We use cookies to analyse our traffic. By clicking "Accept", you consent to our use of cookies for this purpose. You can change your preference at any time.`
- **Link:** Include a link to the `/cookie-policy` page within the body text.

## 4. Implementation Notes for Engineering

- It is critical that the GA4 script is conditionally loaded based on the user's consent. The consent state should be checked before the `gtag.js` script is even rendered in the `<head>`.
- A simple implementation could use `localStorage` to store the user's consent choice (`'accepted'` or `'declined'`).
- The "Manage Cookie Consent" link in the footer should clear the stored consent state from `localStorage` and reload the page, which would cause the banner to reappear.
- Consider a lightweight, open-source library if a custom implementation is too time-consuming, but ensure it can meet all legal requirements listed above.

---

This spec is now ready for implementation by the engineering team.
