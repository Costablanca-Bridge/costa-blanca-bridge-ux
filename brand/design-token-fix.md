# Design Token Fix — Gold Colour Inconsistency

**Version:** 1.0 · April 2026
**Owner:** UX Lead
**Resolves:** `#C4965A` in `website/css/styles.css` vs `#C8973A` in `brand/design-tokens.css` and `brand/brand-guidelines.md`

---

## Problem

The website CSS (`costa-blanca-bridge-website/website/css/styles.css`) defines the gold colour as `#C4965A`. The UX repository's design tokens (`brand/design-tokens.css`) and brand guidelines (`brand/brand-guidelines.md`) define it as `#C8973A`.

These are different colours. `#C4965A` is a slightly more muted, cooler-leaning gold. `#C8973A` is the correct brand gold — warmer and more saturated.

Design systems drift when the source of truth is not pinned. Every hardcoded value in the website that doesn't reference the token is a future inconsistency.

---

## Source of Truth

**`#C8973A` is the correct brand gold.**

This is confirmed in:
- `costa-blanca-bridge-ux/brand/brand-guidelines.md` — Section 2, Primary Palette
- `costa-blanca-bridge-ux/brand/design-tokens.css` — `--color-gold: #C8973A`

The website CSS is wrong and must be corrected.

---

## Required Fix

### In `costa-blanca-bridge-website/website/css/styles.css`

Replace the local CSS custom property definitions at the top of the file with an import of the design tokens from the UX repository, OR manually correct the gold values to match the source of truth.

**Option A — Correct approach (recommended):** Reference the design tokens file as the single source.

The website's CSS file should open with:
```css
/* Design tokens — single source of truth */
/* Copy of: costa-blanca-bridge-ux/brand/design-tokens.css */
/* Last synced: [date] */
```

And the token values must match exactly.

**Option B — Immediate fix (minimum acceptable):** Update the hardcoded values in `website/css/styles.css`:

```css
/* Before */
--color-gold:         #C4965A;
--color-gold-light:   #E0B87A;
--color-gold-20:      rgba(196, 150, 90, 0.20);
--color-gold-12:      rgba(196, 150, 90, 0.12);
--shadow-gold:        0 4px 24px rgba(196, 150, 90, 0.18);

/* After — corrected to match brand/design-tokens.css */
--color-gold:         #C8973A;
--color-gold-light:   #E8C46A;
--color-gold-10:      rgba(200, 151, 58, 0.10);
--color-gold-20:      rgba(200, 151, 58, 0.20);
--color-gold-30:      rgba(200, 151, 58, 0.30);
--shadow-gold:        0 4px 24px rgba(200, 151, 58, 0.20);
--shadow-gold-lg:     0 8px 40px rgba(200, 151, 58, 0.30);
```

Note also: `--color-gold-12` does not exist in the design tokens. If used anywhere in the website CSS, replace with `--color-gold-10` (closest match). Remove the non-standard token.

---

## Contrast Check After Fix

Verify these combinations still pass WCAG AA after the fix:

| Text | Background | Required ratio | Post-fix status |
|---|---|---|---|
| `#0D2340` (navy-dark) | `#C8973A` (gold) | 3:1 (large text/UI) | ✅ ~6.9:1 |
| `#C8973A` (gold text) | `#0D2340` (navy-dark bg) | 4.5:1 (body) | ✅ ~6.9:1 |

`#C8973A` has slightly better contrast against navy-dark than `#C4965A` — the fix improves accessibility marginally as well as brand accuracy.

---

## Long-Term: Single Source of Truth

The website CSS should not maintain its own parallel token definitions. The recommended long-term approach:

1. The design tokens CSS file (`costa-blanca-bridge-ux/brand/design-tokens.css`) is the canonical source
2. The website build process copies or imports this file directly
3. No colour value is ever hardcoded in the website CSS — all via `var(--token-name)`
4. When brand tokens change, only `design-tokens.css` changes — website updates automatically

Until a build pipeline is in place, the manual sync process is: update `design-tokens.css` → copy token values to `website/css/styles.css` → note the sync date in a comment.

---

## Checklist

- [ ] `--color-gold` corrected to `#C8973A` in `website/css/styles.css`
- [ ] `--color-gold-light` corrected to `#E8C46A`
- [ ] RGBA values corrected for gold opacity variants
- [ ] `--color-gold-12` removed (non-standard) — usages replaced with `--color-gold-10`
- [ ] Visual regression check: review all gold elements on screen after the change
- [ ] Contrast check passes on CTA buttons, stat numbers, section labels
