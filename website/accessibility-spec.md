# Accessibility Specification

**Version:** 1.0 · April 2026
**Owner:** UX Lead
**Standard:** WCAG 2.1 Level AA — mandatory, no exceptions
**Resolves:** Missing skip-navigation link on current website

---

## Principle

Accessibility at CostablancaBridge is not a feature. It is a baseline. Every page, every component, every release must meet WCAG 2.1 AA before it is considered done. This is a legal requirement in Spain (Real Decreto Legislativo 1/2013 applies to public-facing digital services) and a reputational baseline for a company operating at the institutional level.

No deadline, no resource constraint, and no design preference overrides this.

---

## Skip Navigation Link

### Problem
The current website has no skip-to-content mechanism. Keyboard users and screen reader users must tab through the entire navigation bar on every page load before reaching the page content. This fails WCAG 2.4.1 (Bypass Blocks, Level A — the most basic accessibility requirement).

### Required Fix

Add a skip link as the **very first element inside `<body>`** on every page:

```html
<body>
  <!-- Skip navigation — MUST be first element in <body> -->
  <a href="#main-content" class="skip-link">Skip to main content</a>

  <nav>...</nav>

  <main id="main-content" tabindex="-1">
    <!-- All page content here -->
  </main>
</body>
```

### Skip Link CSS

The skip link is visually hidden until focused. It must be reachable by pressing Tab as the very first keyboard action on the page.

```css
/* ── Skip Navigation ─────────────────────────────── */
.skip-link {
  position: absolute;
  top: -100%;
  left: var(--space-4);
  z-index: 9999;
  padding: var(--space-3) var(--space-6);
  background-color: var(--color-gold);
  color: var(--color-navy-dark);
  font-family: var(--font-body);
  font-size: var(--text-base);
  font-weight: var(--font-semibold);
  text-decoration: none;
  border-radius: var(--radius-sm);
  border: 2px solid var(--color-navy-dark);
  transition: top var(--transition-fast);
}

.skip-link:focus {
  top: var(--space-4);  /* Slide into view when focused */
}

.skip-link:focus-visible {
  outline: 3px solid var(--color-navy-dark);
  outline-offset: 2px;
}
```

**Why gold background:** Maximum contrast against navy text (ratio ≈ 7:1, exceeds AA). The skip link must itself be accessible.

---

## Global Accessibility Rules

These apply to every page and component. The coding agent must not ship code that violates any of these.

### 1. Focus Management

```css
/* NEVER do this: */
*:focus { outline: none; }
button:focus { outline: none; }

/* DO this instead — visible, on-brand focus ring: */
:focus-visible {
  outline: 3px solid var(--color-gold);
  outline-offset: 2px;
}
```

Suppressing focus outlines is a WCAG 2.4.7 failure. It renders the site unusable for keyboard users.

### 2. Colour Contrast Minimums

| Context | Minimum ratio | Target |
|---|---|---|
| Body text (< 18px) | 4.5:1 | 7:1 |
| Large text (≥ 18px or 14px bold) | 3:1 | 4.5:1 |
| UI components (borders, icons) | 3:1 | 4.5:1 |

**Pre-approved combinations from the brand palette:**

| Text | Background | Ratio | Status |
|---|---|---|---|
| `#1A1A2E` (near-black) | `#F4F1EB` (cream) | 14.2:1 | ✅ Pass |
| `#FFFFFF` (white) | `#0D2340` (navy-dark) | 16.3:1 | ✅ Pass |
| `#FFFFFF` (white) | `#1B3A6B` (navy) | 10.5:1 | ✅ Pass |
| `#C8973A` (gold) | `#0D2340` (navy-dark) | 6.9:1 | ✅ Pass (large text) |
| `#C8973A` (gold) | `#FFFFFF` (white) | 2.8:1 | ❌ Fail — do not use gold text on white |
| `#8BA8C8` (blue-gray) | `#0D2340` (navy-dark) | 5.2:1 | ✅ Pass |
| `#64748B` (mid-gray) | `#F4F1EB` (cream) | 4.6:1 | ✅ Pass (just) |
| `#64748B` (mid-gray) | `#FFFFFF` (white) | 4.5:1 | ✅ Pass (borderline — avoid for small text) |

**Do not use gold text (`#C8973A`) on white or cream backgrounds for body text.** Gold is approved only as an accent colour, for large display text, and on dark (navy-dark) backgrounds.

### 3. Interactive Elements

- **Minimum touch target:** 44×44px for all clickable/tappable elements (WCAG 2.5.5)
- **Links vs buttons:** Use `<a>` for navigation, `<button>` for actions. Do not use `<div>` or `<span>` as interactive elements.
- **Hover-only states:** All hover interactions must also be keyboard-accessible (`:focus` mirrors `:hover`)
- **External links:** Add `target="_blank" rel="noopener noreferrer"` and visually indicate they open in a new tab (icon or "(opens in new tab)" text for screen readers)

### 4. Semantic HTML

```html
<!-- Required landmark structure on every page -->
<header role="banner">...</header>
<nav aria-label="Main navigation">...</nav>
<main id="main-content">...</main>
<footer role="contentinfo">...</footer>

<!-- Section headings: one <h1> per page, logical hierarchy -->
<h1>Page title</h1>
  <h2>Section heading</h2>
    <h3>Sub-section</h3>

<!-- Never skip heading levels (h1 → h3 with no h2) -->
```

### 5. Images

```html
<!-- Decorative images: empty alt attribute -->
<img src="decoration.png" alt="" role="presentation" />

<!-- Informative images: descriptive alt text -->
<img src="costa-blanca-aerial.jpg" alt="Aerial view of the Costa Blanca coastline, Spain" />

<!-- Logo: specific alt text -->
<img src="logo.png" alt="CostablancaBridge" />

<!-- Never: alt text that repeats adjacent text or says "image of" -->
```

### 6. Forms

Full form accessibility spec is in `website/contact-form-spec.md`. Summary:
- Every input has an associated `<label>` (not placeholder-only)
- Required fields marked with `aria-required="true"` and visual indicator
- Errors surfaced with `role="alert"` and linked via `aria-describedby`
- No time limits on form completion

### 7. Motion & Animation

```css
/* Respect user preference for reduced motion — always */
@media (prefers-reduced-motion: reduce) {
  *,
  *::before,
  *::after {
    animation-duration: 0.01ms !important;
    animation-iteration-count: 1 !important;
    transition-duration: 0.01ms !important;
    scroll-behavior: auto !important;
  }
}
```

### 8. Page Language

```html
<html lang="en">
```

For future Spanish-language pages: `<html lang="es">`. Never leave `lang` unset.

---

## Current Website — Known Issues

| Issue | WCAG criterion | Severity | Status |
|---|---|---|---|
| No skip-to-content link | 2.4.1 Bypass Blocks (A) | Critical | ⏳ Spec written — awaiting fix |
| Contact CTA uses `mailto:` not a form | UX/conversion issue | Critical | ⏳ Spec written — `contact-form-spec.md` |
| Footer links to `href="#"` (Privacy/Cookie) | Not WCAG, but legal | Critical | ⏳ Spec written — `legal-pages-spec.md` |
| Gold token mismatch (`#C4965A` vs `#C8973A`) | Design system integrity | Medium | ⏳ Spec written — `design-token-fix.md` |

---

## Accessibility Testing Checklist

Run before every release:

### Automated
- [ ] Run axe DevTools (browser extension) — target: zero violations
- [ ] Run Lighthouse accessibility audit — target: score ≥ 95
- [ ] Check colour contrast with Colour Contrast Analyser for custom combinations

### Manual
- [ ] Tab through the entire page without a mouse — every interactive element reachable
- [ ] Skip link appears and works on first Tab press
- [ ] Screen reader test with VoiceOver (Mac) or NVDA (Windows) — headings, landmarks, form labels
- [ ] Zoom to 200% — no content hidden, no horizontal scroll on mobile-width viewport
- [ ] Test with `prefers-reduced-motion` enabled — no animations
- [ ] Test with `prefers-color-scheme: dark` — if not supported, ensure not broken

---

## Monthly Audit Schedule

The UX Lead runs a focused accessibility audit on one key page per month and logs findings in Google Drive → `UX & Engineering/Proposals/`. Any WCAG 2.1 AA failure is escalated to Armando immediately — it is treated as a production bug, not a backlog item.
