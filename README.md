# Princess Annie's Picks — Amazon Associates Starter Site

A static HTML/CSS/JS comparison-and-listicle site scaffold, built to line up with the
**Amazon Associates Program Operating Agreement** requirements. It ships with placeholder
content — swap that out before you publish.

Your Associates tracking ID (`annie0387-20`) is already wired into every affiliate link
via `?tag=annie0387-20`.

## Structure

```
amazon-associate-site/
├── index.html                    Homepage
├── css/style.css                 All styling (light + dark mode aware)
├── js/script.js                  Mobile nav toggle only — no tracking/analytics added
└── pages/
    ├── best-picks-example.html   Example comparison/listicle page (5 placeholder products + table)
    ├── disclosure.html           Required Amazon Associates + FTC affiliate disclosure
    ├── privacy-policy.html       Privacy policy covering Amazon's affiliate cookies
    ├── about.html                About page template
    └── contact.html              Contact page (mailto only — no backend)
```

## Before you publish: replace placeholder content

1. **Niche & copy** — you told me to scaffold with placeholder content. Replace "Placeholder
   Product One–Five", category names, and all body copy in `pages/best-picks-example.html`
   and `index.html` with your real niche and real products.
2. **ASINs** — replace `B0PLACEHOLD1`…`B0PLACEHOLD5` in the `href` attributes with real
   Amazon ASINs (find them in the product URL or via SiteStripe).
3. **Images** — the gray boxes are placeholders. Use your **own** product photos (yours,
   licensed stock, or manufacturer press images you have rights to) — never copy Amazon's
   listing photos.
4. **Site name / domain** — "Princess Annie's Picks" and `example.com` are placeholders throughout
   (nav, footer, disclosure, privacy policy, contact email). Do a find-and-replace.
5. **Legal review** — `privacy-policy.html` is a starting point, not legal advice. If you'll
   have EU/UK or California visitors, have it reviewed for GDPR/CCPA cookie-consent
   requirements before going live.

## Why the site is built this way (Associates Program compliance)

- **Disclosure on every page with a link**: A disclosure banner appears near the top of
  `best-picks-example.html` and inline under every "Check Price on Amazon" button, plus a
  standalone `disclosure.html` and a footer disclosure on *every* page. Amazon requires the
  "As an Amazon Associate I earn from qualifying purchases" disclosure be placed in reasonable
  proximity to affiliate links, not buried in one hard-to-find page.
- **No displayed prices, star ratings, or "Prime" badges**: Amazon's API Terms only let you
  show pricing/availability/review data if you pull it live via the Product Advertising API
  (and refresh within 24 hours). Since this scaffold has no backend/API integration, it never
  prints a price — it always sends the visitor to Amazon to see the live price instead.
- **No copied Amazon content**: product titles, descriptions, and images on Amazon listings
  are not yours to reuse. Every product block here is written as original placeholder copy
  you're meant to replace with your own words/photos.
- **Plain, untampered links**: affiliate links are full `amazon.com` URLs with `?tag=` —
  not shortened or redirected through your own domain, which is against Associates policy
  because it obscures the destination.
- **`rel="nofollow sponsored noopener"`** on every affiliate link — not an Amazon requirement,
  but expected by Google's guidelines for paid/affiliate links, and `noopener` is a security
  best practice for `target="_blank"` links.
- **No Amazon trademarks used as branding**: no Amazon logo, no site name containing "Amazon,"
  and an explicit "not endorsed by Amazon" line in every footer.
- **Independent Privacy Policy** disclosing that Amazon may set cookies via affiliate links,
  per Associates Program requirements.

## Operational rules to know (not solved by code — these are about how you *run* the account)

- **3 sales in 180 days**: Amazon requires at least 3 qualifying sales within 180 days of
  applying, or the application is closed (you can reapply).
- **No affiliate links in email or offline material**: Associates links may only be used on
  your registered website/app/social presence, not in emails/PDFs.
- **No incentivized clicks**: you can't offer a reward, discount, or "cash back" for using
  your links.
- **Traffic disclosure**: you must accurately describe how you'll drive traffic to the site
  when applying, and keep doing so.
- **One approved site per link type**: link only from properties you've listed/approved in
  your Associates account.

## Running it locally

No build step — just open `index.html` in a browser, or serve the folder:

```bash
npx serve .
# or
python -m http.server 8000
```

## Hosting

Any static host works: Netlify, Vercel, GitHub Pages, Cloudflare Pages, S3+CloudFront.
Drop the whole folder in; no server-side code required.
