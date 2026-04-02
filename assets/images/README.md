# Brand Image Assets

All source logo files — use these as references when producing final web-optimised assets.

| File | Description | Use |
|---|---|---|
| `logo-full.jpg` | Master logo sheet — all variations on one page (dark navy, cream, and gold backgrounds) | Design reference |
| `logo-hero-dark.jpg` | Logo on dark navy gradient, horizontal layout, large format | Hero section reference |
| `logo-full-dark.jpg` | Full logo (icon + wordmark) on dark navy, medium size | Nav and dark section reference |
| `logo-full-dark-2.jpg` | Full logo on dark navy, slightly wider crop | Alternative nav reference |
| `logo-icon-dark.jpg` | Icon only (bridge arch), no wordmark, on dark navy | Favicon, icon-only contexts |
| `logo-light-bg.jpg` | Full logo on cream/light background | Light section use |
| `logo-variations.jpg` | All colour variations (dark/cream/gold backgrounds) | Colour usage reference |

## Logo Colours (extracted from images)

| Element | Value |
|---|---|
| Bridge arch icon | `#C4965A` (warm gold/bronze) |
| Wordmark "Costa Blanca Bridge" (on dark) | `#FFFFFF` |
| Wordmark (on light) | `#0D2340` (navy dark) |
| Tagline "Connecting Worlds" | letter-spaced, same as wordmark |
| Background (dark version) | `#0D2340` → `#1B3A6B` gradient |
| Background (light version) | `#F5F1EA` (cream) |

## For the Coding Agent

The bridge arch icon is reproduced as an inline SVG in `concept/homepage-concept.html`
(inside a `<symbol id="bridge-icon">` element). This SVG version is used for nav, footer, and
the hero card. When the real logo files are converted to SVG by a designer, replace the inline SVG
with the official file and update all `<use href="#bridge-icon">` references.

To convert for web production:
- Export `logo-hero-dark.jpg` → `logo-dark.webp` (for hero and nav)
- Export `logo-light-bg.jpg` → `logo-light.webp` (for light backgrounds)
- Export `logo-icon-dark.jpg` → `favicon.ico` + `icon.png` (32×32, 180×180)
- Request official `.svg` source from designer
