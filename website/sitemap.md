# CostablancaBridge — Website Sitemap

**Version:** 1.0 · April 2026

---

## Navigation Structure

### Primary Navigation (Desktop)
```
Logo | Services ▾ | How We Work | About | Insights | [Book a Call]
```

### Services Dropdown
```
Services
├── LAND — Market Entry
├── OPERATE — Business Operations
├── TRADE — Cross-Border Deals
└── PEOPLE — Workforce & Relocation
```

### Mobile Navigation (Hamburger)
```
Home
Services
  ├── LAND
  ├── OPERATE
  ├── TRADE
  └── PEOPLE
How We Work
About
Insights
Contact / Book a Call
```

---

## Full Sitemap

```
/ (Homepage)
│
├── /services
│   ├── /services/land          (Market Entry)
│   ├── /services/operate       (Business Operations)
│   ├── /services/trade         (Cross-Border Deals & Co-Investment)
│   └── /services/people        (Workforce & Relocation)
│
├── /how-we-work                (The Principal Model)
│
├── /about                      (Team + Unfair Advantage)
│
├── /insights                   (Blog / Market Intelligence index)
│   ├── /insights/post-slug-1   (e.g. "How to Set Up a Spanish SL Post-Brexit")
│   ├── /insights/post-slug-2   (e.g. "Digital Nomad Visa Spain: Complete Guide 2026")
│   └── /insights/post-slug-3   (e.g. "Emerging Market Trade Corridors into the EU")
│
├── /contact                    (Contact / Book a Call)
│
└── Legal
    ├── /privacy-policy
    └── /cookie-policy
```

---

## Page Priority for Phase 1 Build

| Priority | Page | Rationale |
|---|---|---|
| P0 | Homepage `/` | Primary landing, all personas, primary CTA |
| P0 | `/services/land` | Highest search volume, James persona |
| P0 | `/services/people` | High search volume, Sofia + Erik persona |
| P0 | `/how-we-work` | Differentiator page, Mohammed persona |
| P0 | `/contact` | Conversion page |
| P0 | `/about` | Trust page — all personas check this |
| P1 | `/services/trade` | Deal origination — Mohammed persona |
| P1 | `/services/operate` | Upsell + retention |
| P1 | `/insights` (index + 3 posts) | SEO + Erik/Sofia discovery |
| P2 | `/privacy-policy`, `/cookie-policy` | Legal requirement |
| P3 | Remaining insights posts | Ongoing SEO content |

---

## URL Structure Conventions

- All lowercase, hyphen-separated: `/services/market-entry` not `/Services/MarketEntry`
- No trailing slashes
- No query string parameters in canonical URLs
- Canonical tags on all pages
- Sitemap.xml generated and submitted to Google Search Console at launch
