# CostablancaBridge — Component Library

**Version:** 1.0 · April 2026
**For:** Engineering Lead / Coding Agent
**Depends on:** `brand/design-tokens.css`

All components use CSS custom properties from the design tokens file. No hardcoded colour values anywhere in the codebase.

---

## Buttons

### Primary CTA Button
```html
<a href="/contact" class="btn-primary">Book a Discovery Call</a>
```
```css
.btn-primary {
  display: inline-flex;
  align-items: center;
  gap: var(--space-2);
  background-color: var(--color-gold);
  color: var(--color-navy-dark);
  font-family: var(--font-body);
  font-size: var(--text-base);
  font-weight: var(--font-semibold);
  padding: var(--space-4) var(--space-8);
  border-radius: var(--radius-sm);
  text-decoration: none;
  border: 2px solid transparent;
  transition: background-color var(--transition-base), transform var(--transition-fast);
  white-space: nowrap;
}
.btn-primary:hover {
  background-color: var(--color-gold-light);
  transform: translateY(-1px);
}
.btn-primary:active { transform: translateY(0); }
```

### Secondary Button (outline on dark bg)
```css
.btn-secondary {
  /* same as btn-primary but: */
  background-color: transparent;
  color: var(--color-white);
  border: 2px solid var(--color-white);
}
.btn-secondary:hover {
  background-color: var(--color-white-10);
}
```

### Ghost Button (outline on light bg)
```css
.btn-ghost {
  background-color: transparent;
  color: var(--color-navy);
  border: 2px solid var(--color-navy);
}
.btn-ghost:hover {
  background-color: var(--color-navy-10);
}
```

**Button sizes:**
- Default: `padding: 14px 32px`, `font-size: 16px`
- Large: `padding: 18px 40px`, `font-size: 18px`
- Small: `padding: 10px 20px`, `font-size: 14px`

---

## Section Label

Small gold all-caps label above section headings.
```html
<span class="section-label">WHO WE SERVE</span>
```
```css
.section-label {
  display: block;
  font-family: var(--font-body);
  font-size: var(--text-xs);
  font-weight: var(--font-semibold);
  letter-spacing: var(--tracking-widest);
  text-transform: uppercase;
  color: var(--color-gold);
  margin-bottom: var(--space-3);
}
```
On dark backgrounds: `color: var(--color-gold)` (same).
On cream/white: `color: var(--color-gold)` (same — gold works on all backgrounds).

---

## Gold Rule / Divider

The signature gold accent line that appears under hero headlines.
```html
<span class="gold-rule" aria-hidden="true"></span>
```
```css
.gold-rule {
  display: block;
  width: 64px;
  height: 3px;
  background-color: var(--color-gold);
  margin: var(--space-4) 0 var(--space-6);
}
```

---

## Typography Components

### Display Headline (Hero)
```html
<h1 class="display-hero">
  Connecting Worlds.<br>
  <em>Powering Prosperity.</em>
</h1>
```
```css
.display-hero {
  font-family: var(--font-display);
  font-size: clamp(2.5rem, 6vw, var(--text-7xl)); /* 40px → 72px */
  font-weight: var(--font-bold);
  line-height: var(--leading-tight);
  letter-spacing: var(--tracking-tight);
  color: var(--color-white);
}
.display-hero em {
  font-style: italic;
  color: var(--color-gold);
}
```

### Section Heading (H2)
```css
.section-heading {
  font-family: var(--font-display);
  font-size: clamp(1.75rem, 3vw, var(--text-5xl)); /* 28px → 48px */
  font-weight: var(--font-bold);
  line-height: var(--leading-snug);
  color: var(--color-navy); /* or --color-white on dark */
}
```

### Body Lead
```css
.body-lead {
  font-family: var(--font-body);
  font-size: var(--text-lg);
  line-height: var(--leading-relaxed);
  color: var(--text-secondary);
  max-width: 65ch;
}
```

---

## Cards

### Service Pipeline Card (light bg)
```html
<div class="card-service">
  <div class="card-service__number">01</div>
  <h3 class="card-service__title">LAND</h3>
  <p class="card-service__subtitle">Market Entry</p>
  <span class="gold-rule"></span>
  <ul class="card-service__list">
    <li>Company formation</li>
    <li>Visa processing</li>
    <li>Banking setup</li>
  </ul>
  <a href="/services/land" class="card-service__link">Explore →</a>
</div>
```
```css
.card-service {
  background: var(--color-white);
  border: 1px solid var(--border-light);
  border-top: 4px solid var(--color-gold);
  border-radius: var(--radius-lg);
  padding: var(--space-8);
  display: flex;
  flex-direction: column;
  gap: var(--space-2);
  box-shadow: var(--shadow-sm);
  transition: transform var(--transition-base), box-shadow var(--transition-base);
}
.card-service:hover {
  transform: translateY(-4px);
  box-shadow: var(--shadow-md);
}
```

### Dark Deal Card (navy bg)
```css
.card-deal {
  background: var(--color-navy-mid);
  border: 1px solid var(--color-gold-20);
  border-top: 3px solid var(--color-gold);
  border-radius: var(--radius-lg);
  padding: var(--space-8);
  color: var(--color-white);
}
```

### Stat Card
```html
<div class="card-stat">
  <span class="card-stat__number">€40B</span>
  <span class="card-stat__label">Foreign direct investment into Spain, 2024</span>
</div>
```
```css
.card-stat__number {
  font-family: var(--font-display);
  font-size: var(--text-5xl);
  font-weight: var(--font-bold);
  color: var(--color-gold);
  line-height: 1;
}
.card-stat__label {
  font-family: var(--font-body);
  font-size: var(--text-sm);
  color: var(--text-on-dark-muted);
  margin-top: var(--space-2);
}
```

---

## Navigation

### Desktop Nav
```html
<nav class="nav" aria-label="Main navigation">
  <div class="nav__inner container">
    <a href="/" class="nav__logo">
      <img src="/assets/logo.png" alt="CostablancaBridge" width="180" height="48">
    </a>
    <ul class="nav__links" role="list">
      <li class="nav__item nav__item--dropdown">
        <button class="nav__trigger">Services</button>
        <ul class="nav__dropdown" role="list">
          <li><a href="/services/land">LAND — Market Entry</a></li>
          <li><a href="/services/operate">OPERATE — Business Operations</a></li>
          <li><a href="/services/trade">TRADE — Cross-Border Deals</a></li>
          <li><a href="/services/people">PEOPLE — Relocation & Workforce</a></li>
        </ul>
      </li>
      <li><a href="/how-we-work">How We Work</a></li>
      <li><a href="/about">About</a></li>
      <li><a href="/insights">Insights</a></li>
    </ul>
    <a href="/contact" class="btn-primary btn--sm">Book a Call</a>
    <button class="nav__hamburger" aria-label="Open menu" aria-expanded="false">
      <!-- hamburger icon -->
    </button>
  </div>
</nav>
```
```css
.nav {
  position: sticky;
  top: 0;
  z-index: var(--z-sticky);
  background: rgba(13, 35, 64, 0.95); /* navy-dark with slight transparency */
  backdrop-filter: blur(8px);
  border-bottom: 1px solid var(--color-white-10);
  height: var(--nav-height);
}
.nav__inner {
  display: flex;
  align-items: center;
  justify-content: space-between;
  height: 100%;
}
.nav__links {
  display: flex;
  align-items: center;
  gap: var(--space-8);
  list-style: none;
}
.nav__links a {
  font-family: var(--font-body);
  font-size: var(--text-sm);
  font-weight: var(--font-medium);
  color: var(--color-white);
  text-decoration: none;
  opacity: 0.85;
  transition: opacity var(--transition-fast);
}
.nav__links a:hover { opacity: 1; }
```

---

## Sections

### Hero Section
```css
.hero {
  background-color: var(--color-navy-dark);
  padding: var(--section-lg) 0;
  position: relative;
  overflow: hidden;
}
/* Decorative circle — purely visual, aria-hidden */
.hero::before {
  content: '';
  position: absolute;
  top: -10%;
  right: -5%;
  width: 500px;
  height: 500px;
  border-radius: 50%;
  background: var(--color-navy);
  opacity: 0.5;
  pointer-events: none;
}
```

### Section Wrapper (standard)
```css
.section {
  padding: var(--section-md) 0;
}
.section--sm  { padding: var(--section-sm) 0; }
.section--lg  { padding: var(--section-lg) 0; }
.section--cream     { background: var(--color-cream); }
.section--white     { background: var(--color-white); }
.section--navy      { background: var(--color-navy); }
.section--navy-dark { background: var(--color-navy-dark); }
.section--gold      { background: var(--color-gold); }
```

---

## Forms

### Contact / Intake Form
```html
<form class="form-contact" method="post" action="/api/contact">
  <div class="form-group">
    <label class="form-label" for="name">Full name *</label>
    <input class="form-input" type="text" id="name" name="name" required
           placeholder="James Whitfield" autocomplete="name">
  </div>
  <div class="form-group">
    <label class="form-label" for="email">Email address *</label>
    <input class="form-input" type="email" id="email" name="email" required
           placeholder="james@company.com" autocomplete="email">
  </div>
  <div class="form-group">
    <label class="form-label" for="service">What are you looking for? *</label>
    <select class="form-select" id="service" name="service" required>
      <option value="">Select a service</option>
      <option value="land">LAND — Company formation / market entry</option>
      <option value="operate">OPERATE — Compliance and ongoing legal</option>
      <option value="trade">TRADE — Cross-border deal or co-investment</option>
      <option value="people">PEOPLE — Relocation or workforce</option>
      <option value="other">Other / Not sure yet</option>
    </select>
  </div>
  <div class="form-group">
    <label class="form-label" for="message">Brief description</label>
    <textarea class="form-textarea" id="message" name="message" rows="4"
              placeholder="Tell us about your situation in a few lines..."></textarea>
  </div>
  <button type="submit" class="btn-primary btn--lg">Send Message</button>
  <p class="form-privacy">We treat all enquiries as strictly confidential. No spam, ever.</p>
</form>
```
```css
.form-group { display: flex; flex-direction: column; gap: var(--space-2); margin-bottom: var(--space-5); }
.form-label { font-size: var(--text-sm); font-weight: var(--font-semibold); color: var(--text-primary); }
.form-input, .form-select, .form-textarea {
  font-family: var(--font-body);
  font-size: var(--text-base);
  color: var(--text-primary);
  background: var(--color-white);
  border: 1px solid var(--border-medium);
  border-radius: var(--radius-md);
  padding: var(--space-3) var(--space-4);
  transition: border-color var(--transition-fast), box-shadow var(--transition-fast);
  width: 100%;
}
.form-input:focus, .form-select:focus, .form-textarea:focus {
  outline: none;
  border-color: var(--color-navy);
  box-shadow: 0 0 0 3px var(--color-navy-10);
}
.form-privacy { font-size: var(--text-xs); color: var(--text-secondary); margin-top: var(--space-3); }
```

---

## Tier Progression (3-step horizontal)

Used on How We Work page.
```html
<div class="tier-progression">
  <div class="tier tier--1">
    <span class="tier__number">01</span>
    <h4 class="tier__title">Service Provider</h4>
    <p class="tier__desc">Fixed fees + retainers. The operational foundation.</p>
    <span class="tier__tag">Fixed fees</span>
  </div>
  <div class="tier__arrow" aria-hidden="true">→</div>
  <div class="tier tier--2">
    <span class="tier__number">02</span>
    <h4 class="tier__title">Deal Architect</h4>
    <p class="tier__desc">Success fees + carried interest. Mid-label role.</p>
    <span class="tier__tag">Success fees</span>
  </div>
  <div class="tier__arrow" aria-hidden="true">→</div>
  <div class="tier tier--3">
    <span class="tier__number">03</span>
    <h4 class="tier__title">Principal Partner</h4>
    <p class="tier__desc">Equity stakes + profit participation. Networks as capital.</p>
    <span class="tier__tag">Equity + profit share</span>
  </div>
</div>
```

---

## Reveal Animations

Apply these classes to any element to animate it on scroll (use IntersectionObserver):
```css
.reveal {
  opacity: 0;
  transform: translateY(24px);
  transition: opacity var(--transition-reveal), transform var(--transition-reveal);
}
.reveal.is-visible {
  opacity: 1;
  transform: translateY(0);
}
```
```js
// Minimal IntersectionObserver — add to main.js
const observer = new IntersectionObserver((entries) => {
  entries.forEach(entry => {
    if (entry.isIntersecting) {
      entry.target.classList.add('is-visible');
      observer.unobserve(entry.target);
    }
  });
}, { threshold: 0.15 });

document.querySelectorAll('.reveal').forEach(el => observer.observe(el));
```

---

## Responsive Grid Patterns

```css
/* 4-column grid (service pipelines, persona cards) */
.grid-4 {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: var(--space-6);
}
@media (max-width: 1024px) { .grid-4 { grid-template-columns: repeat(2, 1fr); } }
@media (max-width: 640px)  { .grid-4 { grid-template-columns: 1fr; } }

/* 2-column split */
.grid-2 {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: var(--space-10);
  align-items: center;
}
@media (max-width: 768px) { .grid-2 { grid-template-columns: 1fr; } }

/* 2-column asymmetric (60/40) */
.grid-60-40 {
  display: grid;
  grid-template-columns: 3fr 2fr;
  gap: var(--space-12);
  align-items: start;
}
@media (max-width: 768px) { .grid-60-40 { grid-template-columns: 1fr; } }
```
